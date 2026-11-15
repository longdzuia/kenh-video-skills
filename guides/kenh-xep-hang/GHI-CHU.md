# thu-xuong: dự án thử của xưởng kênh xếp hạng

Tạo ngày 2026-11-14 theo bản chuyển giao `C:\hyperframestest\_ban-giao-kenh-xep-hang\BAN-GIAO.md` mục 2, bước 5–6.

## Kiểm máy từ chỗ mới

- Tạo bằng `npx.cmd --offline hyperframes@0.9.43 init thu-xuong --example blank --non-interactive --skip-skills` (bản 0.9.43 là bản ghim mới nhất ở xưởng gốc, đã có sẵn trong máy; `npx hyperframes` trơn đòi 0.9.44 chưa có trong máy nên báo lỗi khi chạy offline).
- `C:\hyperframestest\cong-cu\hf.cmd may` đứng trong thư mục này: mọi mục OK, "Máy sẵn sàng". `hf check`, `hf snap`, `hf render --khoi1` cũng chạy được ở đây.

## Bản trình diễn bảng tier

- `index.html` (8 giây): bảng hiện ra từng hàng (0–1,2 s), ba món bay từ chỗ của mèo vào S, B, D (1,6 / 2,6 / 3,6 s), hạng SSS hào quang chèn lên đầu bảng kèm rung khung 0,3 s (4,8 s), giữ bảng tới 8 s.
- Cấu hình bảng nằm trong khối `<script type="application/json" id="cau-hinh-bang">`, đúng khuôn trang mẫu xuất ra.
- Thành phần: `assets\bang-tier.js` (chép từ `C:\kenh-xep-hang\bang-tier\bang-tier.js`), font `assets\fonts\Pangolin-Regular.ttf` (Google Fonts, OFL, kèm `OFL.txt`).
- `hf check`: 0 lỗi; một cảnh báo `first_frame_empty` (khung 0 chỉ có nền vì bảng hiện ra từ trống), để nguyên vì bản trình diễn cần cảnh bảng hiện ra.
- Đã soát `hf snap`: dấu tiếng Việt của Pangolin đọc rõ ("Diễn giả", "Chỉ biết").
- Bản xem: `renders\thu-xuong_khoi1_v1.mp4` (8,0 s, 1,7 MB). Khung trích sau render ở `snapshots\sau-render\`.

## Tốc độ render đo được (số tạm, một lần đo)

- 8,0 s video mất 22,8 s render (chụp 16,0 s, 240 khung, 2 worker, `hyperframes@0.8.160`), tức khoảng 21 s video mỗi phút render. (Dòng tóm tắt của `hf` làm tròn thành 0,4 phút nên in ra 18 s/phút.)
- Bảng vẽ lại toàn bộ SVG mỗi khung mà không chậm hơn video chỉ ảnh tĩnh của xưởng gốc (khoảng 18 s/phút).

## Lỗi đã gặp khi dựng

- `hf check` báo `template_literal_selector`: `querySelector` có biến template trong `bang-tier.js`. Đổi sang bảng tra theo id.
- Món đang bay bị thu nhỏ: món dịch bằng transform làm `scrollHeight` của hàng phình ra, bảng tưởng hàng tràn. Đổi sang đo tràn theo `offsetTop`.

## File rác để chủ kênh tự xóa (nếu muốn)

- `snapshots\1114-225354\`, `snapshots\1114-225424\` (ảnh soát trước khi sửa lỗi món thu nhỏ).
- `AGENTS.md`, `CLAUDE.md` do `hyperframes init` tạo (hướng dẫn chung của HyperFrames, không phải sổ tay xưởng).
