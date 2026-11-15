# Lệnh `hf`: hướng dẫn

Viết ngày 2026-10-30 (đợt dọn mạch). Mọi chỗ riêng của máy này — trình duyệt, bản HyperFrames, DLL bị Windows chặn, mã hóa chữ, thời hạn chờ — nằm trong `cong-cu\hf.py`, không nằm trong luật. Tác nhân (Claude Code hay Antigravity) chỉ gọi `hf`, không tự gõ `npx`, không tự đặt biến môi trường.

## Cách gọi

Đứng trong thư mục dự án:

```
C:\hyperframestest\cong-cu\hf.cmd <lệnh> [cờ…]
```

Gõ được như nhau trong PowerShell, cmd và Git Bash (Bash: `/c/hyperframestest/cong-cu/hf.cmd <lệnh>`).

| Lệnh | Làm gì |
|---|---|
| `hf may` | Kiểm máy: Chrome, headless-shell, bản HyperFrames có sẵn, ffmpeg, hai venv, cổng nội bộ, mạng. **Chạy đầu mỗi phiên.** Có mục LỖI thì báo chủ kênh trước khi làm tiếp. |
| `hf moc` | Chặng 1: whisper rồi khớp dòng, ra `assets\mocgio.json`. Tự tìm `assets\giongdoc.mp3` (hoặc file mp3 duy nhất) và `assets\kichban*.txt`. Có `mocgio.json` cũ thì chép sang `.work\mocgio-truoc-<giờ>.json` trước. |
| `hf tulieu [--so 5]` | Chặng 3: tìm tư liệu thật (`lay-tu-lieu.py`) cho dự án đang đứng. |
| `hf bao` | Chặng 3: chụp bài báo (`chup-bao.py`). Chạy sau `hf tulieu`, không chạy song song. |
| `hf tachnen [cờ…]` | Chặng 4: tách nền `assets\vat-lieu-goc` ra `assets\vat-lieu`. Cờ như `tools\tach-nen\HUONG-DAN.md` (`--gop 3`, `--vien 10`…). |
| `hf check [cờ…]` | `hyperframes check` bằng bản ghim của dự án. Cờ chuyển thẳng (`--range 40,90`, `--at 12,30`). |
| `hf snap [cờ…]` | `hyperframes snapshot` bằng bản ghim, mặc định ra `snapshots\<ngày-giờ>\`. Vd `hf snap --at 3,10.5,18 --no-end`. |
| `hf preview [cờ…]` | `hyperframes preview` bằng bản ghim. |
| `hf render` | Render cả video bằng `hyperframes@0.8.160` ra `renders\<tên>_vN.mp4` (N tự tăng, bản cũ giữ nguyên). |
| `hf render --khoi1` | Như trên, ra `renders\<tên>_khoi1_vN.mp4` cho bản xem khối 1. |

Render in log UTF-8 vào `.work\render-<tên>_vN.log`, cuối cùng báo thời lượng, cỡ file, thời gian render, rồi đo tiếng ở 10%, 50%, 90% thời lượng.

## `hf` làm gì thay mình, và vì sao

1. **Trình duyệt.**
   - `check`, `snap`, `preview` chạy bằng Chrome của máy (`HYPERFRAMES_BROWSER_PATH` = `chrome.exe`), như từ 2026-10-13.
   - `render` có một bước thử trình duyệt bằng `<trình duyệt> --version`. Trên Windows, `chrome.exe --version` không in số phiên bản: Chrome đang mở (kể cả chạy ngầm) thì lệnh chuyển sang nó rồi thoát mã 21; Chrome đã tắt hẳn thì lệnh mở cửa sổ mới rồi treo (`ETIMEDOUT`). Vì thế trước đây phải nhờ chủ kênh đóng Chrome, mà đóng hay mở đều có lúc hỏng (bac-ho-v2, 29/10: mất 70 phút). Nay `hf render` cho bước thử dùng `chrome-headless-shell` (in số phiên bản đàng hoàng), còn bước chụp khung đọc `PRODUCER_HEADLESS_SHELL_PATH` = `chrome.exe`, nên vẫn chụp bằng Chrome thật như mọi lần render trước. **Chủ kênh không cần đóng Chrome.** Đã chạy: bac-ho-v2 cả video (30/10), `thu-hieu-ung-dau` khi Chrome đang chạy ngầm (30/10).
   - Luật cũ ghi "Windows chặn Chrome riêng của hyperframes". Kiểm lại 30/10: nhật ký chặn của Windows 30 ngày qua không có `chrome-headless-shell`, và nó chạy được. Chưa thử dùng nó cho cả bước chụp, nên bước chụp vẫn giữ `chrome.exe` đã chạy quen.
2. **Không gọi Gemini.** `snapshot` tự gọi Gemini tả ảnh khi máy có key (dịch vụ tính tiền). `hf` gỡ `GEMINI_API_KEY`, `GOOGLE_API_KEY` khỏi môi trường của mọi lệnh, nên không cần nhớ `--describe false` nữa.
3. **Bản HyperFrames.**
   - `check`, `snap`, `preview` dùng bản ghim trong `package.json` của dự án; `render` dùng `0.8.160` (chủ kênh chốt 2026-10-28; lý do ở `phongcach\ban-luu\2026-10-28_render-0.8.160\`).
   - Luôn chạy `npx --offline` trước: không lên mạng kiểm phiên bản (trước đây `npx` treo khi bị sandbox chặn mạng). Bản chưa có trong máy thì mới tải.
4. **Thời hạn chờ trang 180 giây** (`PRODUCER_PAGE_NAVIGATION_TIMEOUT_MS`, `PRODUCER_PLAYER_READY_TIMEOUT_MS`). Mặc định của HyperFrames là 45 giây; trang có clip phim mất khoảng 95 giây mới sẵn sàng (bac-ho-v2), quá 45 giây là render hỏng với "window.__hf not ready".
5. **Render** mặc định `-w 2`. Gặp "The browser is already running for …puppeteer_dev_chrome_profile…" (một Chrome của lần chụp trước chưa thoát) thì chờ 20 giây rồi tự chạy lại một lần.
6. **Chữ tiếng Việt.** Mọi lệnh chạy với `PYTHONUTF8=1`, log ghi UTF-8 (log do PowerShell `*>` ghi ra là UTF-16, khó đọc).
7. **Tách nền** chạy thẳng `tools\tach-nen\tachnen.py`; file này tự né DLL bị chặn của numba (từ 2026-10-07) và của scipy (từ 2026-10-30, chỉ né khi nạp thật bị chặn). Không còn chép `tachnen-khong-scipy-transform.py` vào từng dự án.
8. **Tìm tư liệu.** `lay-tu-lieu.py` luôn tải bản thu nhỏ của Wikimedia (rộng tối đa 1920 px). Máy chủ ảnh `upload.wikimedia.org` có lúc nhận yêu cầu rồi im lặng với máy này (30/10 lúc 22 giờ: không trả byte nào, kể cả ảnh 496 px, cả IPv4, IPv6, cả Chrome của chủ kênh; một tiếng sau tự hết), trong khi `commons.wikimedia.org` vẫn trả bình thường. Nên file nào treo quá 30 giây thì công cụ tự lấy lại cùng ảnh qua `commons.wikimedia.org/w/thumb.php` (trang chính thức của Commons, đi qua cụm máy chủ trang), không phải tải tay. Đã chạy 30/10: một file treo được lấy qua đường này, 3/3 ứng viên trong 41 giây.

## Số đo thời gian (tạm)

| Việc | Số đo | Ở đâu |
|---|---|---|
| Render video chỉ có ảnh tĩnh | khoảng 18 giây video mỗi phút render (3 phút video mất 10 phút) | bac-ho-ra-di, 28/10 |
| Render video có clip phim | khoảng 8,5 giây video mỗi phút render (3 phút 33 mất 25 phút; chụp 4,7 khung/giây) | bac-ho-v2, 30/10 |
| Chờ trang trước khung đầu | 2 giây (ảnh tĩnh), 95 giây (có clip phim) | như trên |
| `check` cả video 3–4 phút | khoảng 7 phút mỗi lượt | bac-ho-v2, 30/10 |

Ước giờ render cả video thì lấy tốc độ đo được ở khối 1 nhân lên, không đoán. Báo tiến độ bằng số khung đã chụp trên tổng số khung.

## Chỗ chưa chữa được

- Nếu cả máy chủ ảnh lẫn `commons.wikimedia.org` cùng không trả (chưa gặp), công cụ báo "lỗi tải" cho dòng đó. Chạy lại `hf tulieu` sau một lúc (file đã tải thì bỏ qua); vẫn không được thì mở link Commons trong `NGUON.md`, tải tay vào `assets\tulieu\da-chon\`, ghi vào mục "Tải tay".
- Windows Smart App Control đang bật và thỉnh thoảng chặn thêm một DLL mới. Không tắt (luật quyền, mục 8). Gặp chặn mới thì vá theo cách cũ (thay module bằng module rỗng nếu công cụ không cần tới nó) **trong công cụ hoặc trong `hf.py`**, ghi vào đây.

## Khi gặp lỗi máy mới

1. Gỡ lỗi tối đa 10 phút. Chưa ra hướng thì dừng, báo chủ kênh: lỗi gì, đã thử gì, còn hướng nào.
2. Ra cách chữa thì vá vào `hf.py` (hoặc công cụ gốc), ghi một mục vào phần "`hf` làm gì thay mình" ở trên, kèm ngày và dự án gặp lỗi. **Không thêm vào sổ tay hay LUAT-GOC**: luật chỉ giữ luật kênh, máy nằm ở đây.
3. Trước khi sửa `hf.py` hay công cụ gốc, chép bản đang chạy vào `phongcach\ban-luu\<ngày>_<tên>\` như sổ tay mục 9.

## Antigravity

Sandbox terminal của Antigravity chặn mạng, thư mục Downloads và cổng nội bộ 127.0.0.1. Mà `check`, `snap`, `render` đều mở một máy chủ nhỏ trên 127.0.0.1, còn `tulieu`, `bao` cần mạng. Chủ kênh tắt sandbox terminal cho workspace `C:\hyperframestest`; nếu sandbox còn bật thì `hf may` báo LỖI ở mục "cổng nội bộ", và các lệnh `hf` phải chạy ngoài sandbox.
