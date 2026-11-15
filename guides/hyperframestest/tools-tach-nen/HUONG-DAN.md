# Tách nền sticker: hướng dẫn

Công cụ dùng chung cho mọi video. Biến ảnh sinh từ Nano Banana Pro (một vật, hoặc một tờ nhiều vật) thành PNG nền trong suốt, mỗi vật một file.

## Lệnh chạy

Đứng trong thư mục project (vd `C:\hyperframestest\coca-5xu`):

```bash
C:/hyperframestest/cong-cu/hf.cmd tachnen
```

Từ 2026-10-30 gọi qua lệnh chung `hf tachnen` (xem `cong-cu\HUONG-DAN-HF.md`); `tachnen.cmd` vẫn chạy được. `tachnen.py` tự né DLL bị Windows chặn của numba và scipy, không cần script bọc trong dự án.

- Đầu vào mặc định: `assets/vat-lieu-goc/` (không bao giờ bị sửa).
- Đầu ra mặc định: `assets/vat-lieu/` + ảnh xem nhanh `assets/vat-lieu/_xem-nhanh.png`.
- Chạy lại thì ghi đè file cùng tên trong thư mục ra.

Chỉ định thư mục khác: `tachnen.cmd <thư mục vào> <thư mục ra> [tùy chọn]`.

## Tùy chọn

| Tùy chọn | Tác dụng |
|---|---|
| `--vien 10` | bật viền giấy trắng dày 10 px quanh sticker (kiểu miếng dán). Mặc định `0` = tắt |
| `--khong-cat` | coi mỗi ảnh là một vật, không tách tờ |
| `--lap-het` | lấp cả các lỗ kín cùng màu nền (khi công cụ báo "giữ lỗ" mà lỗ đó là thủng nhầm) |
| `--mo-hinh birefnet-dis` | đổi mô hình (mặc định `birefnet-general`; `birefnet-general-lite` nhanh hơn, kém nét hơn) |
| `--nguong 30` | độ lệch màu so với nền để tính là vật; nền bẩn thì tăng lên |
| `--gop 0` | số px nới để gộp các mảnh của cùng một vật; `0` = tự tính (1,2% cạnh ngắn). Vật bị chẻ đôi thì tăng; hai vật bị dính làm một thì giảm |
| `--le 12` | lề trong suốt quanh sticker |

## Đặt tên

- Ảnh chỉ có một vật: `ten-anh.png`.
- Ảnh là một tờ nhiều vật: `ten-anh-01.png`, `-02`… theo thứ tự đọc (hàng trên xuống, trái sang phải).
- Đuôi giờ tải của công cụ sinh ảnh bị bỏ và `_` đổi thành `-`: `chai_20260926012751.jpg` → `chai-01.png`. Ảnh gốc không bị đổi tên.

Nên đặt tên ảnh gốc theo tên tờ trong `VAT-LIEU.md` để biết sticker nào là vật nào.

## Cách làm (vì sao chọn như vậy)

1. **Tìm vật trên tờ**: lấy màu nền ở dải viền ảnh, đánh dấu điểm lệch màu nền, nới ra để gộp mảnh của cùng một vật, tách vùng liền. Không dùng phép lọc nhiễu kiểu "opening" vì nó xóa luôn nét mực 1–2 px (vật chỉ gồm nét mảnh như mũi tên, lò xo vẫn được giữ).
2. **Mô hình BiRefNet** (`birefnet-general` qua rembg, chạy CPU bằng onnxruntime) tách nền cho **từng vật đã cắt riêng**, để mỗi vật được mô hình nhìn ở độ phân giải cao (mô hình thu ảnh về 1024 px, chạy cả tờ thì vật nhỏ mất nét).
3. **Cứu nét mực**: điểm tối (độ sáng < 110) nằm trong vùng của vật luôn được giữ đục, nên nét mảnh không bị mô hình làm mờ hay cắt cụt.
4. **Không khoét thủng mảng sáng bên trong vật**: mọi điểm nằm trong đường bao của vật được đặt đục, quyết theo cả mảng chứ không từng điểm ảnh (mô hình hay khoét nham nhở mặt trong đồng xu, nhãn trắng…). Chỉ giữ trong suốt những mảng **trùng màu nền** mà là lỗ thật:
   - nền có sắc (bạc hà, hồng nhạt…): mảng trùng hẳn màu nền là lỗ thật;
   - nền trắng/xám: mảng trắng của vật trùng màu nền, nên để mô hình quyết.
   → **Khi sinh ảnh, chọn màu nền không có trong vật** (vd bạc hà nhạt cho vật không có màu xanh lá) thì lỗ thật (quai cốc) được giữ đúng, mảng trắng không bị khoét.
5. **Bỏ vụn rời** nhỏ hơn 1% thân chính.
6. **Gỡ ám màu nền ở mép** để sticker không có quầng sáng khi đặt lên nền tối.
7. Cắt sát theo vật + lề, thêm viền trắng nếu bật `--vien`.

Chạy hoàn toàn trên máy, CPU: ~25–35 s mỗi vật. Kết quả tất định (cùng ảnh cho cùng sticker).

## Đọc cảnh báo

Cuối mỗi lần chạy, công cụ liệt kê sticker nghi hỏng; vẫn phải xem `_xem-nhanh.png` (mỗi sticker hai ô: nền caro để thấy chỗ thủng, nền tối để thấy quầng sáng và vết cắt).

| Cảnh báo | Nghĩa | Xử lý |
|---|---|---|
| `giữ N lỗ cùng màu nền` | có mảng kín trùng màu nền được để trong suốt | lỗ thật thì thôi; thủng nhầm thì chạy lại với `--lap-het` |
| `mép mờ rộng ~N px` | dải mép bán trong suốt dày hơn 4 px | nghi nét bị nhòe hoặc dính bóng; xem trên nền tối |
| `N% phần đục nằm ngoài nét viền` | có phần đục ngoài đường viền mực của vật | nghi dính bóng đổ hoặc mẩu nền; sinh lại ảnh với "no shadow" hoặc cắt tay |

Vật không có viền mực (hiếm với phong cách kênh) thì thước đo "ngoài nét viền" không áp dụng.

## Máy chặn DLL (Application Control)

- **numba** (`numba/_helperlib.pyd`, chặn từ 2026-10-04): rembg nạp pymatting, pymatting nạp numba. Công cụ không dùng alpha matting (`only_mask=True`), nên từ 2026-10-07 `tachnen.py` tự thay pymatting bằng module rỗng trước khi nạp rembg. Không đụng cài đặt bảo mật. Bản trước khi sửa: `tachnen-truoc-2026-10-07.py`. Đã kiểm: sticker ra trùng từng byte với bản chạy qua script bọc cũ.
- Script bọc `blockbuster/.work/tachnen-khong-numba.py` không cần dùng nữa.

## Cài đặt (đã làm, ghi lại để dựng lại khi cần)

```bash
cd C:/hyperframestest/tools/tach-nen
python -m venv venv
venv/Scripts/python -m pip install --no-cache-dir "rembg[cpu]"
```

- Python 3.14, rembg 2.0.85, onnxruntime 1.30 (chạy được dưới Application Control của máy này).
- Mô hình tự tải lần chạy đầu vào `tools/tach-nen/models` (~930 MB; biến `U2NET_HOME` đặt sẵn trong script nên không rải ra `~/.u2net`).

## Chạy thử

`tools/tach-nen/thu/` có ảnh mẫu tự vẽ (`vat-lieu-goc/`) và kết quả (`vat-lieu/`, `vat-lieu-vien/` với `--vien 10`). Các ca đã kiểm: tờ 6 vật trên nền trắng ngà (chai có nhãn trắng, đồng xu mặt trong sáng, máy bán hàng có ô kính trắng, lò xo và mũi tên chỉ gồm nét 2 px), ảnh một vật (jpg), vòng có lỗ thật trên nền bạc hà, hộp có bóng đổ mềm dưới đáy (bóng bị cắt bỏ).
