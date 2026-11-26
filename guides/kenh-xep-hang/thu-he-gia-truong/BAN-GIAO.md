# Bàn giao — Dựng phác #3 Hệ gia trưởng (kênh xếp hạng, Tập 1)

*Viết ngày 2026-11-26, sau khi render bản v2. Người làm: Long (chủ kênh) + Claude Code. Đọc kèm `guides/kenh-xep-hang/CLAUDE.md` (sổ tay xưởng).*

## 1. Đây là gì

Tập 1 của kênh xếp hạng: **xếp hạng các kiểu thành viên trong nhóm thảo luận**. Bảng tier mới (chốt 25/11), 2 chữ, đo trực diện "nó gánh hay nó báo":

| Hạng | Tên | Món |
|---|---|---|
| S | Cứu tinh | Người hùng bục giảng |
| A | Trụ cột | Con nhà người ta, Chiến thần Canva, Đấng cứu thế |
| B | Được việc | **Hệ gia trưởng**, Nước đến chân mới nhảy |
| C | Báo thủ | Nô lệ ChatGPT, Người tối cổ |
| D | Ăn theo | Hoàn cảnh khó khăn, Nhân vật hư cấu |
| Ngoại hạng ẩn | Khổ chủ | Nhóm trưởng & Thuyết trình bất đắc dĩ (giấu tới cuối) |

**Chiến lược cuốn chiếu:** thay vì dựng cả tập, dựng hoàn chỉnh **một món đinh** để thử cảm giác nhịp, khoảng lặng, thoại phụ chen ngang và cú lật bảng. Món thử là **#3 Hệ gia trưởng**, đứng sau #1 Nô lệ ChatGPT (đã ở ô C) và #2 Con nhà người ta (vừa đậu ô A). Bản nháp cũ *Đứa lặn mất tăm* tạm gác.

## 2. Tình hình hiện tại

| Hạng mục | Trạng thái |
|---|---|
| Bảng kịch bản 22 nhịp (`bang-kich-ban.js`) | Xong, đã cập nhật số giây v2. Cột "Cần" vẫn ghi chữ `TẠM` của v1, chưa sửa theo ảnh thật. |
| Bản v1 (25/11) | 102,08 s, hình tạm vẽ SVG, giọng `edge-tts` toàn bộ. Đã cất. |
| **Bản v2 (26/11, 17:31)** | **98,38 s**, 1920×1080, 30 fps. Đủ ảnh thật (Nano Banana / Google Flow), giọng Mèo là giọng thật của chủ kênh, SFX thật. **Chưa có ghi nhận chủ kênh duyệt v2.** |
| Nhân vật Hệ gia trưởng | Đã có 4 tư thế + 1 bản đổi style manga (nữ, tóc đuôi ngựa, kính cận dày, gile đỏ đô, thẻ đeo xanh, bút đỏ). |
| Thẻ #1, #2 trên bảng | Đã có chân dung (thay thẻ chữ). |

### Mạch kể (22 nhịp, 5 phần)

1. **Giới thiệu (B1–B3):** bảng tier, Mèo lật thẻ, lặng 2 s nhìn mặt.
2. **Buổi họp đầu tiên: tự đẻ việc (B4–B9):** quán cà phê, đề "Word 15 trang + Slide"; Hệ gia trưởng đập bàn đòi mô hình 3D, 200 phiếu, phỏng vấn; lặng 2,5 s cả bàn đơ (rít ống hút); Mèo rụt rè phản đối; **cú đổi style manga**; cắt về Mèo cụp tai.
3. **Chuỗi tra tấn 07:00 → 02:00 (B10–B15):** Mèo tăng tốc dần (1,04x → 1,12x → 1,22x), mỗi câu bị Hệ gia trưởng chen ngang (loa, kính lúp, thả ngược như camera giám sát, giọng ngọt xớt "đập đi làm lại").
4. **Phanh gấp (B16–B17):** im tuyệt đối 1 s, Mèo ngồi bệt xuất hồn, giọng rã rời.
5. **Cú lật hạng & bóc phốt (B18–B22):** kéo thẻ nhử ô A → lặng liếc xéo → hất xuống **B — Được việc** "vì mình không thích"; bạn ngoài khung bóc phốt "nhờ nó mà ké được 9 điểm"; Mèo huýt sáo lảng sang món sau.

Tỉ lệ: 5 nhịp lặng (9,5 s), 6 nhịp xen, 11 nhịp lời.

## 3. Giọng và âm thanh

- **Mèo (11 nhịp):** cắt từ file giọng thật chủ kênh thu (`hegiatruong-giongmeo.mp3`), chỉnh tốc độ từng nhịp lúc dựng, -16 LUFS.
- **Hệ gia trưởng (5 nhịp) và Bạn ngoài khung (1 nhịp):** vẫn là `edge-tts` (giọng `vi-VN-HoaiMyNeural` / `NamMinhNeural`), **là giọng tạm**. Nguyên văn lời để thu thật ở `LOI-DOC-AI.md`.
- **SFX:** phần lớn đã thay bằng file thật CC0 (Freesound) hoặc thư viện HyperFrames; nguồn từng file ở `NGUON-SFX.md`. Còn 4 âm tổng hợp: rung điện thoại, thở hắt, nốt đàn trầm, huýt sáo; trống dồn cũng tổng hợp.

## 4. Việc còn mở

1. **Chủ kênh duyệt v2** trên điện thoại: nhịp có ăn không, lặng có đủ, cú lật hạng có bật cười không. Đây là mục đích của bài thử.
2. **Giọng thật cho Hệ gia trưởng và Bạn** (cần giọng nữ cho Hệ gia trưởng, người đã đồng ý). Nếu dùng OmniVoice thì nhớ luật cấm thương mại (sổ tay mục 10).
3. **Nhạc nền ghi công chưa khớp:** `KIEM-KE-TAI-NGUYEN-HGT.md` ghi `trivial-call.mp3` là *Blue Dot Sessions, CC BY 3.0*, còn `NGUON-SFX.md` ghi *Kevin MacLeod, CC BY 4.0*. Phải kiểm lại trước khi đăng, vì CC BY bắt buộc ghi công trong mô tả video.
4. **Nhịp 22 dài hơn ước** (~5,7 s so với 4,5 s): cân nhắc rút huýt sáo.
5. Sửa cột "Cần" trong bảng kịch bản cho khớp ảnh thật; đưa tờ nhân vật Hệ gia trưởng và cảnh quán cà phê vào `kho\` để các món sau dùng lại (hiện `kho\nhan-vat\`, `kho\nen\` còn trống).
6. Render v2 chạy bằng HyperFrames 0.8.160 trong khi dự án ghim 0.8.216; lần render sau nên chạy đúng bản ghim.
7. Nếu v2 đạt: rút bài học vào sổ tay (sau ít nhất 2 món, theo luật không rút luật từ một video), rồi làm món tiếp theo theo cùng cách.

## 5. File trong thư mục này (bản lên GitHub chỉ có chữ)

| File | Nội dung |
|---|---|
| `BAN-GIAO.md` | File này. |
| `GHI-CHEP.md` | Nhật ký dựng v1 và v2: bảng mốc giây thật từng nhịp, tốc độ giọng, lỗi đã sửa. |
| `bang-kich-ban.js` | Bảng kịch bản 22 nhịp (mở bằng `bang-kich-ban\bang-kich-ban.html?du-lieu=...`). |
| `LOI-DOC-AI.md` | Nguyên văn lời 3 vai, chia khối để đưa vào công cụ tạo giọng. |
| `KIEM-KE-TAI-NGUYEN-HGT.md` | Kiểm kê ảnh/âm có sẵn trong xưởng ngày 25/11 (trước v2), gửi bên viết prompt. |
| `NGUON-SFX.md` | Nguồn và giấy phép từng file âm thanh bản v2. |

Video, ảnh, âm thanh, `index.html` và script dựng nằm trên máy của Long tại `C:\kenh-xep-hang\thu-he-gia-truong\` (repo không chứa media theo quy tắc). Video v2: `renders\thu-he-gia-truong_v2.mp4` (49 MB) — cần thì xin Long gửi qua Drive.
