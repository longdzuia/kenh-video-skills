# Sổ tay xưởng video — kênh xếp hạng

File này là bộ não của xưởng kênh xếp hạng (tier list, tên kênh chưa đặt). Claude Code không nhớ gì giữa các phiên, nên mọi luật và quy trình phải nằm ở đây hoặc trong các file được trỏ tới. Đọc hết file này trước khi làm bất cứ việc gì. Khi một luật thay đổi, sửa ngay trong file và ghi một dòng vào Nhật ký thay đổi ở cuối.

Chủ kênh là Long. Chủ kênh nói bằng lời thường; việc của Claude Code là quy lời đó về đúng chặng, đúng luật trong sổ tay này.

Xưởng này mở ngày 2026-11-14, ngang cấp với `C:\hyperframestest` (xưởng Sinh Viên Kinh Tế). Hai xưởng chung máy, chung công cụ, chung chủ kênh, nhưng khác giọng, khác nét vẽ, khác luật chữ.

## 0. Thừa hưởng từ xưởng gốc

`C:\hyperframestest` đã chạy hơn 30 video bằng HyperFrames. Mọi kinh nghiệm về máy, công cụ, quy trình và cách làm việc ở đó là của xưởng này luôn. Cách thừa hưởng: **đọc tại chỗ, không chép luật sang**, để khi xưởng gốc sửa một chỗ về máy hay công cụ thì xưởng này dùng ngay bản mới.

**Đọc ở xưởng gốc và làm theo** (thứ tự đọc khi mở phiên đầu):

| Ở `C:\hyperframestest` | Áp thế nào cho xưởng này |
|---|---|
| `CLAUDE.md` mục 2 (sáu chặng) | Áp, trừ chỗ mục 2 dưới đây ghi khác. |
| `CLAUDE.md` mục 6, `cong-cu\HUONG-DAN-HF.md` (lệnh `hf`) | Áp nguyên. Gọi bằng đường tuyệt đối `C:\hyperframestest\cong-cu\hf.cmd <lệnh>`, đứng trong thư mục dự án của xưởng này. `hf` tìm công cụ theo đường tuyệt đối nên chạy được ở bất kỳ thư mục nào có `index.html`. |
| `CLAUDE.md` mục 8 (luật quyền) | Áp nguyên, chỉ đổi phạm vi: xem mục 7 dưới đây. |
| `CLAUDE.md` mục 9 (cách làm việc) | Áp nguyên: gỡ lỗi tối đa 10 phút, ước giờ từ số đo, không rút luật từ một video, cất bản trước khi đổi. |
| `CLAUDE.md` mục 10 (tư liệu thật, sound effect) | Áp luật nguồn, giấy phép, danh sách cấm, cách đặt thẻ báo và footage. Danh sách video được phép là file riêng của xưởng này (mục 6). |
| `CLAUDE.md` mục 11 (giọng đọc, văn nói) | Đọc để học, chưa phải luật ở đây. |
| `phongcach\DESIGN.md` mục 3.7, 3.8, 5.1–5.3, 7, 8 | Đọc để học về hiệu ứng, bố cục, động tác, chuyển ý, chống lặp, nhịp độ. Không áp phần màu, font, bút mực. |
| Thư viện dựng: `hf-chung.js` của dự án gần nhất, `cong-cu\dung\` | Chép sang dự án, không sửa bản gốc. |
| `phongcach\skills\minh-y\SKILL.md` | Đọc để học cách phân việc từng dòng và gom sân khấu. Không chạy nguyên bản cho kênh này (luật chữ và style khác). |

**Không áp ở xưởng này:** mục 3 phần "chữ hai vai" và mục 4 (bút mực, hạt giấy, mực đo theo sticker), mục 5 (khuôn prompt S1, S3), `style-*.txt` của xưởng gốc, `DESIGN.md` phần màu và font, nhân vật Xu. Thay bằng mục 3–5 dưới đây.

**Không ghi vào `C:\hyperframestest`.** Đọc thì được. Cần vá `hf.py` hay công cụ gốc vì lỗi máy thì báo chủ kênh trước, vá theo `HUONG-DAN-HF.md` của xưởng gốc, vì xưởng gốc vẫn dùng chung.

Nếu luật ở đây mâu thuẫn với xưởng gốc: điểm nào thuộc nét vẽ, chữ, nhân vật thì luật ở đây thắng; điểm nào thuộc máy, công cụ, quyền thì xưởng gốc thắng. Không rõ thuộc loại nào thì dừng hỏi chủ kênh.

## 1. Kênh

- Video YouTube xếp hạng các thứ theo hạng (SS, S, A…) hoặc theo một tiêu chí, đề kiến thức và đời sống, giọng vui. Cảm hứng từ dòng kênh "Những…" như Vui Vẻ, biến thành xếp hạng.
- Đề tập đầu: xếp hạng các kiểu thành viên trong nhóm thảo luận, mỗi kiểu một biệt danh châm biếm.
  - **Tiêu chí & Bảng Tier mới Tập 1 (rút gọn 2 chữ, đo trực diện "nó gánh hay nó báo", cập nhật 2026-11-25):**
    - **S — Cứu tinh**: độc tôn cho *Người hùng bục giảng*
    - **A — Trụ cột**: *Con nhà người ta*, *Chiến thần Canva*, *Đấng cứu thế*
    - **B — Được việc**: *Hệ gia trưởng*, *Nước đến chân mới nhảy*
    - **C — Báo thủ**: *Nô lệ ChatGPT*, *Người tối cổ*
    - **D — Ăn theo**: *Hoàn cảnh khó khăn*, *Nhân vật hư cấu*
    - **Ngoại hạng ẩn — Khổ chủ** (giấu tới cuối bài): *Nhóm trưởng & Thuyết trình bất đắc dĩ*
  - **Chiến lược test cuốn chiếu (2026-11-25):** Tạm gác bản nháp *Đứa lặn mất tăm* cũ (`thu-lan-mat-tam-v2\`). Dựng phác hoàn chỉnh 1 món đinh trước để test cảm giác nhịp, khoảng lặng, thoại phụ chen ngang và cú lật bảng tier; món test đầu tiên là **#3 Hệ gia trưởng** (`thu-he-gia-truong\`, ngay sau khi *#1 Nô lệ ChatGPT* đã ở ô C và *#2 Con nhà người ta* vừa đậu ô A).
- Khung 16:9, 1920×1080.
- **Bảng tier là ngôi nhà** của kênh: video quay về nó nhiều nhất (mục 4).
- **Mèo xám là nhân vật kênh** (mục 5).
- Điểm đặc biệt nhất của kênh: hình phải tự nhiên, có chất con người, giống vẽ tay nhất có thể. Nét Google Flow mặc định đuổi theo sự hoàn hảo; mọi khối style ở đây là để kéo nó về phía người vẽ nghiệp dư.

## 2. Dây chuyền

Sáu chặng như xưởng gốc mục 2, mỗi chặng xong dừng chờ chủ kênh duyệt. Chỗ khác:

- **Chặng 0.** Tạo dự án trong `C:\kenh-xep-hang`, không trong xưởng gốc: mở PowerShell ở `C:\kenh-xep-hang`, `npx.cmd hyperframes init <tên-dự-án>`, mẫu Blank. Trong `assets` đặt `giongdoc.mp3`, `kichban.txt`, `mach.txt`, chép `phongcach\style-*.txt` của xưởng này. Chép `bang-tier\bang-tier.js` (khi đã có, mục 4) vào dự án. Đầu mỗi phiên chạy `C:\hyperframestest\cong-cu\hf.cmd may`.
- **Trước chặng 0 có chặng nội dung** (mục 2a): từ ý tưởng ra bảng kịch bản, duyệt xong mới tạo dự án. Kịch bản của xưởng này là bảng kịch bản; cột Lời chép ra `kichban.txt` cho chặng mốc giờ. Khi chủ kênh đưa kịch bản lời viết sẵn thì vẫn qua skill nhip-hf, rồi lên bảng kịch bản từ đó.
- **Chặng 2 (nguyên liệu).** Claude Code tự viết `VAT-LIEU.md` theo sổ tay này, học cách phân việc của minh-y nhưng theo luật mục 3. Mỗi tờ cần sinh có prompt hoàn chỉnh, **không để sót ngoặc vuông**: ở phiên style ngày 13/11, một prompt còn `[COSTUME]` chưa điền làm Nano Banana tự vẽ cướp biển và Dracula. Ghi rõ ảnh nào đính, theo thứ tự nào.
- **Chặng 4 (tách nền)** chỉ cần cho thứ đứng trên nền trống hoặc dán lên ảnh thật (mục 3). Cảnh tình huống sinh liền một tấm thì không tách.
- **Chặng 5–6** như xưởng gốc. Render bằng `hf render`.

## 2a. Chặng nội dung: từ ý tưởng ra bảng kịch bản

Mở ngày 2026-11-16, sau tập 1: đồ họa đạt nhưng nội dung còn nghiêm, vì kịch bản lời viết xong hết rồi mới đem dựng, không có chỗ cho hình, khoảng lặng, meme. Chặng này là **thứ tự cố định và một bộ câu hỏi**, không phải khuôn. Câu trả lời đổi theo từng đề; không rút độ dài, số hạng, vai mèo hay tỉ lệ lời/lặng từ một video mẫu nào.

1. **Danh sách đi trước.** Đề, tiêu chí xếp, các món, chia mấy hạng và tên hạng: do đề quyết. Danh sách là list chủ kênh có sẵn hoặc cùng lên. Chưa đào chất liệu ở bước này.
2. **Chất liệu đến sau, phục vụ từng món.** Có danh sách rồi mới đào cho từng món: khoảnh khắc ai cũng từng gặp, meme hợp, cảnh thật, con số. Chất liệu làm món sống hơn, không quyết món nào có mặt.
3. **Chọn cách kể**, bằng câu hỏi:
   - Cả tập: mèo đóng vai gì (người thuyết trình, người trong cuộc, nạn nhân…)? Tùy đề.
   - Từng món, nghĩ theo thứ tự: **Thấy gì?** (cảnh làm người xem nhận ra hoặc bật cười) → **Lặng ở đâu, trong lặng có gì?** (hành động, ánh mắt, âm thanh, cú xen; không lặng suông) → **Lời gài gì, châm gì?** Cái hay nằm ở cả ba móc vào nhau. Hình và lặng dẫn, lời đi sau nhưng không tạm bợ: lời vẫn giữ cái châm biếm, cợt nhả của kênh.
   - Có cần xen gì không (meme, cú đổi style, nhân vật phụ cãi, lạc đề…)? Lấy từ kho đồ nghề `phongcach\kho-do-nghe.md`. Không tập nào bắt buộc có đủ.
   - **Chủ kênh chốt sau bản thử "Đứa lặn mất tăm" (2026-11-16):** (a) mỗi món **giới thiệu trước, xếp hạng ở cuối** ("tiếp theo chúng ta đến với…", kể đặc điểm, diễn vui, rồi mới đặt lên bảng); (b) món là phần nội dung chính, **lời phải đủ và có cảm xúc**: kể chuyện bằng câu trọn, câu cụt chỉ để chốt; (c) **người xem không phải vừa đọc vừa nghe**: chữ cần đọc (tin nhắn, giấy tờ) thì lời im, hoặc lời đọc đúng chữ đó, và chữ đứng đủ lâu để đọc; (d) **thời gian trong chuyện nhảy thì có câu nói rõ**, không chỉ để màn hình tự đổi.
   - Soi bảng bằng 7 câu hỏi ở cuối `mau\HOC-TU-VIDEO-MAU.md` (mổ 4 video mẫu, mỗi video có bảng dựng ngược để xem). Câu hỏi, không phải khuôn.
4. **Bảng kịch bản.** Trang `bang-kich-ban\bang-kich-ban.html` (mở bằng trình duyệt), dữ liệu mỗi dự án ở một file `.js` (cách viết ở đầu `bang-kich-ban\mau-du-lieu.js`). Mỗi dòng một nhịp, cột: **#, giây, Loại** (Lời / Lặng / Xen), **Thấy** (màn hình chiếu gì, mèo làm gì), **Lời** (nguyên văn, ai nói), **Lặng / Xen** (lặng bao lâu và trong đó có gì; gợi ý meme, đổi style, cảnh thật), **Âm**, **Cần** (nguyên liệu có sẵn hay phải sinh). Bảng này là kịch bản: thu giọng đọc cột Lời, dựng phác đọc cả bảng, `VAT-LIEU.md` lấy nguyên liệu từ cột Cần. Đây là chỗ chủ kênh duyệt kỹ nhất, vì sửa ở đây rẻ nhất.
5. **Dựng phác** bằng HyperFrames với hình tạm (sticker trong kho, khung chữ), theo giây ước của bảng, chưa cần giọng thật, để xem nhịp có ăn không. Ảnh khung của bản phác gắn vào từng dòng bảng (trường `anh`). Ổn rồi mới viết prompt Nano Banana và thu giọng.

Mỗi bước xong dừng chờ chủ kênh duyệt, như sáu chặng. **Kho đồ nghề** lớn dần: mỗi video tham khảo chủ kênh gửi và mỗi tập làm xong thêm vài món vào kho, kèm "dùng khi nào".

## 3. Luật nhìn

Chi tiết, lý do và bằng chứng ở `SO-TAY-STYLE.md` (bản xuất ngày 2026-11-14 của sổ tay style chủ kênh giữ trên Claude). Khối style chép nguyên văn từ `phongcach\`.

**Nhân vật người.** `phongcach\style-nguoi.txt`. Người ra người: nét nguệch ngoạc, có cằm, tai, mũi một nét, lông mày; đầu khoảng một phần ba người. Đã bỏ lối đầu trứng (13/11) vì đứng cạnh mèo thì người không ra người. Mỗi nhân vật một dấu riêng nhìn bóng dáng là nhận ra; dàn sáu kiểu của tập đầu ở `SO-TAY-STYLE.md`. Mỗi đứa một tờ gốc, sinh từng tờ một.

**Nền: một cái thang, mỗi câu leo đúng nấc nó cần.**

| Nấc | Dùng khi | Làm bằng |
|---|---|---|
| Nền trống | cận mặt, phản ứng (nhiều nhất) | code tô một màu phẳng |
| Vài nét | cần biết đang ở đâu | sinh chung với nhân vật |
| Phông vẽ | đến một nơi mới | `phongcach\style-nen.txt` + chi tiết sống |
| Chuyển cảnh thật vào style | nhại một nơi ai cũng biết | `phongcach\khuon-chuyen-canh-that.txt` |
| Ảnh thật cắt dán | món đem ra xếp, nơi có thật | ảnh thật, nhân vật vẽ đặt lên (chỉ video được phép, mục 6) |

Phông vẽ không được vẽ giỏi hơn nhân vật. Phông phải có dấu vết người sống (phấn viết dở, chai nước bỏ quên, ghế lệch) và một mốc giờ trong ngày, nếu không sẽ lạnh như mô hình 3D. Cảnh thật giữ màu gốc và chữ ký nơi chốn; ánh sáng vẽ thành mảng phẳng có viền tay.

**Chữ.** Khác xưởng gốc: **chữ được nằm trong ảnh** (biển, băng rôn, khẩu hiệu, logo, chữ phấn), vì cảnh Việt Nam sống nhờ chữ và ảnh tĩnh của Nano Banana Pro ít lỗi chữ. Luôn đưa nguyên văn trong ngoặc kép; nhắc tên đồ vật mà không đưa chữ thì mô hình hay tự dán nhãn vô nghĩa. Chữ thông tin của video (tên hạng, biệt danh, con số, chú thích) vẫn do HyperFrames viết bằng font tay (mục 4).

**Dựng cảnh tình huống: sinh liền người với cảnh** (chủ kênh chốt 13/11). Ghép nhân vật vào phông bằng Nano Banana, rồi sửa ra 2–3 tư thế **từ cùng một tấm gốc**; khuôn ở `phongcach\khuon-sua-anh.txt`. HyperFrames hoán đổi nguyên tấm theo nhịp lời. Đã so điểm ảnh ba tấm "Ai là triệu phú": nền gần như đứng im, khác biệt chỉ quanh nhân vật. Thấy nền nhấp nháy thì cắt vùng nhân vật dán lên tấm gốc. Ảnh 4K phóng khoảng 1,3 lần vẫn nét; cận mặt mạnh hơn thì sinh riêng.

**Chuyển tư thế** (chủ kênh xem trên điện thoại, 13/11): bản B (cắt phựt + rung khung 0,3 giây tắt dần + phóng nhẹ 1,2–1,3 lần vào mặt) và bản C (như B + nhân vật rung nhẹ liên tục trong lúc giữ tấm, nền đứng yên) đều hợp. Bản A chỉ cắt phựt thì không nổi, không dùng. Cú quay về mặt lì cuối nhịp là chỗ người xem bật cười.

**Cú đổi style.** Đến khoảnh khắc đắt nhất thì nhân vật vẽ lại bằng một style khác (manga, kinh dị, cổ động, Đông Hồ, pixel…), giữ 1–2 giây, cắt phựt vào, cắt thẳng về mặt lì. Kho vũ khí, khuôn chung và mức đổi ở `SO-TAY-STYLE.md`. Mới có manga đã thử đạt. Đích đến chọn trong họ mực và in ấn; cấm chuyển sắc mịn, da bóng, phát quang, dựng 3D (thủ phạm của bệnh nhựa AI).

## 4. Bảng tier

Thiết kế đã chốt ngày 2026-11-14: trang mẫu `bang-tier\bang-tier.html` (mở bằng trình duyệt để xem và chỉnh). Bản dùng trong video là thành phần HyperFrames `bang-tier\bang-tier.js` chuyển từ trang đó (bản đầu viết 2026-11-14, chưa duyệt; cách dùng ở đầu file, bản trình diễn ở `thu-xuong`). Font kèm theo ở `bang-tier\fonts\`.

- Viền ô và hàng là nét tay run (đường cong bậc hai lệch ngẫu nhiên, mỗi cạnh hai lượt nét), ô hạng tô màu phẳng lệch mép như tô sáp, chữ hạng viết tay. Khung mẫu chừa khoảng 30% bên phải cho mèo đứng.
- Hạng mặc định: SS (hào quang), S, A, B, C, D. **Hạng đặc biệt thêm được bất kỳ lúc nào**: tên tự đặt, màu tự chọn, vị trí lên xuống, kiểu tô (tô kín, gạch chì), hiệu ứng (hào quang xoay, lấp lánh, sọc cấm). Bốn mẫu có sẵn: SSS, Ngoài vũ trụ, Cấm cửa, Thùng rác. Bảng bao nhiêu hàng cũng chia đều chiều cao.
- Trang mẫu xuất được cấu hình JSON (danh sách hạng và món); dự án đọc cấu hình đó để dựng bảng.
- **Khi chuyển sang HyperFrames phải tất định:** nét sôi trong trang mẫu đổi hình bằng đồng hồ máy; trong video, hạt ngẫu nhiên của nét phải tính từ thời điểm khung (vd đổi 7–8 lần mỗi giây theo `floor(t × 8)`), để render lần nào cũng ra giống nhau.
- Font tay: trang mẫu dùng Pangolin (Google Fonts, có tiếng Việt). Trong dự án tải file font về `assets\fonts\`, không gọi Google Fonts lúc render. Soát dấu tiếng Việt bằng `hf snap` trước khi dùng.

## 5. Mèo xám, nhân vật kênh

Chi tiết và prompt ở `phongcach\meo\meo-xam.md`. Tóm lược: mèo xám than béo lùn, đứng hai chân, mắt lệch mí nặng, khinh khỉnh; tai trái sứt, đuôi gãy khúc, bụng xám nhạt hơn một bậc. Mũ đặt giữa hai tai, không gì che mắt, luôn sửa từ tờ gốc. Mèo là ảnh sinh bằng Nano Banana, không dựng bằng code như Xu. Tên chưa đặt.

## 6. Tư liệu thật

Danh sách video được dùng tư liệu thật của xưởng này ở `C:\kenh-xep-hang\VIDEO-DUOC-PHEP.md`; mặc định là không, như xưởng gốc. Kênh này đặc biệt hợp ảnh thật cho món đem ra xếp và cho lối cắt dán; đó là đề xuất, hỏi chủ kênh khi giao từng dự án.

## 7. Luật quyền

Như xưởng gốc mục 8, với phạm vi:
- Làm việc trong `C:\kenh-xep-hang`.
- Đọc `C:\hyperframestest` được; gọi `hf` được; ghi vào đó thì không (mục 0).
- Không xóa file nào, không cài gì khi chưa hỏi, không dùng dịch vụ tính tiền, không đụng cài đặt bảo mật Windows, không tự dừng preview hay Chrome của chủ kênh.

## 8. Cấu trúc thư mục

```
C:\kenh-xep-hang\
  CLAUDE.md               sổ tay này
  SO-TAY-STYLE.md         sổ tay style (bản xuất), lý do và bằng chứng
  VIDEO-DUOC-PHEP.md      video được dùng tư liệu thật
  phongcach\              khối style, khuôn prompt, mèo, ảnh neo
    neo\                  ảnh neo nét (tờ gốc người, tấm giảng đường, tờ gốc mèo)
    ban-luu\              bản cũ cất nguyên bộ khi đổi chuẩn
    CHANGELOG.md          đổi gì, từ gì sang gì, vì sao, ngày nào
  bang-tier\              trang mẫu bảng tier, sau thêm bang-tier.js
  bang-kich-ban\          trang xem bảng kịch bản (chặng nội dung, mục 2a)
  giong-doc\              giọng đọc: VOICESTUDIO.md (mục 10), file đo thử
  kho\                    nguyên liệu dùng lại: nhan-vat\, meo\, nen\, canh\
  mau\                    bài thử đã duyệt (ba tấm "Ai là triệu phú", bản chuyển cảnh B và C)
  <tên-dự-án>\            mỗi video một thư mục, cấu trúc như xưởng gốc mục 7
```

## 9. Đang theo dõi (chưa chốt)

- Âm thanh cho mỗi cú cắt và cú đổi style.
- Ảnh thật cắt dán: chưa thử tấm nào.
- Thumbnail: chưa bàn.
- Hành vi gạt khỏi bảng của mèo: chưa thử.
- Skill nguyên liệu riêng cho kênh (bản minh-y của kênh xếp hạng): làm khi đã chạy vài video.
- Giọng đọc lâu dài: OmniVoice hay VieNeu-TTS hay ElevenLabs, giọng mẫu của chủ kênh (mục 10).

## 10. Giọng đọc

Đọc `giong-doc\VOICESTUDIO.md` trước mọi việc dính tới giọng đọc. File đó là bàn giao phiên nghiên cứu VoiceStudio 16–17/11, gồm: cài đặt và lỗi Smart App Control, giấy phép, chế độ Truyện, thẻ nào chạy ở đâu kèm số đo, cách gọi API cục bộ để Claude tự tạo giọng, và các lựa chọn thay thế. Bốn điều phải nhớ:

- **Mô hình OmniVoice cấm dùng thương mại**, kể cả âm thanh tạo ra. Mua gói Pro không đổi được điều này. Video dùng OmniVoice chỉ đăng khi kênh chưa bật kiếm tiền; trước khi bật phải tắt quảng cáo, đăng lại hoặc ẩn các video đó. Giọng mẫu phải là giọng của chủ kênh hoặc của người đã đồng ý.
- **Lời đọc làm ở chế độ Truyện**, xuất MP3. Thẻ `[slow]`, `[fast]` chỉ chạy ở chế độ này và đo thấy gần như không tác dụng. Nhanh chậm và cao độ chỉnh lúc dựng, giữ cao độ.
- **Thẻ cảm xúc** chỉ có 13 thẻ OmniVoice viết đúng y chữ; `[pause …]` chạy mọi nơi.
- **Card 4 GB chậm:** khoảng 90–180 giây cho một câu ngắn. Mỗi lượt tạo 200–450 ký tự.

## Nhật ký thay đổi

- 2026-11-14 — Mở xưởng. Sổ tay viết từ phiên nghiên cứu style 13–14/11 trên Claude (bản chuyển giao `_ban-giao-kenh-xep-hang`). Thừa hưởng xưởng gốc bằng cách đọc tại chỗ (mục 0).
- 2026-11-14 — Mục 4: ghi `bang-tier.js` đã có bản đầu (chưa duyệt) và chỗ để font. Không đổi luật.
- 2026-11-16 — Thêm mục 2a (chặng nội dung trước chặng 0: danh sách → chất liệu → cách kể → bảng kịch bản → dựng phác), trang `bang-kich-ban\`, kho đồ nghề `phongcach\kho-do-nghe.md`. Lý do: tập 1 đồ họa đạt nhưng nội dung còn nghiêm vì kịch bản lời viết xong mới dựng. Bản trước: `phongcach\ban-luu\2026-11-16_so-tay-truoc-chang-noi-dung\`.
- 2026-11-16 — Mục 2a bước 3: thêm bốn điểm chủ kênh chốt sau bản thử "Đứa lặn mất tăm" (giới thiệu trước hạng sau, lời đủ và có cảm xúc, không bắt vừa đọc vừa nghe, mốc thời gian nói rõ) và trỏ tới 7 câu hỏi soi bảng ở `mau\HOC-TU-VIDEO-MAU.md`. Lý do: v1 mở bằng hạng, lời cụt, tin nhắn hiện đè lời, thời gian nhảy không báo. Thêm công cụ `bang-kich-ban\dung-nguoc.py`, `boc-loi.py` (dựng bảng ngược từ video mẫu). Bản trước: `phongcach\ban-luu\2026-11-16_so-tay-truoc-hoc-video-mau\`.
- 2026-11-17 — Thêm mục 10 (Giọng đọc) trỏ tới `giong-doc\VOICESTUDIO.md`, bàn giao phiên nghiên cứu VoiceStudio 16–17/11 (cài đặt, giấy phép OmniVoice cấm thương mại, chế độ Truyện, số đo thẻ tốc độ và kéo chữ, API cục bộ, VieNeu-TTS). Mục 8, 9 thêm dòng theo. Không đổi luật cũ. Bản trước: `phongcach\ban-luu\2026-11-17_ghi-giong-doc\`.
- 2026-11-15 — `bang-tier\bang-tier.js` thêm tùy chọn `kichThuoc: {w, h}`: bảng đặt trong cảnh con thì truyền vào, để khung đầu tiên khi render nhảy thẳng vào giữa cảnh vẫn vẽ đúng (gặp ở `tap01-nhom-thao-luan` SK5). Không đổi luật. Bản trước: `phongcach\ban-luu\2026-11-15_bang-tier-kich-thuoc\`.
- 2026-11-25 — Mục 1: cập nhật khung Tập 1 mới (bảng tier 2 chữ đo trực diện "gánh hay báo": S Cứu tinh, A Trụ cột, B Được việc, C Báo thủ, D Ăn theo, ngoại hạng ẩn Khổ chủ) và chiến lược test cuốn chiếu món đinh `#3 Hệ gia trưởng` (tạm gác bản nháp *Đứa lặn mất tăm*). Bản trước: `phongcach\ban-luu\2026-11-25_cap-nhat-tap01-he-gia-truong\`.
