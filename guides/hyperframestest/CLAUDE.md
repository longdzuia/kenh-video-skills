# Sổ tay xưởng video — Sinh Viên Kinh Tế

File này là bộ não của dây chuyền. Claude Code không nhớ gì giữa các phiên, nên mọi luật và quy trình phải nằm ở đây hoặc trong các file được trỏ tới, không nằm trong lịch sử trò chuyện. Đọc hết file này trước khi làm bất cứ việc gì. Khi một luật thay đổi, sửa ngay trong file và ghi một dòng vào mục Nhật ký thay đổi ở cuối.

Chủ kênh là Long. Chủ kênh nói bằng lời thường; việc của Claude Code là quy lời đó về đúng chặng, đúng luật trong sổ tay này.

## 0. Các file chỉ dẫn và thứ bậc

- `C:\hyperframestest\CLAUDE.md` (file này): luật kênh, quy trình, quyền.
- `phongcach\DESIGN.md`: phong cách hình ảnh chi tiết, bút mực ở mục 3.6. Đây là bản gốc; bản trong từng dự án chỉ là bản chép.
- `phongcach\style-nhan-vat.txt`: khối style gốc cho tờ nhân vật (style S3 "chibi biểu cảm", từ 2026-11-05; trước đó là S1). Ảnh neo nhân vật: `phongcach\neo\nhan-vat.png`.
- `phongcach\style-do-vat.txt`: khối style gốc cho tờ đồ vật, đạo cụ (cùng nét và màu S1, cấm mặt và tay chân).
- `phongcach\style-nen.txt`: khối style gốc cho ảnh nền nơi chốn.
- Bản `assets\style-*.txt` trong từng dự án chỉ là bản chép. `style-veo.txt`, `style-sticker.txt` (quy trình Veo cũ) đã cất ở `phongcach\ban-luu\2026-10-10_full-hf\phongcach-cat\`; `phongcach\style.txt` là chuỗi giản lược đời trước nữa. Không dùng các chuỗi này cho đối sách full HF.
- `phongcach\CHANGELOG.md`: nhật ký chi tiết mọi thay đổi chuẩn nhìn (đổi gì, từ gì sang gì, vì sao, ngày nào).
- `phongcach\ban-luu\`: các bản cũ cất nguyên bộ, mỗi bản một thư mục có README hướng dẫn dùng lại (xem mục 9).
- `tools\...\HUONG-DAN.md` (hai file): cách dùng whisper và tách nền.
- `phongcach\xu\xu-character.js`: nhân vật Xu, bản gốc.
- `phongcach\skills\minh-y\SKILL.md`: bản nguồn của skill minh-y, sửa ở đây rồi tải lên claude.ai. Bản skill máy đang chạy là bản đồng bộ từ claude.ai, không sửa trực tiếp.
- `CLAUDE.md` và `AGENTS.md` trong từng thư mục dự án: hướng dẫn kỹ thuật gốc của HyperFrames, do lệnh init đặt vào. Không sửa.
- `cong-cu\hf.cmd` (mã ở `hf.py`) và `cong-cu\HUONG-DAN-HF.md`: lệnh chung chạy mọi công cụ, và nơi duy nhất giữ các chỗ riêng của máy (mục 6).
- `VIDEO-DUOC-PHEP.md`: danh sách video được dùng tư liệu thật (mục 10).
- `antigravity\LUAT-GOC.md`: lớp nối cho Antigravity. Chỉ trỏ đường đọc và nói chỗ riêng của Antigravity, không chép luật; luật nằm ở file này.

**Một xưởng, hai tác nhân.** Claude Code và Antigravity cùng làm trong `C:\hyperframestest`, dùng chung sổ tay này. `C:\hyperframestest - antigravity` là bản chép cả xưởng ngày 24/10 cho phiên thử 3D; mọi dự án trong đó đã được chép về đây ngày 2026-10-30. Không làm tiếp ở bản chép đó.

Nếu hai file mâu thuẫn nhau, dừng lại báo chủ kênh, không tự chọn bên nào.

## 1. Dây chuyền

**Đối sách full HyperFrames (chủ kênh chốt 2026-10-10).** Cả video dựng bằng HyperFrames, mọi dòng là HF. Google Flow (Nano Banana, Veo) chỉ còn là bộ công cụ sinh nguyên liệu: nền, nhân vật, đồ vật. Không còn khối VEO, không còn clip Veo đặt vào video.

- Kịch bản đi qua skill **nhip-hf**: ra danh sách mạch (`mach.txt`) và kịch bản từng dòng dạng `#n.mp3-HF-câu`.
- Skill **minh-y** đọc kịch bản và mốc giây, phân việc từng dòng, gom thành sân khấu, viết VAT-LIEU.md (prompt các tờ nhân vật, đồ vật, nền còn thiếu) và chỉ dẫn cho tác nhân Flow.
- Chủ kênh (hoặc tác nhân Flow) sinh ảnh trên giao diện, Claude Code tách nền và dựng.
- Bản render cuối của HyperFrames là video hoàn chỉnh.

Quy trình Veo cũ (nhip-doan, khối VEO/HF, Minh Ý bản 5, clip Veo ở Chặng 6, chuỗi `style-veo`/`style-sticker`) cất nguyên ở `phongcach\ban-luu\2026-10-10_full-hf\` và các bản lưu trước; có thể lấy lại khi cần.

Sân khấu HF không bắt buộc có vật hay người. Nhiều khối là **HF thuần**, dựng hoàn toàn bằng code: biểu đồ, sóng, tầng lớp, dòng chảy, nền motion graphic. Đó là sân khấu riêng của HF. Khi khối cần vật hay người thì lấy từ sticker sinh bằng Nano Banana Pro theo khối style S1 (mục 5), không do code tự vẽ (xem mục 3).

## 2. Sáu chặng

Mỗi chặng xong là **dừng lại chờ chủ kênh duyệt**, không tự chạy sang chặng sau.

### Chặng 0 — Tạo dự án

Chủ kênh tự làm trước khi mở tác nhân (Claude Code hay Antigravity):

- Mở PowerShell tại `C:\hyperframestest` bằng cách gõ `powershell` vào thanh địa chỉ File Explorer.
- Gõ `npx.cmd hyperframes init <tên-dự-án>`, chọn mẫu **Blank**. Phải dùng `npx.cmd` vì máy chặn chạy file `.ps1`; gõ `npx` trơn sẽ báo lỗi.
- Với bản HyperFrames hiện tại, init xong sẽ tự mở studio và đứng chờ. Khi thư mục đã có `index.html` thì bấm Ctrl+C, chọn Y để dừng.
- Trong `assets` đặt `giongdoc.mp3`, `kichban.txt`, `mach.txt` (đầu ra của nhip-hf), và `style-nhan-vat.txt`, `style-do-vat.txt`, `style-nen.txt` chép từ `phongcach` (lưu UTF-8, kiểm `kichban.txt` không phải 0 byte), cùng thư mục trống `vat-lieu-goc`. Chép vào dự án `phongcach\xu\xu-character.js` và `phongcach\DESIGN.md`. Tên file kịch bản có lệch (vd `kichban (4).txt`) thì Claude Code đọc theo tên hiện có, không đổi tên.
- (Quy trình Veo cũ còn `assets\veo-prompt.txt`, `assets\veo\`, `assets\veo-clip\`; đối sách full HF không dùng.)
- Mở Claude Code bằng app Claude, tab Code, chọn thư mục dự án, chọn Opus, bật accept edits. Hoặc mở Antigravity ở workspace `C:\hyperframestest` (luôn là thư mục gốc), câu đầu nói tên dự án; cách cài ở `antigravity\README.md`.
- Video được dùng tư liệu thật thì nói ngay khi giao dự án; tác nhân thêm một dòng vào `VIDEO-DUOC-PHEP.md`.
- **Đầu mỗi phiên, tác nhân chạy `hf may`** (mục 6). Có mục LỖI thì báo chủ kênh trước khi làm.

### Chặng 1–6

Viết lại ngày 2026-10-24 theo cách đã chạy ở `giao-thong-thuy-dien`, `duong-seoul`, `duong-seoul-p2`, `ngay-dep-test-anti` và `longvd-chonngay`. Bản Veo cũ của các chặng này cất ở `phongcach\ban-luu\2026-10-24_chang-full-hf\truoc\CLAUDE.md`.

`VAT-LIEU.md` là sổ ghi của dự án. Xong mỗi chặng, thêm vào cuối file một mục có ngày gồm:
- kết quả;
- chỗ khác kế hoạch;
- việc đang chờ chủ kênh;
- file rác để chủ kênh tự xóa.

Phiên sau đọc VAT-LIEU là biết dự án đang ở chặng nào. Quyết định của chủ kênh ghi vào đúng mục đó, kèm ngày.

1. **Mốc giây.**
   - Chạy `hf moc` (whisper rồi `khopdong.py`; cách khớp và cách vá ở HUONG-DAN của whisper) ra `assets\mocgio.json`.
   - Báo tỉ lệ khớp và các đoạn khớp kém. Whisper hay nuốt một câu hoặc nghe sai tên riêng: nghe lại riêng đoạn đó rồi sửa tay, ghi lý do vào khóa `ghi_chu`, giữ bản chưa sửa trong `.work`.
2. **Nguyên liệu: skill minh-y viết `VAT-LIEU.md`.**
   - Chạy minh-y theo skill. VAT-LIEU gồm:
     - ý chung và vật thể chính chạy xuyên video;
     - bảng phân việc từng dòng;
     - các sân khấu kèm nhịp có số giây;
     - đối chiếu kho, rồi các tờ cần sinh theo thứ tự sinh, mỗi tờ có dòng **Tham chiếu**;
     - Tin; Thấy thật (kèm hai khối `truy-van.txt`, `bao.txt` khi video được phép); Hiểu; Cảm;
     - mục **"Những thứ code tự vẽ"**, mỗi thứ một câu lý do (mục 3);
     - câu hỏi cho chủ kênh.
   - **Phương án sân khấu:** vật thể chính đề xuất ngay trong mục "Ý chung" và hỏi chủ kênh trong mục câu hỏi. Chỉ viết `PHUONG-AN.md` (2–3 phương án, ghi từng sân khấu là HF thuần hay có vật liệu) khi chủ kênh muốn.
   - **Storyboard:** không còn file riêng; mục Sân khấu của VAT-LIEU là storyboard.
   - **Kho:** chưa có `kho\` thì tìm trong `assets\vat-lieu`, `assets\nen` của các dự án cũ, nhân vật chỉ nhận style S3 (sinh từ 2026-11-05), đồ vật và nền nhận style S1 (sinh từ 2026-10-07). Nhân vật S1 cũ không trộn với nhân vật S3 trong cùng một video; cần người cũ thì sinh lại bằng S3. Dùng lại thì chép, không di chuyển.
   - **Link bài báo** phải do chủ kênh đưa hoặc duyệt. Claude Code được tìm và đọc trang, nhưng chạy `chup-bao.py` sau khi chủ kênh gật.
   - Báo bảng ngắn (số sân khấu, số tờ phải sinh, số mục dùng lại, câu hỏi) rồi dừng.
3. **Sinh ảnh và tìm tư liệu.** Các việc dưới đây chạy song song.
   - **Ảnh, chủ kênh làm.**
     - Chủ kênh dán các tờ ở mục "Cần sinh" vào tác nhân Google Flow (đã cài chỉ dẫn `phongcach\TAC-NHAN-FLOW.md`), chọn bản và tải bản 4K; nền rộng ít nhất 2560 px.
     - Claude Code không sinh ảnh, không gọi API (mục 8).
   - **Tư liệu thật**, chỉ video có tên trong `VIDEO-DUOC-PHEP.md` (mục 10). Tác nhân chạy quy trình ở `cong-cu\HUONG-DAN.md`:
     - chép hai khối thành `assets\tulieu\truy-van.txt` và `bao.txt`;
     - chạy `hf tulieu`, rồi mới chạy `hf bao`. Không chạy song song: hai công cụ cùng ghi `ung-vien.json` nên mất mục;
     - ghi bảng gợi ý chọn vào VAT-LIEU (kích thước, giấy phép, lý do), rồi dừng chờ chủ kênh chọn trên `so-sanh.html`;
     - chép file được chọn vào `da-chon\`, ghi `NGUON.md`, chuyển mã footage vào `.work\tulieu\`.
     - Không tìm được hình đúng thì phương án vẽ dự phòng trong VAT-LIEU phải sinh: báo chủ kênh tờ nào thêm vào danh sách sinh.
   - **Sound effect**, chỉ video chủ kênh cho thử (mục 10).
     - Ứng viên vào `assets\sfx\ung-vien\`.
     - Chủ kênh nghe và chọn trước khi dựng khối 1.
4. **Tách nền.** Không có sticker thì bỏ qua chặng này.
   - Chủ kênh báo chỗ để ảnh đã tải (thường là Downloads). Chép, không di chuyển, vào `assets\vat-lieu-goc\` với tên gọn (bỏ đuôi `_a_4K_…`); nền chép thêm vào `assets\nen\`.
   - Chạy `hf tachnen` (mục 6) ra `assets\vat-lieu\`. Tờ bị dính tư thế thì tách lại với `hf tachnen --gop n`.
   - Mở `_xem-nhanh.png` cho chủ kênh. Xem từng cảnh báo nghi hỏng: khe thật hay thủng nhầm.
   - Ghi vào VAT-LIEU: bảng tờ → sticker → tên ngắn dùng ở mục Sân khấu; tờ nên sinh lại; file rác để chủ kênh tự xóa.
5. **Dựng khối 1.** Dựng một đoạn đầu (một hay vài sân khấu đầu, thường là mạch 1 hoặc phần mở bài) để chủ kênh duyệt nhìn trước khi làm cả video.
   - Mỗi sân khấu một sub-composition `compositions\skN.html`; `index.html` chỉ gọi các sân khấu, giọng đọc và sound effect.
   - Thư viện dùng chung (`hf-chung.js`, `xu-character.js`, `cong-cu\dung\`) chép từ dự án gần nhất, không viết lại từ đầu.
   - Mốc lấy từ `mocgio.json`, không đoán. Có thể sinh `assets\moc.js` cho composition đọc.
   - Thứ gì code vẽ mà không có trong mục "Những thứ code tự vẽ" thì báo kèm lý do trước khi dựng.
   - Chạy `hf check`, soi `hf snap --at …` ở những chỗ vừa dựng, mở preview (`hf preview`).
   - Render bản xem bằng `hf render --khoi1` (ra `renders\<tên>_khoi1_vN.mp4`). Ghi vào VAT-LIEU tốc độ render đo được (giây video mỗi phút render) để ước giờ render cả video.
   - Ghi vào VAT-LIEU chỗ khác kế hoạch ở mục Sân khấu. Dừng chờ duyệt.
6. **Dựng cả video và render.** Khi chủ kênh bảo dựng tiếp:
   - **Dựng.**
     - Dựng đủ sân khấu theo VAT-LIEU. Khối 1 đã duyệt giữ nguyên, trừ khi chủ kênh bảo sửa.
     - Ảnh và footage thật chỉ gắn màu `muted-editorial`, không nét vẽ Kuwahara (mục 10); sound effect đã chọn đặt dưới giọng đọc (mục 10).
   - **Soát trước khi render.**
     - Chạy `hf check` (video 3–4 phút mất khoảng 7 phút mỗi lượt). Cả phim quá hạn giờ của công cụ thì check từng đoạn (`hf check --range đầu,cuối`).
     - Soi snapshot từng sân khấu, sửa chữ đè, id trùng, lớp che sót.
   - **Render** bằng `hf render` (dùng `hyperframes@0.8.160`, mục 6) ra `renders\<tên>_vN.mp4`, bản cũ giữ nguyên. Ước giờ bằng tốc độ đo ở khối 1, không đoán (số tạm: video chỉ ảnh tĩnh khoảng 18 giây video mỗi phút render; có clip phim khoảng 8,5 giây, tức video 3–4 phút mất khoảng 25 phút). Chạy nền, báo chủ kênh giờ xong dự kiến, hỏi tiến độ thì báo số khung đã chụp trên tổng.
   - **Soát sau render.**
     - Đo tiếng nhiều đoạn: `hf render` tự đo ở 10%, 50%, 90% thời lượng; chỗ nghi thì đo thêm theo `cong-cu\HUONG-DAN.md`, mục "Soát trước khi gửi".
     - Trích khung nhiều chỗ vào `snapshots\` để so với bản dựng.
     - Báo thời lượng, cỡ file, thời gian render.
   - Chủ kênh xem và chỉ chỗ sửa. Mỗi lần sửa render ra bản `vN` mới.

Sau video: quan sát (prompt nào hỏng, chỗ chủ kênh sửa tay, nhịp) ghi ở cuối VAT-LIEU. Thứ dùng được cho video sau thì đề nghị ghi vào mục 10 hoặc thành luật theo mục 9.

## 3. Luật chia việc vẽ

Hai câu hỏi, theo thứ tự.

**Câu 1: khối này có cần vật liệu không?** Ý của khối có cần người xem **nhận ra** một vật, một người hay một nơi cụ thể không?
- **Không cần → HF thuần.** Cả khối do code dựng: biểu đồ, sóng, tầng lớp, lưới, dòng chảy, sơ đồ nút, số liệu, nền motion graphic. Không sticker, không ảnh nền. Đây là sân khấu riêng của HF, không mượn từ Veo (DESIGN 5.4).
- **Cần → HF có vật liệu.** Chỉ thứ phải nhận ra mới là ảnh; phần còn lại vẫn là code.
- Không lấy vật liệu chỉ vì cảnh Veo đã có sẵn thứ đó. Ý về dòng tiền, tỉ lệ, cơ chế, chi phí thường nói rõ hơn bằng hình trừu tượng hơn là bằng đồ vật.

**Câu 2: phần phải vẽ, code có vẽ đẹp được không?** Không chia theo loại vật.

- **Code vẽ**: thứ dựng từ hình học — khung, mũi tên, đường nối, thanh, sóng, tầng, lưới, nút, số, chữ, nền motion graphic — cùng toàn bộ chuyển động.
- **Ảnh lo**: thứ có đường viền tự nhiên phức tạp — vật, người, bản đồ, bờ biển, tòa nhà, cây, đám đông, khuôn mặt. Hai dạng: sticker, hoặc ảnh nền không tách nền.
  - Khối cần người xem nhận ra một nơi có thật thì nơi đó là ảnh nền sinh theo chuỗi Veo, vẽ kín mép.
  - Nếu ý chỉ là dòng chảy, mạng lưới hay phạm vi thì dựng bằng hình trừu tượng (nút, đường, vùng). Không vẽ nơi chốn bằng code.
  - **Bản đồ: chọn linh hoạt theo hiệu ứng** (chủ kênh chốt 2026-10-20).
    - Cần hiệu ứng khó (tô dần từng nước hay từng vùng, vùng đổi màu, đường đi chạy trên bản đồ, phóng từ châu lục vào một nước, biên giới dịch chuyển) thì dựng bằng code **từ dữ liệu địa lý thật** (GeoJSON, TopoJSON của kho công), để chuyển động dễ làm.
    - Chỉ cần đặt nhãn, mũi tên hay vài chấm lên thì dùng ảnh bản đồ có sẵn trên Wikimedia (chọn bản trơn hoặc ít chữ, đọc giấy phép, ghi công dưới ảnh); nhãn HF đè lên chữ nước ngoài trên ảnh nếu có.
    - Không bao giờ vẽ tay đường viền bản đồ trong code, và không sinh bản đồ bằng Nano Banana (đường biên dễ sai).
    - **Chủ quyền** (chủ kênh chốt 2026-10-20): bản đồ có Việt Nam hay Biển Đông phải thể hiện quần đảo Hoàng Sa và Trường Sa thuộc Việt Nam. Gọi là Biển Đông; không dùng tên "South China Sea", không có đường lưỡi bò. Ảnh Wikimedia không đạt (thiếu hai quần đảo, ghi "South China Sea", có đường lưỡi bò) thì không dùng, dựng bằng code từ dữ liệu địa lý thật và tự đặt hai quần đảo.
- **Xu** vẫn là code, vì cần nhép miệng và đổi biểu cảm.
- **Chữ chia hai vai.**
  - *Chữ thông tin* (con số, nhãn biểu đồ, tiêu đề, từ khóa) luôn do HyperFrames viết, không bao giờ nằm trong ảnh.
  - *Chữ thế giới* (biển hiệu, bảng quảng cáo, màn hình, logo thương hiệu thật trên vật thật) thuộc về ảnh: Veo, ảnh nền, sticker. Chỉ có ở nơi hoặc vật ngoài đời có nó, đúng chính tả, không bao giờ mang số.
  - HF không vẽ biển hiệu giả; ảnh không mang số liệu.
- **Nhân vật lịch sử** chỉ sống trong một video: làm tờ nhiều tư thế bằng ảnh, không dựng code như Xu.

Thứ gì không nằm trong mục "Những thứ code tự vẽ" của VAT-LIEU.md thì không được tự vẽ. Danh sách này để soát, không để hạn chế: khối HF thuần có danh sách dài là bình thường. Bài học video Coca: hai cảnh bản đồ do code vẽ ra thô như nét trẻ con vì lọt khỏi vòng soát. Lỗi ở đó là code bắt chước đường viền tự nhiên bằng tay, không phải là code vẽ nhiều; bản đồ dựng từ dữ liệu địa lý thật không mắc lỗi này.

## 4. Bút mực (đang thử)

Chi tiết ở DESIGN.md mục 3.1 và 3.6. Tóm lược:
- Nét có đậm nhạt, đầu nét vuốt nhọn, dựng thành hình tô kín từ đường tâm; nét hơi run, góc hơi chồng nét.
- Nét có thứ bậc như Veo: đậm cho nhân vật và vật chính, mảnh cho đồ vật, xám xanh cho vật ở xa.
- Mực đo theo sticker của từng video, thường ra gần đen, và hòa vào giấy.
- Nền là tấm hạt giấy mịn, không lớp lốm đốm.
- Đổ sáng kiểu cel: vật có thể tích có một mặt sáng và một mặt tối phẳng; bóng đổ và bóng tiếp đất là mảng phẳng màu chàm, không blur. Hướng sáng theo khối Veo kề bên.
- Chiều sâu tạo bằng thứ bậc nét và độ tương phản, không bằng làm mờ.
- **Hiệu ứng được phát sáng** (chủ kênh chốt 2026-10-28, bỏ luật cũ "không quầng sáng, không tia sáng, không chuyển sắc, kể cả cho hiệu ứng nhấn"). Va chạm, vận khí, nhấn, chuyển cảnh được dùng quầng màu quanh người, chớp trắng, tia lóe, vòng sáng, đốm sáng, chuyển sắc. Các dòng trên vẫn áp cho bản thân hình vẽ (nét, mảng màu, bóng). Mẫu: `thu-hieu-ung-dau`, bản phát sáng, thư viện `hf-dau.js`; chi tiết ở DESIGN mục 3.7.
- **Nhấn mạnh thông tin** (chủ kênh chốt 2026-11-05). Mỗi video có vài hiệu ứng nhấn thông tin nhẹ, lặp có luật, để kênh có đặc trưng, không để video trôi "basic":
  - Ví dụ: đổi nền bằng mực tràn ở khoảnh khắc "nhận ra" hay ở ranh ý lớn; chữ chốt phát sáng nhẹ; làm tối nhẹ phần còn lại để nổi vật đang nói; khoanh hay gạch chân bằng bút dạ.
  - Mức nhẹ: không chớp trắng, không khung đen trắng, không tia lửa, không vòng xung kích, không rung máy mạnh. Những thứ đó dành cho cảnh combat (DESIGN 3.7). Ở `thu-dac-trung` bản 4, bộ phát sáng đầy đủ dùng cho câu "BỊ PHẠT" bị chủ kênh chê "hơi lố".
  - Chi tiết ở DESIGN 3.8.
- Mọi thứ render tất định.

- Độ run giữ nhẹ.
- Làm mờ tiền cảnh chỉ dùng tiết kiệm.
- Xu: bước hiện tại gồm đổi màu mực, thêm nét run, và mặt tối phẳng (đã có trong `phongcach\xu\xu-character.js`, giao ngày 2026-09-30). Nét đậm nhạt là bước sau, cần viết lại xu-character.js, chưa làm khi chưa được giao. Không đổi dáng chibi của Xu.

## 5. Khuôn prompt vật liệu

- Tả gọn từng vật. Đồ có phiên bản hiện đại thì gắn năm hoặc chữ "antique".
- **Sticker**: các vật đặt rời nhau, không chạm nhau, trên nền một màu có sắc không trùng bất kỳ vật nào trên tờ.
  - Không dùng nền trắng, vì công cụ tách nền không bắt được lỗ thật bên trong vật.
  - Không dùng nền xanh dương hay xanh đêm, vì trùng màu mặt tối chàm của vật, sẽ bị khoét.
  - Không bóng đổ, không cảnh nền.
- **Tên thương hiệu**: chỉ gọi tên khi vật ngoài đời thật mang logo đó và câu chuyện cần. Khi xem ảnh phải kiểm chính tả; sai thì sinh lại.
- Không dùng những chữ gọi ra chữ viết như label, sign, headline, poster, title. Chữ thông tin do HF viết (mục 3).
- Kính hay vật trong suốt thì tô màu xám sương, nếu không sẽ bị khoét thủng.
- **Chuỗi style**: cuối prompt là khối style chép **nguyên văn** từ file gốc.
  - Tờ nhân vật dùng **`phongcach\style-nhan-vat.txt`** (S3, chibi biểu cảm). Tờ nhân vật mới kèm ảnh neo `phongcach\neo\nhan-vat.png`, chỉ để lấy nét, tỉ lệ và cách biểu cảm, không chép người (câu dặn có sẵn trong skill minh-y). Tờ tư thế bổ sung kèm tờ gốc của chính nhân vật đó.
  - Tờ đồ vật, đạo cụ dùng **`phongcach\style-do-vat.txt`**.
  - Ảnh nền nơi chốn dùng **`phongcach\style-nen.txt`**.
  - (Quy trình Veo cũ dùng `style-sticker.txt` và `style-veo.txt`, nay đã cất.)
  - Bản `assets\style-*.txt` trong từng dự án chỉ là bản chép; nếu khác bản gốc thì dừng lại báo chủ kênh.
- **Ảnh nền nơi chốn**: vẽ kín mép như cảnh Veo, nhưng chừa khoảng trống cho chữ thông tin của HF.
  - Biển hiệu chỉ giữ cái định danh nơi chốn, nếu ngoài đời có. Ghi rõ trong prompt để ảnh không tự thêm biển hiệu khác.
  - Không người, nếu người sẽ là sticker đặt lên.
- Tỷ lệ khung chủ kênh chọn trên giao diện, không ghi trong prompt. Ảnh nền nhắm 4K.
- Mỗi tờ gom những vật cùng cỡ. Nhân vật làm tờ riêng, 3–5 tư thế.
- **Ảnh tham chiếu: tác nhân tự quyết, không hỏi chủ kênh.**
  - **Dòng Tham chiếu**: mỗi tờ, mỗi nền trong VAT-LIEU có một dòng, ghi kèm ảnh nào (tên tờ đã sinh), dùng cho vật nào, vì sao. Nếu không cần thì ghi "không cần" kèm lý do.
  - **Khi nào cần**: cùng một người, vật hay nơi xuất hiện ở hai tờ trở lên (vd một nhân vật ở hai bộ trang phục, hộp trong tay người): tờ sau kèm ảnh tờ đã sinh, và xếp tờ đó sinh trước.
  - **Số ảnh**: mỗi tờ kèm ít ảnh nhất mà đủ, thường 1, tối đa 3 (tạm).
  - **Thứ tự sinh**: VAT-LIEU ghi rõ tờ và nền nào sinh trước.
  - Quy trình Veo cũ chọn tham chiếu từ cảnh Veo theo `assets\veo-prompt.txt` (chọn cảnh, nền cạnh khối Veo, thiếu prompt Veo); bản đó cất ở `phongcach\ban-luu\2026-10-30_don-mach\truoc\CLAUDE.md`, mục 5.
- Chuỗi style có câu tả nhân vật chibi nên đồ vật có thể mọc mặt; chủ kênh hiện chấp nhận. Nếu video nào cần đồ vật trơn thì thêm: `plain inanimate objects with no faces, no eyes and no limbs`.
- Nhiều vật trên cùng tờ vẫn có thể lệch độ kỹ. Nhắc chủ kênh canh bằng mắt.

## 6. Công cụ

**Mọi công cụ chạy qua lệnh chung `C:\hyperframestest\cong-cu\hf.cmd`**, đứng trong thư mục dự án (từ 2026-10-30): `hf may`, `hf moc`, `hf tulieu`, `hf bao`, `hf tachnen`, `hf check`, `hf snap`, `hf preview`, `hf render`. Không tự gõ `npx`, không tự đặt biến môi trường, không chép script né lỗi vào dự án. Mọi chỗ riêng của máy (trình duyệt, bản HyperFrames, DLL bị Windows chặn, thời hạn chờ, không gọi Gemini, mã hóa chữ) nằm trong `hf.py`; giải thích và số đo ở `cong-cu\HUONG-DAN-HF.md`. Gặp lỗi máy mới thì vá ở đó theo HUONG-DAN-HF, không ghi vào sổ tay.

- **whisper** (`tools\whisper`): faster-whisper large-v3, kèm khopdong.py để khớp từng từ với dòng kịch bản. Gọi bằng `hf moc`; cách khớp, cách vá khi whisper bịa câu ở HUONG-DAN.md. Không dùng `hyperframes transcribe`: lệnh này chỉ dò ba chỗ cố định nên không thấy whisper, và máy không có công cụ biên dịch whisper-cpp.
- **tach-nen** (`tools\tach-nen`): rembg với BiRefNet, chạy CPU, khoảng 25–35 giây mỗi vật. Gọi bằng `hf tachnen`; thêm `--vien 10` nếu muốn viền trắng. Tờ nhiều vật tự cắt thành `tên-01.png`, `tên-02.png`… Mỗi lần chạy xuất `_xem-nhanh.png` (sticker trên nền caro và nền tối) kèm danh sách sticker nghi hỏng.
- **cong-cu** (`C:\hyperframestest\cong-cu`): `lay-tu-lieu.py` (`hf tulieu`) tìm và tải tư liệu thật loại A, B; `chup-bao.py` (`hf bao`) chụp bài báo loại C. Key ở `cong-cu\.env`. Cách dùng trong `cong-cu\HUONG-DAN.md`. Chỉ dùng cho video được phép dùng tư liệu thật (mục 10). HUONG-DAN có quy trình trọn từ "Thấy thật" của minh-y tới chọn, chuyển mã, dựng thẻ báo (`cong-cu\dung\hf-dung.js`), gắn màu footage và ghi công.
- **Render dùng `hyperframes@0.8.160`**, không dùng bản ghim của dự án; `check`, `snap`, `preview` vẫn dùng bản ghim (chủ kênh chốt 2026-10-28). `hf render` tự làm việc này. Lý do: từ khoảng 0.8.169 render chậm gấp đôi khi trang có `mix-blend-mode` (lớp hạt giấy `.hat` của kênh); số đo và log ở `phongcach\ban-luu\2026-10-28_render-0.8.160\`.
- **phan-tich** (`C:\hyperframestest\phan-tich\kenh-mau`): công cụ đo giọng (`caodo.py`, `phantich.py`, `nhom.py`, `chamthu.py`, chạy bằng venv whisper) dùng để chấm một bản giọng mới so với giọng mẫu; `tolien.py` (venv tach-nen, cần Pillow) ghép khung 2 giây một tấm kèm lời thành tờ liên hoàn để xem cách dựng của một video. Cách chạy trong `phan-tich\BAN-GIAO-2026-10-13.md` mục 4.

## 7. Cấu trúc một thư mục dự án

- `index.html`: chính là video.
- `assets\vat-lieu-goc`: ảnh gốc từ Nano Banana Pro.
- `assets\vat-lieu`: sticker đã tách nền.
- `assets\nen`: ảnh nền.
- `assets\tulieu`: tư liệu thật (chỉ video được phép, mục 10).
- (Quy trình Veo cũ còn `assets\veo-prompt.txt`, `assets\veo`, `assets\veo-clip`.)
- `snapshots`: ảnh Claude Code chụp để tự xem.
- `renders`: file MP4.

## 8. Luật quyền

- **Không xóa file nào**, kể cả file thử do chính Claude Code tạo ra, kể cả lệnh dọn dẹp hay ghi đè cả thư mục. Chạy lại công cụ thì ghi đè file cùng tên, không xóa trước. Cần dọn thì liệt kê đường dẫn để chủ kênh tự xóa.
- **Không cài đặt gì** khi chưa hỏi (gói npm, gói Python, công cụ, extension), mỗi lần cài hỏi một lần.
- **Không dùng dịch vụ tính tiền** (API Gemini, Imagen, Nano Banana Pro, Veo, hay bất cứ API trả phí nào), kể cả khi đã có key (máy có `GEMINI_API_KEY`; gói Gemini Ultra của chủ kênh không bao phần API trả theo lượt). Ảnh và clip do chủ kênh tự làm trên giao diện; Claude Code chỉ sắp xếp và dựng.
- **Không đụng ra ngoài `C:\hyperframestest`** khi chưa hỏi. Đọc skill ở `%USERPROFILE%\.claude\skills\` thì được; ghi vào đó thì không.
- **Không đụng cài đặt bảo mật của Windows** (Smart App Control, Application Control, Defender). Gặp file bị chặn thì báo chủ kênh, vá theo `cong-cu\HUONG-DAN-HF.md`.
- Lệnh chạy lặp lại như render, preview, check, snapshot, tách nền thì chạy bình thường.
- Đã chạy `hf preview --background` thì để nguyên, **không tự dừng** khi chủ kênh chưa bảo (không `preview --stop`, không giết tiến trình). Cần khởi động lại thì hỏi trước.
- Không tự tắt tiến trình Chrome của chủ kênh.
- Chủ kênh làm việc ở chế độ Accept edits (Claude Code) hay Request Review (Antigravity), không dùng Bypass hay Turbo.

## 9. Cách làm việc

- Mọi thứ định tự vẽ bằng code phải hiện ra kèm lý do để soát được.
- Với nét vẽ và cảm giác hình, tin mắt chủ kênh hơn tin số đo.
- Số nào còn tạm thì ghi là tạm. Không rút luật từ một video, không vá thêm luật sau mỗi lỗi; ghi quan sát vào nhật ký rồi để chủ kênh đánh giá sau nhiều video.
- Khi chủ kênh chốt một luật mới trong phiên, đề nghị ghi ngay vào file này hoặc DESIGN.md, đừng để nó chỉ nằm trong lịch sử trò chuyện.
- **Lỗi máy không phải luật.** Lỗi của công cụ, trình duyệt, Windows thì vá trong `hf.py` hay công cụ gốc và ghi vào `cong-cu\HUONG-DAN-HF.md`; không thêm vào sổ tay hay LUAT-GOC.
- **Gỡ lỗi tối đa 10 phút.** Quá 10 phút chưa ra hướng thì dừng, báo chủ kênh: lỗi gì, đã thử gì, còn hướng nào, mỗi hướng tốn bao lâu. Không đọc mã nguồn của HyperFrames hàng giờ mà không báo.
- **Ước giờ từ số đo, không đoán.** Báo tiến độ bằng số đo thật (khung đã chụp trên tổng, số truy vấn đã xong trên tổng, số sticker đã tách trên tổng). Ước sai thì nói ngay khi biết.
- **Cất bản trước khi đổi.** Trước một đợt đổi chuẩn nhìn hay quy trình, chụp trọn bộ đang dùng vào `phongcach\ban-luu\<ngày>_<tên-ngắn>\`.
  - Bộ chụp gồm: sổ tay, DESIGN gốc, các chuỗi style, Xu, và bộ file của dự án video gần nhất (DESIGN, VAT-LIEU, PHUONG-AN, STORYBOARD, index.html, file sinh hạt giấy).
  - Kèm README ghi bản đó nhìn như thế nào và cách dùng lại.
  - Sửa xong thì chụp thêm bản sau, kèm tài liệu bàn giao của đợt đổi.
  - Không sửa, không xóa file trong `ban-luu`.
  - Ghi từng thay đổi vào `phongcach\CHANGELOG.md`: đổi gì, từ gì sang gì, vì sao, ngày nào. Khi lấy lại một phần từ bản cũ, cũng ghi vào đó là đã lấy gì, từ bản nào.

## 10. Tư liệu thật và sound effect

**Video được phép:** chỉ video có tên trong `C:\hyperframestest\VIDEO-DUOC-PHEP.md`; mặc định là không (chủ kênh chốt 2026-10-13). Chủ kênh cho phép video nào thì thêm một dòng vào file đó, không sửa sổ tay. (Trước 2026-10-30 danh sách nằm ở đây; các dòng cũ đã chép nguyên sang file đó.)

Các luật dưới đây chuyển nguyên văn từ mục "Đang theo dõi" cũ ngày 2026-10-30 (đợt dọn mạch): chúng đã được chủ kênh chốt hoặc cho dùng tiếp ở mọi video được phép, không còn là phép thử.

- Cách đặt tư liệu thật (2026-10-13, phân tích kênh Lóng, `phan-tich\kenh-mau\BAO-CAO-FOOTAGE.md`): hình thật dùng để người xem nhận ra đúng nơi, thời, sự kiện, hoặc tin một con số, không để lấy không khí; đi thành chuỗi theo phần, phủ kín khung; bài báo hiện một lần, đứng suốt đoạn đọc số. Ghi vào minh-y (việc "Thấy thật", mục "Hình thật"). **Tư liệu thật chỉ dùng cho video chủ kênh cho phép từng video**, ghi tên video vào mục này; mặc định là không (chủ kênh chốt 2026-10-13). Số đo trên một video, là số tạm.
  - **Khi dựng** (video được phép), theo phân tích trên và lỗi của Domino's v4:
    - Footage và ảnh thật phủ kín khung, đi thành chuỗi 3–8 cú, mỗi cú 2–4 s, theo phần nội dung (mạch lịch sử, đời sống thì dày; mạch cơ chế, số liệu thì để HF làm, có thể không có ảnh thật nào).
    - Không đặt ảnh hay clip nhỏ lồng giữa sân khấu vẽ; khung nhỏ chỉ dùng để đặt nhiều vật cạnh nhau so sánh.
    - Thẻ bài báo gần kín bề ngang, chữ đọc được (v4 chỉ chiếm khoảng 1/3 khung, đọc không ra), bôi câu có số, hiện **một lần** và đứng suốt các dòng đọc số của bài đó; cần nhắc lại số thì dùng chữ to HF. Văn bản luật ghi "TRÍCH: <tên văn bản>".
    - Chữ đè lên footage chỉ là năm (chữ to) hoặc tiêu đề vài chữ. Thứ phi pháp, thứ bị phủ định: gạch chéo đỏ do code vẽ. Xu đứng ở góc trên footage và bài báo.
    - Không dùng footage chung chung thay cho thứ cụ thể (phố nước ngoài thay phố Việt Nam). Không có hình đúng thì vẽ.
    - **Gắn màu** (chủ kênh chốt 2026-10-26, áp cho mọi video sau): footage và ảnh thật chỉ gắn màu `muted-editorial` (chuỗi ở `cong-cu\HUONG-DAN.md`), không dùng nét vẽ Kuwahara. Ở `longvd-chonngay` v1, Kuwahara 0,75 gom ảnh thành mảng loang, chủ kênh chê "vỡ nát, mờ tịt"; v2 bỏ hẳn thì nét như ảnh gốc (so sánh ở `phongcach\ban-luu\2026-10-26_bo-kuwahara\so-sanh-kuwahara.jpg`). Không còn nét vẽ che nên ảnh nhỏ phóng kín khung sẽ lộ mềm: ghi kích thước ảnh vào gợi ý chọn.
  - **Ảnh thật làm nền sân khấu** (thử ở `giao-thong-thuy-dien` 18/10, chủ kênh cho dùng tiếp 20/10; chỉ ở video được phép; số tạm). Ảnh thật phủ kín làm phông, sticker và chữ HF đè lên, thay cho nền sinh bằng Nano Banana. **Dùng có chọn, không phải sân khấu nào cũng thế:**
    - **Dùng** khi sân khấu kể chuyện ở một nơi, một thời có thật mà người xem cần nhận ra đúng nó (phố Stockholm 1967, tòa Quốc hội Thụy Điển, quốc lộ Việt Nam), và có ảnh hợp: nhìn ngang tầm mắt hoặc dọc theo con đường, phía trước có mặt đất trống cho sticker đứng, tiền cảnh không bị người che, cạnh dài từ khoảng 900 px.
    - **Ảnh đúng mà không có chỗ cho sticker** (đám đông kín khung, nhìn từ trên cao, ảnh sự kiện, ảnh nhỏ): dùng phủ kín như một cú "Thấy thật", nhân vật vẽ cùng lắm đứng ở góc.
    - **Không dùng** cho mạch cơ chế, số liệu, giải thích (nền giấy và đồ họa HF); cho chuyện giả định, chuyện cá nhân, ví von (vẽ); cho nơi chung chung không cần nhận ra (nền vẽ hoặc nền giấy). Không lấy ảnh nước ngoài thay cho nơi ở Việt Nam; không có ảnh đúng thì vẽ.
    - **Ảnh phải nói được đúng ý của câu.** Câu nêu một điều nhìn thấy được (đi bên phải, đông, vắng, mới, hỏng) thì ảnh phải cho thấy rõ điều đó, thêm mũi tên hay vạch code chỉ vào; ảnh đúng nơi mà không rõ ý thì tìm ảnh khác. Ví dụ: Long chê ảnh ngã tư Gò Vấp ở câu "đi bên phải như Việt Nam mình", thay bằng ảnh Quốc lộ 1A nhìn dọc đường, có mũi tên chiều chạy hai làn.
    - Mỗi chỗ dùng ảnh làm nền có phương án vẽ dự phòng trong VAT-LIEU. Ở `giao-thong-thuy-dien` ảnh thật (làm nền và phủ kín) chiếm khoảng 40% thời lượng, dồn ở mạch lịch sử Thụy Điển và mạch đời sống Việt Nam; mạch cơ chế (nỗi sợ, bù trừ rủi ro) không có ảnh thật nào.
    - Khi dựng: gắn màu như footage (`muted-editorial`, không Kuwahara; ảnh đen trắng giữ đen trắng), máy quay trượt chậm, sticker có bóng tiếp đất phẳng màu chàm, ghi công dưới ảnh. Xu không đứng trên ảnh làm nền; Xu chỉ đứng góc trên ảnh phủ kín và thẻ báo. Cách lên kế hoạch ở skill minh-y (mục "Hình thật"), cách dựng ở `cong-cu\HUONG-DAN.md` (mục "Dựng").
  - Hai video mẫu là hai kênh khác nhau: Lóng (xổ số) và Vui Vẻ (nói). Kênh Vui Vẻ dùng ảnh thật làm mờ làm phông cho nhân vật vẽ; kênh mình đã thử ở `giao-thong-thuy-dien` theo cách riêng (không làm mờ, gắn màu `muted-editorial`), xem mục "Ảnh thật làm nền sân khấu" ở trên.
- Gốc của luật tư liệu thật (ba loại A, B, C và danh sách cấm vẫn áp cho mọi video được phép):
  - Tư liệu thật cho video w1d4 (Domino's), chủ kênh chốt 2026-10-09, chỉ trong phạm vi video này. Ba loại: A footage và ảnh chung (Pexels, Pixabay, Coverr, Mixkit; NASA, NARA, Library of Congress khi file ghi rõ phạm vi công cộng); B ảnh tĩnh đúng đối tượng từ Wikimedia Commons hoặc kho công, đọc giấy phép từng file, CC BY và CC BY-SA phải ghi công; C ảnh chụp bài báo chỉ từ danh sách link đã kiểm, vệt bôi và dòng "NGUỒN" do HF vẽ. Cấm: clip truyền hình, quảng cáo cũ, video của báo hay của hãng, video YouTube hay Facebook; ảnh từ Google Images hay trang không ghi giấy phép (Facebook tự quét bản quyền video). Mọi file ghi vào `assets\tulieu\NGUON.md`; chỉ file chủ kênh đã chọn mới vào `assets\tulieu\da-chon\`. Công cụ tìm tư liệu mượn adapter của OpenMontage (AGPL-3.0, clone ở `_ngoai\OpenMontage` chỉ để đọc và gọi, không phát tán lại mã đã sửa). Không dùng Archive.org (ngoài danh sách nguồn, kho Prelinger nhiều quảng cáo cũ). Mẫu dựng (chủ kênh chọn 2026-10-10, file mẫu `domino-30-phut\mau\mau-the-bao.html`, `mau\mau-footage.html`): thẻ bài báo trên nền giấy + hạt giấy (không nền mờ); footage chỉnh màu `muted-editorial` mức 1, tắt tối viền, thêm nét vẽ Kuwahara 0,75 (bản v2b; nét vẽ Kuwahara bỏ từ 2026-10-26, xem "Gắn màu" dưới đây); Xu được đứng cạnh footage. Chưa phải luật chung; đánh giá sau video này.
- **Sound effect (phép thử ở `duong-seoul`, chủ kênh cho thử 2026-10-20; chưa phải luật, số tạm).** Trước video này kênh chỉ có giọng đọc.
  - Nguồn: Openverse (âm lấy từ Freesound và kho khác, chỉ nhận giấy phép CC0 và CC BY; không cần tài khoản, không tính tiền; mỗi ngày tối đa khoảng 200 lượt tìm) và thư viện 19 file có sẵn trong skill media-use của HyperFrames. Không sinh âm bằng AI, không lấy âm từ phim, TV, YouTube.
  - Chủ kênh nghe và chọn trước, Claude Code mới đặt vào video. Ứng viên để ở `assets\sfx\ung-vien\`, file chọn chép sang `assets\sfx\da-chon\`; giấy phép và ghi công (CC BY phải ghi) ở `assets\sfx\NGUON.md`.
  - Khi dựng: âm nằm dưới giọng đọc (âm lượng khoảng 0,35, tạm), khớp đúng nhịp chuyển động. Chỉ đặt ở chỗ có hành động nghe được (còi, búa khoan, bê tông vỡ, đám đông, chuyển cảnh, chữ to bật ra), không rải đều mọi dòng.
  - Đánh giá sau video này: có làm video sống hơn không, có lấn giọng đọc không, số chỗ đặt vừa hay dày.

## 11. Đang theo dõi (chưa chốt)

- Bút mực, vật liệu ảnh, đồ vật có mặt hay không có mặt: đánh giá tổng thể sau vài video.
- Chuẩn Veo mới trong HF (2026-09-30): lớp màu cảnh, bóng phẳng, mặt tối cho vật code và Xu, thứ bậc nét, logo thật trên sticker, cách nối cắt Veo–HF (DESIGN mục 9, đang thử). Đánh giá bằng phép cắt trên video đầu tiên làm theo chuẩn này (gợi ý: Fremont và NUMMI), rồi xem lại sau vài video. Bảng màu hằng số vẫn là số đo từ clip Veo cũ, cần đo lại trên clip Veo mới.
- HF thuần và ngôn ngữ riêng của HF (2026-09-30, DESIGN 5.4): tỉ lệ khối thuần và khối có vật liệu, vốn hình, bước lưới và nhịp so le. Đánh giá sau vài video.
- Quan sát (video Công nhân tệ, 2026-09-30): HF thuần dùng ký hiệu thay người và vật (chấm đen = công nhân, hộp chữ nhật = xe) bị chủ kênh chê là hiểu được nhưng biểu diễn thông tin kém, không hiệu quả. Khối 1 dựng xong thì bỏ, chuyển sang phương án có vật liệu (bản đồ → nhà máy → xưởng). Chưa phải luật; xem lại sau vài video cùng với mục HF thuần ở trên.
- (Quy trình Veo cũ, đã cất 2026-10-10) Bỏ CapCut, đặt clip Veo thẳng vào HyperFrames (2026-10-02, Chặng 6): chưa thử trên video thật; video đầu làm theo cách này là Häagen-Dazs. Theo dõi: clip ngắn hơn khung có hay gặp không, giữ hình cuối có lộ không, và chỗ cắt Veo↔HF nhìn có liền không.
- Giọng đọc (2026-10-11 đến 13; chủ kênh tạo giọng trong Google AI Studio, Gemini TTS; chủ kênh thấy đã ổn). Hồ sơ giọng (Audio Profile, Scene, Sample Context) ở `phan-tich\kenh-mau\KICH-BAN-THU-v2.md`, số đo giọng mẫu ở `BAO-CAO-GIONG.md`. Quan sát qua bốn lần thử (số tạm):
  - nhãn ngoặc vuông tại từng câu ăn hơn quy tắc chung trong Sample Context;
  - nhãn cảm xúc (`[laughing at himself]`, `[grinning]`) đẩy giọng lên được, nhãn ra lệnh cao độ (`[higher]`) thì không;
  - dấu chấm làm máy hạ giọng chốt câu và nghỉ 0,3–0,4 s, chỗ muốn nói liền thì dùng dấu phẩy;
  - câu con số vẫn chưa chậm đủ;
  - không viết "steady pace" trong Sample Context;
  - thẻ `<short pause>` là của Gemini Flash TTS, không dùng trong AI Studio.

  Chấm một bản giọng mới bằng công cụ `phan-tich` (mục 6).
- Văn nói cho kịch bản (2026-10-13, bản nháp, chưa chốt nơi đặt). So sánh w1d1–w1d4 với Lóng và Vui Vẻ ở `phan-tich\kenh-minh\SO-SANH-VAN.md`, mục 6 là 10 luật. Kịch bản kênh mình đúng nội dung nhưng viết như văn đọc bằng mắt:
  - người kể vắng mặt;
  - thiếu "thì / là / nhưng mà / thực ra / ví dụ";
  - hài kể gián tiếp;
  - không có biển chỉ đường;
  - thành ngữ giật tít;
  - kết bằng "Nên lần tới…".

  Viết lại là một bước riêng trước nhip-hf (nhip-hf không được sửa chữ), chỉ làm khi chủ kênh nhờ. Bài mẫu mới nhất: `phan-tich\kenh-minh\gruen-viet-lai-3.txt`. Bàn giao cả phiên: `phan-tich\BAN-GIAO-2026-10-13.md`.
- Số tạm của nhip-doan: sàn khối 10 giây, ngưỡng 30 giây, 1–3 khối mỗi mạch, dải mật độ Veo 10–13 cảnh mỗi phút. Video Coca ra 14,0 cảnh mỗi phút, vượt dải.

## Nhật ký thay đổi

- 2026-09-27 — Tạo sổ tay, gom từ hồ sơ bàn giao phiên 25–26/09 (dây chuyền, năm chặng, luật chia việc vẽ, khuôn vật liệu, công cụ, luật quyền).
- 2026-09-27 — Thêm "Chặng 0 — Tạo dự án" trước chặng 1, ghi theo cách tạo dự án mcdonalds (init bằng `npx.cmd`, mẫu Blank, dừng studio bằng Ctrl+C, chuẩn bị assets, mở Claude Code). Tên file sổ tay được sửa từ `calude.md` thành `CLAUDE.md`.
- 2026-09-29 — Tạo bản gốc chuỗi style tại `phongcach\style.txt` (chép từ dự án hop-nhua-tupperware, trùng từng byte với bản của coca-5xu và mcdonalds). Điền đường dẫn này vào mục 5 thay chỗ trống, thêm vào mục 0 và Chặng 0.
- 2026-09-29 — Chủ kênh chọn bản `DESIGN.md` ngày 27/09 (bản của video mcdonalds, 48,7 KB) làm bản gốc. Chép đè vào `phongcach\DESIGN.md`; bản gốc cũ ngày 24/09 cất ở `phongcach\DESIGN-cu-2026-09-24.md`. Dòng đầu của bản gốc mới vẫn ghi "Bản chép cho video McDonald's", chưa sửa.
- 2026-09-30 — Chuẩn nhìn mới theo cảnh Veo. Chuỗi style tách thành hai file gốc (`style-veo.txt`, `style-sticker.txt`); `style.txt` thôi dùng. Xu có bản gốc ở `phongcach\xu\`, thêm mặt tối phẳng. Sửa theo: mục 0, Chặng 0, mục 3 (ảnh nền nơi chốn, chữ hai vai), 4, 5, 9 (cất bản trước khi đổi), 10. Dòng đầu DESIGN gốc đã sửa. Chi tiết: `phongcach\CHANGELOG.md`. Bản trước: `phongcach\ban-luu\2026-09-29_truoc-chuan-veo-moi\`.
- 2026-09-30 — HF tự chủ và đầu vào prompt Veo. Mục 3 thêm câu hỏi 1 (khối có cần vật liệu không; không cần thì HF thuần). Mục 1, Chặng 0 (`veo-prompt.txt`, `assets\veo\`), Chặng 2, 3, 4, mục 5 (Claude Code tự quyết ảnh tham chiếu, không hỏi), 7, 10 sửa theo. DESIGN thêm 5.4 "Sân khấu HF thuần". Chi tiết: `phongcach\CHANGELOG.md`. Bản trước: `phongcach\ban-luu\2026-09-30_chuan-veo-moi\`.
- 2026-09-30 — Mục 10 thêm quan sát từ video Công nhân tệ: HF thuần dùng ký hiệu thay người và vật bị chê (chủ kênh đồng ý ghi, chưa thành luật).
- 2026-10-02 — Bỏ ghép CapCut. Clip Veo đặt vào `assets\veo-clip\`, Claude Code đặt thẳng vào `index.html` theo mốc từng dòng, tắt tiếng, render ra video hoàn chỉnh (thêm Chặng 6). Mục 8 thêm luật không dùng dịch vụ tính tiền. Sửa theo: mục 1, Chặng 0, mục 2, 7, 8, 10. Chi tiết: `phongcach\CHANGELOG.md`. Bản trước và sau: `phongcach\ban-luu\2026-10-02_bo-capcut\`.
- 2026-10-09 — Mục 10 thêm quyết định cho video w1d4: được dùng tư liệu thật (footage, ảnh tư liệu, ảnh chụp bài báo) theo ba loại A/B/C và danh sách cấm. Chỉ áp cho w1d4, chưa thành luật chung.
- 2026-10-09 — Mục 6 thêm `cong-cu` (lay-tu-lieu.py, chup-bao.py). Cài gói Python `playwright` (chủ kênh duyệt), clone OpenMontage vào `_ngoai\OpenMontage` để mượn adapter.
- 2026-10-10 — Đối sách full HyperFrames: mọi dòng là HF, Google Flow chỉ sinh nguyên liệu, không còn clip Veo. Mục 0, 1, Chặng 0, mục 5, 7, 10 sửa theo; Chặng 2–6 ghi khung tạm, chờ viết lại. `style-veo.txt`, `style-sticker.txt` dời vào bản lưu (không xóa). Chi tiết: `phongcach\CHANGELOG.md`. Bản trước và sau: `phongcach\ban-luu\2026-10-10_full-hf\`.
- 2026-10-13 — Cách đặt tư liệu thật rút từ kênh Lóng ghi vào skill minh-y (việc "Thấy thật", mục "Hình thật", luật bài báo hiện một lần); tư liệu thật chỉ dùng cho video chủ kênh cho phép (mục 10). Mục 0 thêm bản nguồn skill minh-y ở `phongcach\skills\`. Chi tiết: `phongcach\CHANGELOG.md`. Bản trước và sau: `phongcach\ban-luu\2026-10-13_footage-minh-y\`.
- 2026-10-13 — Chủ kênh đã tải minh-y mới lên claude.ai. Mục 10 thêm luật khi dựng tư liệu thật, quan sát giọng đọc AI Studio, bản nháp văn nói cho kịch bản. Mục 6 thêm công cụ `phan-tich` và "Chỗ riêng của máy này" (Chrome, snapshot không gọi Gemini, không tự dừng preview; chép từ bộ nhớ phiên vì phiên mở ở thư mục dự án không đọc được bộ nhớ thư mục gốc). Bàn giao: `phan-tich\BAN-GIAO-2026-10-13.md`.
- 2026-10-13 — Mục 10 ghi video `trungtamthuongmai` được dùng tư liệu thật (chủ kênh cho phép khi tạo dự án).
- 2026-10-13 — Mục 6: `cong-cu` trỏ tới quy trình trọn trong `cong-cu\HUONG-DAN.md` (tìm, chọn, chuyển mã, dựng, ghi công) và thư viện dựng `cong-cu\dung\`. Mục 10: sửa đường dẫn file mẫu (đã dời vào `domino-30-phut\mau\`).
- 2026-10-13 — Skill minh-y (bản nguồn) viết sẵn `truy-van.txt` và `bao.txt` cho công cụ tìm tư liệu khi video được phép; `cong-cu\HUONG-DAN.md` bước 2 sửa theo. Chờ chủ kênh tải lên claude.ai. Chi tiết: `phongcach\CHANGELOG.md`. Bản trước và sau: `phongcach\ban-luu\2026-10-13b_minh-y-dau-vao-cong-cu\`.
- 2026-10-14 — Mục 10 ghi video `starbuck` được dùng tư liệu thật (chủ kênh cho phép khi tạo dự án).
- 2026-10-15 — Mục 10 ghi video `nitendo-vs-sony` được dùng tư liệu thật (chủ kênh cho phép sau khi VAT-LIEU bản đầu đã viết).
- 2026-10-17 — Mục 10 ghi video `tien-phat-trong-tre` được dùng tư liệu thật (chủ kênh cho phép khi tạo dự án).
- 2026-10-18 — Mục 10 ghi video `giao-thong-thuy-dien` được dùng tư liệu thật (chủ kênh cho phép khi tạo dự án), kèm phép thử ảnh thật đặt thẳng làm nền sân khấu.
- 2026-10-20 — Mục 3: thêm điều khoản chủ quyền cho bản đồ có Việt Nam hay Biển Đông (Hoàng Sa, Trường Sa thuộc Việt Nam; không "South China Sea", không đường lưỡi bò; ảnh Wikimedia không đạt thì dựng bằng code). Chủ kênh chốt. Bản trước và sau: `phongcach\ban-luu\2026-10-20c_chu-quyen-ban-do\`.
- 2026-10-20 — Mục 3: luật bản đồ đổi thành chọn linh hoạt: hiệu ứng khó thì dựng bằng code từ dữ liệu địa lý thật, chỉ đặt nhãn, mũi tên thì dùng ảnh bản đồ Wikimedia; không vẽ tay đường viền, không sinh bản đồ bằng Nano Banana (chủ kênh chốt). Gỡ chỗ lệch với skill minh-y. Chi tiết: `phongcach\CHANGELOG.md`. Bản trước và sau: `phongcach\ban-luu\2026-10-20b_ban-do\`.
- 2026-10-20 — Mục 10: phép thử "ảnh thật làm nền sân khấu" thành cách làm cho mọi video được phép dùng tư liệu thật, có điều kiện khi nào làm nền, khi nào phủ kín, khi nào không dùng (chủ kênh yêu cầu sau `giao-thong-thuy-dien` v3). Skill minh-y (bản nguồn) và `cong-cu\HUONG-DAN.md` sửa theo. Chi tiết: `phongcach\CHANGELOG.md`. Bản trước và sau: `phongcach\ban-luu\2026-10-20_anh-that-lam-nen\`.
- 2026-10-20 — Mục 10 ghi video `duong-seoul` được dùng tư liệu thật (chủ kênh cho phép khi tạo dự án).
- 2026-10-20 — Mục 10 thêm phép thử sound effect cho video `duong-seoul` (Openverse CC0/CC BY và thư viện có sẵn của media-use; chủ kênh nghe chọn trước khi đặt; âm dưới giọng đọc). Chủ kênh cho thử, chưa phải luật.
- 2026-10-20 — Mục 10 ghi video `duong-seoul-p2` được dùng tư liệu thật (chủ kênh cho phép khi tạo dự án).
- 2026-10-21 — Mục 10 ghi video `ngay-dep-test-anti` được dùng tư liệu thật (chủ kênh cho phép trong phiên, duyệt ghi sổ tay).
- 2026-10-22 — Mục 10 ghi video `longvd-chonngay` được dùng tư liệu thật (chủ kênh cho phép khi giao dự án; bản đăng YouTube, dài khoảng 14 phút).
- 2026-10-24 — Viết lại Chặng 1–6 theo cách đã chạy ở năm video gần nhất (chủ kênh yêu cầu): mốc giây → minh-y viết VAT-LIEU (gồm cả phương án sân khấu và storyboard) → sinh ảnh, tìm tư liệu, sound effect song song → tách nền → dựng khối 1 → dựng cả video và render. VAT-LIEU thành sổ ghi của dự án, mỗi chặng thêm một mục có ngày. Bỏ phần đặt clip Veo và `veo-prompt.txt` khỏi các chặng. Mục 5 (ảnh tham chiếu theo prompt Veo) và câu cuối mục 1 chưa sửa. Chi tiết: `phongcach\CHANGELOG.md`. Bản trước và sau: `phongcach\ban-luu\2026-10-24_chang-full-hf\`.
- 2026-10-26 — Footage và ảnh thật chỉ gắn màu `muted-editorial`, bỏ nét vẽ Kuwahara 0,75 của bản v2b, áp cho mọi video sau (chủ kênh chốt sau `longvd-chonngay` v1, ảnh bị loang như vỡ). Sửa Chặng 6, mục 10 (thêm "Gắn màu", sửa chỗ nhắc v2b), `cong-cu\HUONG-DAN.md` (chuỗi gắn màu, ghi chú render). Chi tiết: `phongcach\CHANGELOG.md`. Bản trước và sau: `phongcach\ban-luu\2026-10-26_bo-kuwahara\`.
- 2026-10-26 — `antigravity\LUAT-GOC.md` sửa cho khớp luật bỏ Kuwahara (mục 3 thêm "Gắn màu", mục 4 sửa ghi chú render), chủ kênh bảo. Bản trước và sau: cùng thư mục `2026-10-26_bo-kuwahara`.
- 2026-10-27 — Mục 10 ghi video `gia-nha-tokyo` được dùng tư liệu thật (chủ kênh cho phép khi tạo dự án).
- 2026-10-28 — Mục 10 ghi video `bac-ho-ra-di-tim-duong-cuu-nuoc` được dùng tư liệu thật (chủ kênh cho phép khi giao dự án).
- 2026-10-28 — Mục 4: bỏ luật "không quầng sáng, không tia sáng, không chuyển sắc, kể cả cho hiệu ứng nhấn". Hiệu ứng được phát sáng; nét, mảng màu và bóng của hình vẽ giữ như cũ. Chủ kênh chốt sau khi so hai bản cảnh đấu ở `thu-hieu-ung-dau` ("bản phát sáng đẹp hơn rõ"). DESIGN gốc sửa theo (0, 1.3, 1.4, 2.2, thêm 3.7, mục 9). Chi tiết: `phongcach\CHANGELOG.md`. Bản trước và sau: `phongcach\ban-luu\2026-10-28b_mo-hieu-ung-phat-sang\`.
- 2026-10-28 — `antigravity\LUAT-GOC.md` (mục 3) và `antigravity\BAN-GIAO-3D.md` (mục 5) sửa cho khớp luật hiệu ứng phát sáng, chủ kênh bảo. Bản trước và sau: cùng thư mục `2026-10-28b_mo-hieu-ung-phat-sang`.
- 2026-10-28 — Render bằng `hyperframes@0.8.160` thay cho bản ghim của dự án (mục 6, Chặng 6), chủ kênh chốt sau khi đo: bản ghim 0.8.210 mất 97,5 phút cho video 3 phút, bản 0.8.160 mất 10 phút, hình giống nhau. `antigravity\LUAT-GOC.md` mục 4 sửa theo. Chi tiết: `phongcach\CHANGELOG.md`. Bản trước và sau: `phongcach\ban-luu\2026-10-28_render-0.8.160\`.
- 2026-10-29 — Mục 10 ghi video `bac-ho-v2` được dùng tư liệu thật (chủ kênh cho phép khi giao dự án, duyệt ghi sổ tay trong phiên Antigravity).
- 2026-10-30 — Dọn mạch (Long yêu cầu sau bac-ho-v2: "làm một video 3–4 phút mà mất hơn 4 tiếng"). Lệnh chung `cong-cu\hf.cmd` gom mọi chỗ riêng của máy (render không cần đóng Chrome nữa); `cong-cu\HUONG-DAN-HF.md` mới. Mục 0 (hf, VIDEO-DUOC-PHEP, LUAT-GOC, một xưởng), Chặng 0–6 (lệnh hf, `hf may` đầu phiên, ước giờ render từ số đo), mục 5 (ảnh tham chiếu bỏ phần dựa vào prompt Veo), mục 6 (trỏ sang hf), mục 8 (gom các điều trước chỉ nằm ở LUAT-GOC), mục 9 (lỗi máy vá vào hf; gỡ lỗi tối đa 10 phút; ước giờ từ số đo), mục 10–11 (luật tư liệu thật đã chốt tách khỏi "Đang theo dõi", nguyên văn). Danh sách video được phép chuyển sang `VIDEO-DUOC-PHEP.md`, thêm `uong-ruou`, `thu-phi-2028`. `antigravity\LUAT-GOC.md` viết lại thành lớp trỏ đường, không chép luật. Chín dự án ở `C:\hyperframestest - antigravity` chép về. Chi tiết: `phongcach\CHANGELOG.md`. Bản trước và sau: `phongcach\ban-luu\2026-10-30_don-mach\`.
- 2026-11-05 — Mục 4 thêm luật "Nhấn mạnh thông tin": mỗi video có vài hiệu ứng nhấn thông tin nhẹ làm đặc trưng; bộ phát sáng đầy đủ (chớp trắng, tia lửa, vòng xung kích, rung mạnh) chỉ cho cảnh combat. Chủ kênh chốt sau `thu-dac-trung` v2 ("hiệu ứng phát sáng hơi lố… cái kia dành cho các hiệu ứng combat"). DESIGN gốc thêm 3.8 và ghi chú phông đang thử ở 2.1. Chi tiết: `phongcach\CHANGELOG.md`. Bản trước và sau: `phongcach\ban-luu\2026-11-05_nhan-thong-tin\`.
- 2026-11-05 — Style nhân vật đổi từ S1 (đầu tròn 45%, mặt lì, nét đen dày như bút dạ) sang S3 "chibi biểu cảm": đầu một phần ba, có tai, mắt nâu có điểm sáng, má hồng gạch chéo, biểu cảm manga dễ thương kèm ký hiệu cảm xúc, nét mận sẫm, đổ bóng cel nhẹ, không viền sticker (tờ thử đầu có viền trắng, Long bảo bỏ). Long chốt: lấy style chibi của các tờ trong `mr-neu` "làm style gốc cho nhân vật sau này sinh ra". Thêm ảnh neo `phongcach\neo\nhan-vat.png` (tờ `ban-chibi-a` của mr-neu). Sửa mục 0, Chặng 2 (kho: không trộn nhân vật S1 với S3), mục 5. Đồ vật, nền, Xu chưa đổi. Chuỗi mới chưa sinh thử. Chi tiết: `phongcach\CHANGELOG.md`. Bản trước và sau: `phongcach\ban-luu\2026-11-05b_style-chibi-bieu-cam\`.
