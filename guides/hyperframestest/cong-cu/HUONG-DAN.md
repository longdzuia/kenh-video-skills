# Công cụ tư liệu thật

Dùng cho video được phép dùng tư liệu thật. Danh sách video được phép ở `VIDEO-DUOC-PHEP.md`, luật đặt hình thật ở sổ tay mục 10; mặc định là **không**. Tìm tư liệu tự động gồm: footage và ảnh chung (Pixabay, Mixkit; Pexels, Coverr khi có key), ảnh đúng đối tượng (Wikimedia), ảnh chụp bài báo có vệt bôi. Adapter tìm kiếm mượn của OpenMontage (`_ngoai\OpenMontage`, chỉ đọc và gọi).

## Quy trình cho một video (đã chạy trọn ở w1d4 `domino-30-phut`, 09–10/10/2026)

1. **Kiểm quyền**: tên video có trong sổ tay mục 10 chưa. Chưa có thì dừng, không tìm.
2. **minh-y** viết danh sách "Thấy thật" và "Tin" trong VAT-LIEU.md, kèm hai code block `// truy-van.txt` và `// bao.txt` (bản minh-y từ 13/10/2026). Claude Code chép hai khối đó ra hai file trong `assets\tulieu\` (VAT-LIEU cũ không có khối thì tự viết từ danh sách):
   - `truy-van.txt` (footage, ảnh chung, ảnh Wikimedia), truy vấn tiếng Anh; Mixkit chỉ 1–2 từ;
   - `bao.txt` (bài báo): cột câu bôi minh-y để trống thì Claude Code điền; **đọc chữ trang trước** để chép nguyên văn câu cần bôi và kiểm số liệu trong kịch bản (w1d4: bài Vietcetera xác nhận khảo sát Gcomm; bài Roanoke trả 410 nên bỏ).
3. Chạy `lay-tu-lieu.py`, rồi `chup-bao.py` (mục dưới). Mở `assets\tulieu\so-sanh.html`, gửi chủ kênh kèm gợi ý chọn. **Dừng chờ chủ kênh chọn**: chủ kênh tích ô, bấm "Chép danh sách", dán vào chat. Mỗi dòng chọn 0, 1 hay 2 file; không chọn thì dòng đó dựng bằng vẽ.
4. Chép file đã chọn vào `assets\tulieu\da-chon\` (bài báo chép kèm `.json` và `.js` cùng tên). Không xóa ứng viên. Ghi mục "Đã chọn" và bản nháp ghi công (file CC BY, CC BY-SA) vào cuối `NGUON.md`, ngoài phần TU-DONG.
5. Clip footage chuyển mã một bản vào `.work\tulieu\` (stock thường thưa khung chính, 4K nặng), bản gốc giữ nguyên:
   ```
   ffmpeg -i assets/tulieu/da-chon/<clip>.mp4 -vf "scale=1920:1080:force_original_aspect_ratio=increase,crop=1920:1080,fps=30" -c:v libx264 -crf 18 -g 30 -keyint_min 30 -pix_fmt yuv420p -movflags +faststart -an .work/tulieu/<clip>.mp4
   ```
6. Dựng (mục "Dựng" dưới), theo luật "Khi dựng" ở sổ tay mục 10.

## Dựng

- **Thẻ bài báo**: `cong-cu\dung\hf-dung.js` (bản gốc; chép vào dự án). Cần `hf-chung.js` và CSS `the-bao.css` (cùng thư mục `cong-cu\dung\`), gsap, và các file `.js` bài báo nạp bằng `<script src="assets/tulieu/da-chon/<tên>.js">` trước nó.
  - `HFD.theBao(el, "<tên ảnh không đuôi>", { rong, tach, them, dem })`: thẻ ảnh chụp, viền mực, bóng khối đen lệch (S1). `tach: <px đầu ảnh>` cắt thành hai mảnh (tiêu đề + đoạn chứa câu) cho ảnh quá dài; `them`: thêm một bộ dòng bôi thứ hai trên cùng ảnh (lấy tọa độ từ lần chụp riêng câu đó).
  - `HFD.boi(tl, k.bo[i], t)`: vệt bôi chạy từng dòng. `HFD.vao`, `HFD.nguon` (dòng "NGUỒN: …"), `HFD.dienThoai`.
  - Cỡ thẻ: theo sổ tay mục 10, thẻ gần kín bề ngang để chữ đọc được (`rong` khoảng 1500–1700). Ở w1d4 thẻ chỉ rộng 760–1300 nên chữ nhỏ, chủ kênh chê.
- **Footage**: `<video class="clip" muted …>` trỏ bản `.work\tulieu\`; phủ kín khung theo sổ tay mục 10. Chỉ gắn màu `muted-editorial`, không nét vẽ Kuwahara (chủ kênh chốt 2026-10-26; bản v2b cũ có Kuwahara 0,75 làm ảnh loang như vỡ). Chạy trong PowerShell, `--file` là file chứa thẻ video:
  ```
  $g = '{\"preset\":\"muted-editorial\",\"intensity\":1,\"adjust\":{\"exposure\":0,\"contrast\":0.14,\"highlights\":-0.1,\"shadows\":0,\"blacks\":-0.12,\"temperature\":0.08,\"saturation\":-0.32},\"details\":{\"vignette\":0},\"effects\":{\"kuwahara\":0}}'
  npx.cmd --yes hyperframes media-treatment --file <file.html> --selector "#<id video>" --grading $g --apply --json
  ```
  Lệnh này tự chèn `data-hf-id` vào mọi thẻ của file; sửa file sau đó bằng script thì phải bắt script báo lỗi khi không khớp chuỗi (w1d4 v3 mất tiếng từ giây 31 vì thay `data-duration` của thẻ audio không khớp mà không ai biết).
- **Ảnh thật làm nền sân khấu** (cách làm từ `giao-thong-thuy-dien`, 18–20/10/2026; khi nào dùng: sổ tay mục 10 và minh-y mục "Hình thật"):
  - `<img class="p">` trong khung `.fo` phủ kín (`object-fit: cover`, chỉnh `object-position` để giữ phần mặt đất), gắn màu bằng cùng lệnh `media-treatment` như footage, `--selector "#<id ảnh>"`. Ảnh đen trắng để nguyên. Bản đồ và đồ họa thì không gắn màu.
  - Sticker đứng ở phần đất phía dưới, kèm bóng tiếp đất phẳng màu chàm (`.bong-dat`: hình elip `#1f2a44`, độ đục 0,45, không làm mờ). Máy quay trượt chậm (`kenBurns`).
  - Cần đổi hướng ảnh cho khớp ý câu (vd làn đầy xe phải nằm bên phải) thì lật bằng CSS `transform: scaleX(-1)` trên khung bọc ảnh, không lật trên chính `<img>` (GSAP ghi đè transform của ảnh khi máy quay trượt); file gốc giữ nguyên; ghi chú trong VAT-LIEU rằng chữ trong ảnh bị ngược.
  - Ảnh dưới khoảng 900 px phóng lên sẽ mềm, nay không còn nét vẽ Kuwahara che. Ghi kích thước vào gợi ý chọn để Long biết.
  - Lớp ảnh bị che hẳn thì tắt (`opacity: 0`) sau khi lớp mới hiện, kẻo `check` báo dòng ghi công của hai ảnh đè nhau.
  - Render: thời bản v2b có Kuwahara, `-w 3` hỏng với "window.__hf not ready" (`giao-thong-thuy-dien`), `-w 1` mất khoảng 8 phút cho mỗi phút video. Bỏ Kuwahara rồi, `longvd-chonngay` v2 chạy `-w 2` vẫn mất 121 phút cho 14 phút 25 giây video, gần bằng `-w 1` (127 phút); số tạm.
  - Cần tìm thêm ảnh cho một dòng sau khi đã chọn: tạo `.work\tim-<dòng>\assets\tulieu\truy-van.txt` rồi chạy `lay-tu-lieu.py` trên thư mục `.work\tim-<dòng>` (`--so 6`), để không ghi đè trang chọn và `NGUON.md` chính; ảnh chọn được thì chép vào `da-chon\` và ghi tay vào mục "Đã chọn" của `NGUON.md`.
- **Ảnh Wikimedia CC BY, CC BY-SA**: ghi công ngay dưới ảnh trên màn hình (tác giả, giấy phép) và trong `NGUON.md`.
- **Mẫu tham khảo**: `domino-30-phut\mau\mau-the-bao.html`, `mau-footage.html`; cả video w1d4 ở `domino-30-phut\compositions\`.
- **Soát trước khi gửi**: `snapshot` cần thêm `PRODUCER_PAGE_NAVIGATION_TIMEOUT_MS=180000` khi trang nặng; sau render đo tiếng nhiều đoạn (`ffmpeg -ss <giây> -t 3 -i <mp4> -vn -af volumedetect -f null NUL`), không chỉ xem hình.

## Bài học khi tìm (w1d4)

- Kho miễn phí gần như không có cảnh Việt Nam đặc thù (xe máy trong mưa, shipper Việt). Không ép: dòng đó vẽ.
- Pixabay trả nhiều clip lạc đề và clip trông như do AI sinh; tránh clip AI vì làm mất lòng tin khi video đang dùng tư liệu thật.
- Wikimedia không có ảnh tự do của nhiều doanh nhân (Tom Monaghan không có); khi đó vẽ nhân vật.

## Key (`cong-cu\.env`)

| Biến | Nguồn | Tình trạng 09/10/2026 |
|---|---|---|
| `PIXABAY_API_KEY` | Pixabay video và ảnh | đã có |
| `PEXELS_API_KEY` | Pexels video và ảnh | Pexels tạm ngừng cấp key mới; dán vào khi họ mở lại |
| `COVERR_API_KEY` | Coverr | API trả 401 khi không có key; chưa đăng ký |

Script tự đọc file này, không in key ra. Không dán key vào khung chat.

## lay-tu-lieu.py (loại A, B)

```
hf tulieu            (đứng trong thư mục dự án; tức là python -I cong-cu\lay-tu-lieu.py <thư mục dự án>)
```

- Đầu vào: `assets\tulieu\truy-van.txt`, mỗi dòng `#12 | A | rainy street night | pixabay, mixkit`. Cột nguồn trống thì dùng nguồn mặc định.
- Nguồn: loại A video `pixabay`, `mixkit`, `pexels`, `coverr`; loại A ảnh `pixabay-anh`, `pexels-anh`; loại B `wikimedia`.
- Mixkit chỉ tìm theo trang chủ đề: truy vấn một hai từ (`rain`, `pizza`), truy vấn dài ra 0.
- Không dùng được: Library of Congress (Cloudflare chặn, không lách), NARA (API đòi key), Archive.org (bỏ 09/10/2026). Cần thì tải tay, ghi vào mục "Tải tay" của `NGUON.md`.
- Lọc: video 3–20 giây, khung ngang, rộng từ 1280; xếp gần 16:9 lên trước. Giấy phép theo danh sách trắng: Pexels, Pixabay, Coverr, Mixkit **Free** (Restricted bị loại), Wikimedia chỉ PD, CC0, CC BY, CC BY-SA. File bị loại không tải, chỉ ghi vào `NGUON.md`.
- Ra: `assets\tulieu\ung-vien\`, khung xem trước trong `ung-vien\xem\`, `ung-vien.json`, `NGUON.md` (chỉ phần giữa hai dấu TU-DONG được viết lại), `so-sanh.html`.
- `--so 5` đổi số ứng viên mỗi truy vấn; `--chi-trang` chỉ viết lại `NGUON.md` và trang chọn.
- Wikimedia đòi User-Agent có liên hệ; script ghi email chủ kênh (chủ kênh đồng ý 09/10/2026).
- Adapter Pexels, Pixabay video, Coverr, Wikimedia import từ `_ngoai\OpenMontage` (AGPL-3.0), không sửa mã của nó.

## chup-bao.py (loại C)

```
hf bao               (đứng trong thư mục dự án; tức là python -I cong-cu\chup-bao.py <thư mục dự án>)
```

- Đầu vào: `assets\tulieu\bao.txt`, mỗi dòng `#21-25 | link | tiêu đề | câu cần bôi | nguồn ghi trên video`.
- Playwright (gói Python, cài 09/10/2026) chạy Chrome có sẵn trên máy, rộng 1280, ảnh nét gấp đôi.
- Ẩn trong ảnh chụp: thanh dính, popup, khung quảng cáo, cột bên. Không bấm đồng ý hay đóng gì.
- Ra: `assets\tulieu\bao\<mã>-<báo>.png` (cắt từ tiêu đề đến hết đoạn chứa câu) và `.json` cùng tên, ghi khung từng dòng của câu cần bôi theo điểm ảnh, để HyperFrames vẽ vệt bôi. Ảnh gốc không bị vẽ lên; khung vàng chỉ có trong ảnh xem trước.
- Trang bị chặn, đòi đăng nhập, hay không thấy câu: báo lại, không lách.
