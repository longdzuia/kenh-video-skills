# Chấm giờ giọng đọc: hướng dẫn

## Dùng đường nào

**faster-whisper, mô hình large-v3, chạy CPU (int8)**, cài trong `tools/whisper/venv`, mô hình nằm ở `tools/whisper/models` (tải một lần, ~3 GB, các video sau dùng lại).

Không dùng `hyperframes transcribe` vì máy không có whisper-cpp (lý do ở cuối file).

## Lệnh chạy (đứng trong thư mục project)

Từ 2026-10-30 gọi cả hai bước bằng một lệnh: `C:/hyperframestest/cong-cu/hf.cmd moc` (xem `cong-cu\HUONG-DAN-HF.md`). Hai lệnh dưới là việc nó làm, dùng khi cần chạy riêng một bước (vd nghe lại một đoạn).

```bash
# 1) Chấm giờ từng từ (~2–4 phút cho 2 phút giọng đọc)
C:/hyperframestest/tools/whisper/venv/Scripts/python C:/hyperframestest/tools/whisper/chamgio.py assets/giongdoc.mp3 .work/whisper-words.json vi

# 2) Khớp với kịch bản #n.mp3-VEO/HF-dòng -> mốc đầu/cuối từng dòng
C:/hyperframestest/tools/whisper/venv/Scripts/python C:/hyperframestest/tools/whisper/khopdong.py assets/kichban.txt .work/whisper-words.json assets/giongdoc.mp3 assets/mocgio.json
```

`mocgio.json` có:
- `khoi`: các khối liền nhau cùng vai (HF/VEO), mốc giây đầu và cuối;
- `dong`: từng dòng với `t0`, `t1` (giây), `khop` (tỉ lệ từ dóng được) và `words` = mốc bắt đầu từng từ của kịch bản (dùng để cho hình vào đúng âm tiết).

`khopdong.py` in bảng tóm tắt ra màn hình; dòng nào `khớp` dưới ~80% thì nghe lại chỗ đó.

## Cách khớp và vì sao

1. Whisper nghe số thành chữ số (`70`, `5 xu`) và nghe nhầm vài âm (`su`/`xu`, `sui`/`xui`, `rúi`/`dúi`). Hai bên được chuẩn hóa về chữ không dấu, số đổi thành chữ, rồi dóng hàng từng từ bằng `difflib`.
2. Whisper hay **nuốt khoảng lặng vào từ đứng sau nó** (vd "Và" 36,60–36,94 trong khi lặng thật 36,74–37,13), làm đầu dòng sớm 0,3–0,6 s. Nên biên dòng được đối chiếu với khoảng lặng thật từ `ffmpeg silencedetect -35dB, 0,15 s`: lặng ở nửa đầu của từ thì từ bắt đầu sau lặng, lặng ở nửa sau thì từ kết thúc lúc lặng bắt đầu.
3. Hai dòng đọc liền không nghỉ (vd #31→#32 video Coca) thì biên là mốc whisper.

## Khi whisper bịa câu (ảo giác)

Gặp ở video Häagen-Dazs (2026-10-02): đoạn 55–84 s whisper ra một câu dài không có trong giọng đọc ("Hãy subscribe cho kênh Ghiền Mì Gõ…"), làm `khopdong.py` dừng với lỗi `Dòng #n không dóng được từ nào`. Dấu hiệu: một segment dài bất thường mang câu lạ trong log của bước 1.

Cách chữa, không sửa `chamgio.py`:
1. Chọn hai biên là đầu và cuối của hai segment whisper nghe đúng kẹp hai bên đoạn hỏng (để không cắt giữa từ).
2. Cắt đoạn đó ra wav rồi cho whisper nghe lại riêng:
   ```bash
   ffmpeg -v error -y -i assets/giongdoc.mp3 -ss <biên đầu> -to <biên cuối> -ac 1 -ar 16000 .work/doan.wav
   C:/hyperframestest/tools/whisper/venv/Scripts/python C:/hyperframestest/tools/whisper/chamgio.py .work/doan.wav .work/whisper-doan.json vi
   ```
3. Ghép: giữ từ của bản đầu nằm ngoài đoạn, thay phần trong đoạn bằng từ của bản nghe lại cộng thêm `<biên đầu>` giây. Ghi ra file mới (vd `.work/whisper-words-ghep.json`), giữ nguyên bản đầu, rồi chạy bước 2 trên file ghép.

Thêm một chỗ cần soát sau bước 2: tên riêng whisper nghe sai hẳn (vd "Häagen-Dazs" → "Harzendat") không dóng được và bị nội suy. Nếu nó là từ cuối dòng thì `t1` của dòng bị cụt (Häagen-Dazs #7: 24,72 thay vì 25,21). Đối chiếu từ cuối mỗi dòng với log whisper và `silencedetect`; sửa tay trong `mocgio.json` thì ghi lý do vào khóa `ghi_chu` và giữ bản chưa sửa trong `.work`.

## Hai chỗ riêng của máy này

- **Windows Application Control chặn DLL của PyAV (gói `av`)**. `chamgio.py` thay `av` bằng module rỗng và tự giải mã âm thanh bằng ffmpeg (16 kHz, mono). Không đụng cài đặt bảo mật.
- In tiếng Việt ra file log: script tự chuyển stdout sang UTF-8 (Windows mặc định cp1252 sẽ báo `UnicodeEncodeError`).

## Vì sao `hyperframes transcribe` báo `whisper_unavailable`

Đọc mã CLI hyperframes (bản 0.8.71, hàm `findWhisper`/`ensureWhisper`), nó tìm whisper-cpp theo đúng ba chỗ:

1. biến môi trường `HYPERFRAMES_WHISPER_PATH`;
2. lệnh `where whisper-cli` trên PATH (chỉ đúng tên `whisper-cli`, không nhận `whisper-cpp.exe`, `main.exe` hay `whisper.exe` của Python);
3. bản tự build ở `~/.cache/hyperframes/whisper/whisper.cpp/build/bin/whisper-cli`.

Trên máy này cả ba đều trống: đã tìm `whisper-cli.exe`, `whisper-cpp.exe`, `ggml-*.bin` trong hồ sơ người dùng, Program Files và AppData, không có. Nó cũng **không tự build được**, vì bước build cần `cmake` và trình biên dịch C (không có; chỉ có git). Thêm nữa, kể cả build được trên Windows, CMake/MSVC đặt file ở `build/bin/Release/whisper-cli.exe`, trong khi CLI chỉ dò `build/bin/whisper-cli` (không `.exe`, không `Release`), nên bản tự build trên Windows cũng không được nhận.

Muốn `hyperframes transcribe` chạy được thì phải có bản `whisper-cli.exe` dựng sẵn và trỏ `HYPERFRAMES_WHISPER_PATH` vào nó. Đường faster-whisper ở trên không cần việc đó và cho kết quả tiếng Việt tốt (video Coca: 99,8% từ kịch bản dóng được).
