# Bản lưu chuẩn nhìn HyperFrames

Mỗi thư mục con là **một bản cất nguyên bộ**: sổ tay, DESIGN, chuỗi style, Xu, và (ở bản trước đợt đổi) bộ file của video gần nhất. Mỗi bản có README riêng, ghi bản đó nhìn như thế nào và cách lấy ra dùng lại.

Luật (sổ tay mục 9):
- Trước mỗi đợt đổi chuẩn nhìn hay quy trình thì chụp bản trước; sửa xong thì chụp bản sau.
- Không sửa, không xóa file trong thư mục này.
- Chi tiết từng thay đổi ghi ở `../CHANGELOG.md`.

| Bản | Là gì | Video đã dùng |
|---|---|---|
| `2026-09-24_design-dau/` | DESIGN đầu tiên, trước luật chia việc vẽ và bút mực | các video trước Coca (Ford 5 đô dùng bộ lọc loang của đời này) |
| `2026-09-29_truoc-chuan-veo-moi/` | chuỗi giản lược (bảng màu khóa, sáng đều, cấm chữ), bút mực với bóng mềm và hậu cảnh mờ, Xu không mặt tối. Kèm trọn bộ file video Tupperware | Coca 5 xu, McDonald's, Tupperware |
| `2026-09-30_chuan-veo-moi/` | chuẩn Veo mới: hai chuỗi style, màu hai lớp, nét ba bậc, cel, chữ hai vai, Xu có mặt tối. Kèm tài liệu bàn giao | chưa có |
| `2026-09-30b_hf-tu-chu/` | như bản trên, cộng: HF thuần (khối không cần vật liệu thì dựng hoàn toàn bằng code), DESIGN 5.4 sân khấu HF thuần, nền motion graphic, đầu vào prompt Veo và luật tự quyết ảnh tham chiếu. Chuỗi style và Xu lấy ở bản trên | chưa có (thử đầu: Fremont và NUMMI) |
| `2026-10-02_bo-capcut/` | chỉ đổi quy trình: bỏ ghép CapCut, clip Veo đặt thẳng vào HyperFrames theo mốc từng dòng (Chặng 6); không dùng API trả phí. Chuẩn nhìn lấy ở hai bản trên | chưa có (thử đầu: Häagen-Dazs) |
| `2026-10-10_full-hf/` | đổi quy trình: full HyperFrames, mọi dòng là HF, Google Flow chỉ sinh nguyên liệu; `style-veo`, `style-sticker` dời vào đây. Chuẩn nhìn lấy ở các bản trên và khối style S1 trong `phongcach/` | w1d4 Domino's (`domino-30-phut`) |
| `2026-10-13_footage-minh-y/` | đổi quy trình chọn hình trong skill minh-y: việc "Thấy thật", mục "Hình thật", bài báo hiện một lần; tư liệu thật chỉ cho video chủ kênh cho phép. Kèm minh-y trước và sau, bộ file Domino's | chưa có |
| `2026-10-13b_minh-y-dau-vao-cong-cu/` | chỉ sửa minh-y: viết sẵn `truy-van.txt` và `bao.txt` cho công cụ tìm tư liệu khi video được phép | trungtamthuongmai (nếu dùng minh-y mới) |

Style Veo đời trước nữa (phát sáng, 20/09) chỉ còn ở các clip mẫu và khung cắt trong `phongcach/` (`*.mp4`, `khung/`), cùng `phongcach/VEO-STYLE-THU.md`.
