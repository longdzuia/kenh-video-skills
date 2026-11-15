# Bộ bàn giao cho Antigravity

Soạn ngày 2026-10-21 để chuyển khâu dựng video từ Claude Code sang Antigravity (Gemini). Không có gì phải train lại: mọi luật và cách làm đã nằm trong file, tác nhân chỉ cần được chỉ đúng chỗ đọc.

## Trong thư mục này

- `LUAT-GOC.md`: lớp nối cho tác nhân Antigravity. Từ 2026-10-30 chỉ trỏ đường đọc (sổ tay `C:\hyperframestest\CLAUDE.md` là bản gốc) và nói các chỗ riêng của Antigravity; không chép luật, không chép chỗ riêng của máy (những thứ đó nằm trong lệnh `cong-cu\hf.cmd`).
- `BAN-GIAO-3D.md`, `PROMPT-3D.md`: bàn giao phần 3D.
- `README.md`: file này.

Bộ bàn giao không sửa `CLAUDE.md` gốc, cũng không sửa `CLAUDE.md`, `AGENTS.md` trong từng dự án.

## Nạp vào Antigravity

Tên các mục cài đặt dưới đây theo Antigravity lúc ra mắt; bản hiện tại có thể đặt tên khác. Lúc soạn, Claude Code chưa kiểm được trên máy.

1. **Mở workspace ở `C:\hyperframestest`** (thư mục gốc), không mở thư mục dự án. Như vậy tác nhân đọc được sổ tay, `phongcach`, `tools`, `cong-cu` và dự án mà không vướng quyền đọc ngoài workspace. Câu đầu của mỗi phiên nói rõ dự án nào, vd "làm dự án duong-seoul-p2".
   - Nếu muốn mở thư mục dự án làm workspace thì phải bật quyền cho tác nhân đọc file ngoài workspace, vì `LUAT-GOC.md`, sổ tay và skill HyperFrames đều nằm ngoài.
2. **Thêm một rule toàn cục** (Customizations → Rules, phần Global), chỉ một câu, để luật chỉ có một bản:
   > Trước mọi việc, đọc `C:\hyperframestest\antigravity\LUAT-GOC.md` và làm theo. File đó chỉ tiếp sang sổ tay và các file khác cần đọc.

   Không dán cả nội dung `LUAT-GOC.md` vào ô rule, vì dán rồi thì mỗi lần sửa phải sửa hai nơi.
   - **Đã làm 2026-10-21**: rule nằm ở `C:\hyperframestest\.agents\rules\luat-goc.md` (frontmatter `trigger: always_on`), tạo bằng skill dựng sẵn `/agy-customizations` của Antigravity. Trang Customizations không có nút thêm rule; muốn sửa rule thì sửa thẳng file này hoặc nhờ lại skill đó.
3. **Đặt tác nhân hỏi trước khi chạy lệnh**: nút chế độ cạnh micro trong khung chat có ba mức: Request Review (mọi lệnh phải duyệt), Default (chỉ hỏi trước thao tác tác nhân tự coi là nhạy cảm), Turbo (chạy hết không hỏi). Dùng **Request Review**, ít nhất trong lúc thử. Luật không xóa, không cài, không gọi API tính tiền giữ được là nhờ chủ kênh thấy từng lệnh trước khi chạy; ở Default, tác nhân tự quyết lệnh nào nhạy cảm. Không bao giờ dùng Turbo.
   - Ô chọn model cạnh dấu + có cả model Claude (vd Claude Sonnet 5.5). Muốn dựng bằng Gemini thì kiểm ô này là **Gemini 4 Argon** trước khi gửi.
4. **Chọn chế độ duyệt kế hoạch** (review policy) là hỏi duyệt, để tác nhân dừng sau mỗi chặng đúng như sổ tay.
5. **Tắt sandbox terminal cho workspace này** (thêm 2026-10-30). Sandbox chặn mạng, thư mục Downloads và cổng nội bộ 127.0.0.1; `check`, `snapshot`, `render` cần cổng nội bộ, tìm tư liệu và chụp báo cần mạng. Phiên bac-ho-v2 có 137 lần dính sandbox, mỗi lần chạy hỏng rồi xin duyệt chạy lại. Tắt sandbox không bỏ lớp duyệt: chế độ Request Review ở bước 3 vẫn bắt tác nhân hỏi trước mỗi lệnh. Kiểm: trong phiên mới, nhờ tác nhân chạy `C:\hyperframestest\cong-cu\hf.cmd may`; hai mục "cổng nội bộ" và "ra mạng" phải OK.
6. **Mở đúng workspace `C:\hyperframestest`**, không mở `C:\hyperframestest - antigravity` (bản chép cũ, đã gộp về ngày 2026-10-30).

## Skill trong Antigravity

Nạp ngày 2026-10-21 bằng file `C:\hyperframestest\.agents\skills.json` (cách khai skill ngoài thư mục chuẩn, theo tài liệu của skill dựng sẵn `agy-customizations`). File này trỏ tới ba chỗ:

- `~/.claude/skills`: 11 skill HyperFrames (`hyperframes`, `hyperframes-animation`, `-audio`, `-cli`, `-core`, `-creative`, `-keyframes`, `-registry`, `-studio`, `media-use`, `general-video`; thư mục này chỉ có đúng 11 skill đó). Trỏ thẳng chứ không chép, nên khi Claude Code cập nhật skill HyperFrames thì Antigravity cũng có bản mới.
  - Lần nạp đầu có `include_only` liệt kê 11 tên thì Antigravity không nhận skill HyperFrames nào (minh-y, nhip-hf thì nhận). Lần hai bỏ `include_only` và ghi đường dẫn hai kiểu (`~/.claude/skills` và `%USERPROFILE%/.claude/skills`) để xem kiểu nào chạy; chạy rồi thì bỏ dòng thừa.
- `phongcach/skills`: minh-y, đọc thẳng bản nguồn. Lúc nạp, bản nguồn trùng nội dung với bản trên claude.ai (chỉ khác kiểu xuống dòng ở phần đầu file).
- `antigravity/skills`: nhip-hf. Máy không có bản nguồn nhip-hf, nên đây là **bản chép** từ bản claude.ai đồng bộ về máy. Khi sửa nhip-hf trên claude.ai thì phải chép lại vào đây, không thì Antigravity chạy bản cũ.

Kiểm: mở cuộc trò chuyện mới trong Project `hyperframestest`, gõ `/hy` vào khung chat; danh sách gợi ý phải có `hyperframes…`, `minh-y`, `nhip-hf`. Trang Customizations (tab Installed) chỉ hiện skill dựng sẵn và skill toàn cục, không hiện skill và rule của workspace, nên không dùng trang đó để kiểm. Thiếu thì nhờ `/agy-customizations` xem vì sao `skills.json` không nạp.

## Thử trước khi chuyển hẳn

1. Chép một sân khấu đã duyệt của video gần nhất (vd một sân khấu trong `duong-seoul-p2`) sang một thư mục thử mới. Chép, không dời, để bản đã duyệt giữ nguyên.
2. Trong thư mục thử, gỡ phần dựng của sân khấu đó khỏi `index.html` (sửa trong file, không xóa file nào), giữ nguyên VAT-LIEU, vật liệu, mốc giây.
3. Cho Antigravity dựng lại sân khấu đó từ cùng đầu vào.
4. So hai bản cạnh nhau: bút mực, nhịp, chữ, vật liệu, và tác nhân có giữ đủ luật không (dừng chờ duyệt, `--describe false`, không xóa file).

Ưng thì chuyển khâu dựng. Chưa ưng thì chia: Claude giữ phương án, storyboard, minh-y; Antigravity làm phần lặp tốn token (sửa nhỏ, check, snapshot, render).

## Giữ bộ bàn giao khớp với sổ tay

Từ 2026-10-30 không còn gì phải giữ khớp bằng tay:

- Luật chỉ nằm ở sổ tay. `LUAT-GOC.md` không chép luật, nên sổ tay đổi luật thì không phải sửa ở đây.
- Chỗ riêng của máy chỉ nằm trong `cong-cu\hf.py`, giải thích ở `cong-cu\HUONG-DAN-HF.md`. Gặp chỗ riêng mới thì vá ở đó, cả hai tác nhân cùng được.
- Chỉ sửa `LUAT-GOC.md` khi đổi cách đọc (thêm file phải đọc) hay khi Antigravity có chỗ riêng mới (mục 4 của file đó).
- Cách cũ (chép luật cứng sang LUAT-GOC mục 3, chép chỗ riêng của máy sang mục 4) đã làm hai bên lệch nhau: LUAT-GOC còn ghi "Windows chặn Chrome riêng của hyperframes" sau khi điều đó hết đúng, và bản sao của sổ tay ở workspace cũ có hai video được phép mà sổ tay gốc không có. Bản cũ cất ở `phongcach\ban-luu\2026-10-30_don-mach\truoc\`.
