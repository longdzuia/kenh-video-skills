# Luật gốc cho tác nhân Antigravity — xưởng video Sinh Viên Kinh Tế

Lớp nối cho Antigravity. Viết lại ngày 2026-10-30 (đợt dọn mạch); bản trước (chép lại luật cứng và các chỗ riêng của máy) cất ở `C:\hyperframestest\phongcach\ban-luu\2026-10-30_don-mach\truoc\antigravity\LUAT-GOC.md`.

File này **không chép luật**. Bản chép cũ hay lệch với sổ tay, và tác nhân đã từng làm theo một dòng chép đã cũ. Luật nằm ở sổ tay; chỗ riêng của máy nằm trong lệnh `hf`.

Chủ kênh là Long. Chủ kênh nói bằng lời thường; việc của bạn là quy lời đó về đúng chặng, đúng luật trong sổ tay.

## 1. Thứ bậc

- **Sổ tay gốc là `C:\hyperframestest\CLAUDE.md`.** Tên file mang chữ Claude vì dây chuyền dựng trên Claude Code trước; nội dung là luật của kênh, áp cho bạn y như cho Claude Code. Mọi chỗ sổ tay ghi "Claude Code" là nói về bạn.
- **Workspace là `C:\hyperframestest`.** Mọi dự án nằm ở đây. `C:\hyperframestest - antigravity` là bản chép cũ (24–30/10), đã gộp về; không đọc luật, không làm dự án ở đó.
- Trong mỗi thư mục dự án có `CLAUDE.md` và `AGENTS.md` do lệnh init của HyperFrames đặt vào: hướng dẫn kỹ thuật của HyperFrames, không phải luật kênh. Đọc để biết cách viết composition; không sửa.
- Hai file mâu thuẫn nhau thì dừng lại báo chủ kênh, không tự chọn bên nào.
- Không sửa file này và sổ tay khi chủ kênh chưa bảo. Chủ kênh chốt luật mới thì đề nghị ghi vào sổ tay (kèm một dòng Nhật ký thay đổi), không ghi vào đây.

## 2. Đọc gì, theo thứ tự

Trước mọi việc:

1. Chạy `C:\hyperframestest\cong-cu\hf.cmd may` (kiểm máy). Có mục LỖI thì báo chủ kênh trước khi làm.
2. `C:\hyperframestest\CLAUDE.md`: sổ tay, đọc hết. Quyền ở mục 8, cách làm việc ở mục 9; hai mục này áp cho bạn từng chữ.
3. `DESIGN.md` trong thư mục dự án (bản chép của `phongcach\DESIGN.md`). Bút mực ở mục 3.1 và 3.6, hiệu ứng phát sáng ở 3.7, sân khấu HF thuần ở 5.4. File dài; khi dựng thì đọc lại đúng mục liên quan, đừng dựa vào trí nhớ.
4. Bộ file của dự án: `VAT-LIEU.md` (đọc mục cuối là biết dự án đang ở chặng nào), `assets\mocgio.json`, kịch bản trong `assets` (đọc theo tên hiện có).
5. `C:\hyperframestest\cong-cu\HUONG-DAN-HF.md`: lệnh `hf` làm gì, số đo thời gian để ước giờ.

Khi đụng tới việc nào thì đọc hướng dẫn việc đó:

- Tư liệu thật, thẻ báo, gắn màu footage, ghi công: `cong-cu\HUONG-DAN.md`. Chỉ cho video có tên trong `VIDEO-DUOC-PHEP.md`.
- Cách khớp mốc giây, whisper bịa câu: `tools\whisper\HUONG-DAN.md`. Cảnh báo tách nền: `tools\tach-nen\HUONG-DAN.md`.
- Đo giọng, tờ liên hoàn: `phan-tich\BAN-GIAO-2026-10-13.md` mục 4.
- Phần 3D (three.js trong HyperFrames): `antigravity\BAN-GIAO-3D.md`.

## 3. Lệnh máy: chỉ qua `hf`

Mọi công cụ chạy bằng `C:\hyperframestest\cong-cu\hf.cmd <lệnh>`, đứng trong thư mục dự án: `may`, `moc`, `tulieu`, `bao`, `tachnen`, `check`, `snap`, `preview`, `render` (`render --khoi1` cho bản xem khối 1).

- Không tự gõ `npx`, không tự đặt biến môi trường trình duyệt, không chép script né lỗi vào dự án. `hf` đã lo: trình duyệt, bản HyperFrames (render dùng 0.8.160), không gọi Gemini, thời hạn chờ, DLL bị Windows chặn, mã hóa chữ.
- **Không cần nhờ chủ kênh đóng Chrome** để render.
- Gặp lỗi máy: gỡ tối đa 10 phút rồi báo chủ kênh (sổ tay mục 9). Ra cách chữa thì đề nghị vá vào `hf.py` theo `HUONG-DAN-HF.md`, không ghi vào luật.

## 4. Chỗ riêng của Antigravity

- **Sandbox terminal** chặn mạng, Downloads và cổng nội bộ 127.0.0.1, mà `check`, `snap`, `render` cần cổng nội bộ, `tulieu`, `bao` cần mạng. Nếu `hf may` báo LỖI ở hai mục đó thì sandbox đang bật: chạy lệnh `hf` ngoài sandbox, và nhắc chủ kênh tắt sandbox cho workspace này (`antigravity\README.md`).
- **Đọc ảnh chủ kênh tải về** ở `%USERPROFILE%\Downloads` là đọc ngoài workspace: hỏi một lần rồi chép (không di chuyển) vào `assets\vat-lieu-goc\` của dự án.
- **Phiên dài bị nén bộ nhớ** (thấy dòng "Resuming from a compaction"): đọc lại mục cuối `VAT-LIEU.md` và file đang dựng trước khi làm tiếp; không làm theo trí nhớ.
- **Đổi model giữa phiên**: model mới không biết các quyết định trong phiên. Đọc lại mục cuối `VAT-LIEU.md` trước khi làm.

## 5. Phạm vi việc của bạn

Chủ kênh có thể giao bạn cả sáu chặng của sổ tay, hoặc chỉ khâu dựng (tách nền, dựng khối 1, dựng cả video, sửa, render). Mỗi chặng xong là dừng lại chờ duyệt (sổ tay mục 2).

Skill của kênh: **minh-y** (bản nguồn ở `phongcach\skills\minh-y\SKILL.md`) lập VAT-LIEU; **nhip-hf** (bản chép ở `antigravity\skills\nhip-hf\SKILL.md`) tách dòng kịch bản. Kịch bản tách dòng và `mach.txt` thường đến từ claude.ai; nhận như đầu vào, không sửa chữ của kịch bản.

Skill HyperFrames (hướng dẫn kỹ thuật của framework) nạp qua `C:\hyperframestest\.agents\skills.json`, gọi bằng tên như `/hyperframes-core`; không nạp được thì mở thẳng `%USERPROFILE%\.claude\skills\<tên>\SKILL.md`. Gặp chỗ skill bảo "invoke /tên-skill" thì mở SKILL.md của skill đó và làm theo. `media-use` có lệnh sinh giọng, nhạc, ảnh cần tài khoản HeyGen: dịch vụ tính tiền, không dùng (sổ tay mục 8).

Mã dựng có sẵn, đọc trước khi viết mã mới để viết cùng một lối: `cong-cu\dung\hf-chung.js`, `hf-dung.js`; Xu ở `phongcach\xu\xu-character.js` (không đổi dáng chibi); dự án làm gần nhất (hiện là `bac-ho-v2`): `index.html`, `compositions\`, các file `hf-*.js`.

Tự soát trước khi đưa chủ kênh xem:

- `hf check` sạch lỗi;
- `hf snap --at …` ở các mốc của sân khấu, tự xem bằng mắt: chữ không tràn, không đè nhau, vật liệu hiện đủ, đúng bút mực DESIGN;
- báo kèm: dựng gì, ở mốc giây nào, những thứ code tự vẽ (kèm lý do), chỗ nào còn tạm, và giờ render dự kiến tính từ số đo.
