# Bản chuyển giao: mở xưởng kênh xếp hạng

Gửi Claude Code. Viết ngày 2026-11-14, sau hai buổi nghiên cứu style của chủ kênh với Claude (13–14/11). Gói này nằm ở `C:\hyperframestest\_ban-giao-kenh-xep-hang\`. Đọc hết file này, rồi làm các việc ở mục 2 theo thứ tự, xong thì dừng báo chủ kênh.

## 1. Việc này là gì

Long mở kênh YouTube thứ hai: xếp hạng (tier list), tên chưa đặt. Kênh dựng 100% bằng HyperFrames như Sinh Viên Kinh Tế, nhưng khác nét vẽ, khác giọng và khác luật chữ. Long muốn kênh này có **xưởng riêng** ở `C:\kenh-xep-hang`, ngang cấp với `C:\hyperframestest`, và muốn xưởng mới **thừa hưởng mọi kinh nghiệm** đã tích lũy ở xưởng gốc: máy, công cụ, quy trình sáu chặng, luật quyền, cách gỡ lỗi, cách ước giờ.

Cách thừa hưởng đã chọn: xưởng mới đọc luật máy và quy trình tại chỗ ở xưởng gốc, không chép sang (sổ tay mới, mục 0). Luật riêng của kênh (nét vẽ, chữ, nhân vật, bảng tier) viết mới trong sổ tay mới.

## 2. Việc cần làm, theo thứ tự

1. **Đọc trước:** `CLAUDE.md` trong gói này (sổ tay của xưởng mới), rồi `C:\hyperframestest\CLAUDE.md` các mục 2, 6, 8, 9, 10 và `cong-cu\HUONG-DAN-HF.md`. Thấy chỗ nào trong sổ tay mới mâu thuẫn với xưởng gốc mà mục 0 không giải được thì ghi lại để báo, đừng tự sửa.

2. **Tạo xưởng.** Tạo `C:\kenh-xep-hang` và các thư mục con theo sổ tay mới mục 8 (`phongcach\neo`, `phongcach\ban-luu`, `bang-tier`, `kho\nhan-vat`, `kho\meo`, `kho\nen`, `kho\canh`, `mau`). Việc này nằm ngoài `C:\hyperframestest`: chủ kênh giao việc này qua bản chuyển giao, nhưng vẫn hỏi một câu xác nhận trước khi tạo.

3. **Chép gói vào xưởng** (chép, không di chuyển, không xóa gói):
   - `CLAUDE.md` → `C:\kenh-xep-hang\CLAUDE.md`
   - `SO-TAY-STYLE.md` → `C:\kenh-xep-hang\SO-TAY-STYLE.md`
   - `phongcach\*` → `C:\kenh-xep-hang\phongcach\`
   - `bang-tier\bang-tier.html` → `C:\kenh-xep-hang\bang-tier\`
   - Tạo `VIDEO-DUOC-PHEP.md` (bảng trống, cùng khuôn với file ở xưởng gốc) và `phongcach\CHANGELOG.md` (một dòng mở xưởng).

4. **Gom bài thử đã duyệt vào `mau\`** (chép, không di chuyển). Chủ kênh sẽ chỉ chỗ nếu Claude Code không tìm thấy:
   - Ba tấm "Ai là triệu phú" 4K: `Character_sitting_in_game_show_c84ebb82_4K.jpg` (ngồi lì), `Character_panicking_in_chair_53557ed8_4K.jpg` (ôm đầu), `Editing_character_pose_and_expre__98688e8a_4K.jpg` (chỉ tay cười đểu). Thường nằm trong Downloads.
   - Bản chuyển cảnh A, B, C mà một phiên Claude Code đã dựng từ ba tấm trên (đợi chủ kênh xác nhận đó là thư mục nào; có thể là `uni-group-tierlist`, đang ghim trong Quick Access của File Explorer). Chép cả composition lẫn mp4: đó là mẫu chuẩn cho lối chuyển tư thế B và C.
   - Tấm sân khấu "Ai là triệu phú" bản vẽ không người, tấm giảng đường có nắng chiều, tờ gốc mèo xám: chép vào `phongcach\neo\` (`nen-ai-la-trieu-phu.png`, `nen-giang-duong.png`, `meo-xam.png`). Tờ gốc người mới (cậu gánh team bản "người ra người") chưa sinh xong; khi có thì đặt `phongcach\neo\nguoi.png`.

5. **Kiểm máy từ chỗ mới.** Tạo một dự án thử `C:\kenh-xep-hang\thu-xuong` (`npx.cmd hyperframes init thu-xuong`, mẫu Blank), đứng trong đó chạy `C:\hyperframestest\cong-cu\hf.cmd may`. Mục đích: chứng minh `hf` chạy được ngoài xưởng gốc. Có LỖI thì báo, đừng vá `hf.py` khi chưa hỏi.

6. **Chuyển bảng tier sang HyperFrames.** Viết `C:\kenh-xep-hang\bang-tier\bang-tier.js` từ trang mẫu `bang-tier.html`, theo sổ tay mới mục 4: đọc cấu hình JSON mà trang mẫu xuất ra, nét sôi tất định theo thời gian, font tay để trong dự án. Dựng một composition trình diễn trong `thu-xuong`: bảng hiện ra, ba món lần lượt bay vào ba hạng, một hạng đặc biệt (SSS hào quang) chèn lên đầu bảng. Chạy `hf check`, soi `hf snap`, render bản xem `hf render --khoi1`. Ghi tốc độ render đo được.

7. **Dừng, báo chủ kênh** một bảng ngắn: đã tạo gì, đã chép gì, `hf may` ra sao, bản trình diễn bảng tier ở đâu, các câu hỏi.

## 3. Những gì đã chốt trong hai buổi style (tóm tắt)

Đầy đủ ở `SO-TAY-STYLE.md`. Gọn lại:

- **Người ra người.** Nét nguệch ngoạc, có cằm, tai, mũi, lông mày; mỗi nhân vật một dấu riêng. Lối đầu trứng đã bỏ.
- **Nền theo thang**: nền trống, vài nét, phông vẽ có hồn, cảnh thật chuyển vào style, ảnh thật cắt dán.
- **Chữ được nằm trong ảnh**, đưa nguyên văn. Khác xưởng gốc.
- **Cảnh tình huống sinh liền người với cảnh**, 2–3 tư thế sửa từ một tấm gốc, hoán đổi nguyên tấm.
- **Chuyển tư thế kiểu B hoặc C**, không dùng A.
- **Kho vũ khí đổi style** cho cú đấm; mới có manga đã thử đạt.
- **Bảng tier vẽ tay** có hạng đặc biệt thêm được (trang mẫu).
- **Mèo xám** tai sứt, đuôi gãy là nhân vật kênh.

## 4. Những bài học từ phiên style, để khỏi mắc lại

- Prompt sót ngoặc vuông thì Nano Banana tự bịa (ra cướp biển, Dracula). Luôn đưa prompt hoàn chỉnh.
- Thứ tự ảnh đính phải khớp chữ "first", "second" trong prompt.
- Tờ gốc có đồ trên tay mà tư thế cần hai tay thì phải nói rõ đồ đó biến mất.
- Sửa chồng nhiều lớp thì nhân vật trôi dần; luôn sửa từ tờ gốc.
- Câu "drawn on a drawing tablet" làm mô hình vẽ thành ảnh chụp máy tính bảng; đã bỏ.
- Luật "màu xỉn, cấm phát sáng, cấm chữ" của phông vẽ làm cảnh thật mất hồn; cảnh thật có luật riêng.
- Mèo đen khó đọc (nét trong thành âm bản trắng trên đen); đã chuyển sang xám than.

## 5. Chặng tiếp theo sau khi xưởng mở

Dựng đoạn đầu của tập 1 (các kiểu thành viên nhóm thảo luận) theo sáu chặng. Cần chủ kênh đưa kịch bản và giọng đọc. Chưa có thì chờ, không tự viết kịch bản.
