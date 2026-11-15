# Nhật ký chuẩn nhìn HyperFrames

Ghi mọi thay đổi ở chuẩn nhìn và quy trình của HF so với bản gốc: đổi gì, từ gì sang gì, vì sao, ngày nào. Mới nhất ở trên. Mỗi đợt đổi có hai bản lưu trong `ban-luu/`: bản trước và bản sau.

Các thay đổi trước 2026-09-30 nằm rải ở nhật ký cuối `CLAUDE.md` và cuối `DESIGN.md` (bản chép của từng dự án). File này bắt đầu từ đợt chuẩn Veo mới.

---

## 2026-11-05 (đợt 2) · Style nhân vật S3 "chibi biểu cảm"

**Vì sao.**
- Đang thử S2 (học nét video mẫu "Kiến Thức Thú Vị") thì Long gửi bốn ảnh từ dự án `mr-neu` (kênh Mr. Nếu): một cảnh phòng trọ có cậu chibi vẫy tay, và ba tờ `ban-bieucam-c`, `ban-chibi-a`, `ban-chibi-b`.
- Long nói: "thôi như này đi… tham khảo cái style chibi mà biểu cảm cute. tôi muốn lấy style này làm style gốc cho nhân vật sau này sinh ra".
- Các tờ đó không có prompt lưu lại, nên chuỗi mới viết bằng cách tả lại từ ảnh.

**Đổi gì.**
| Chỗ | Từ (S1) | Sang (S3) |
|---|---|---|
| `style-nhan-vat.txt` | chibi đầu tròn 45%, không cổ, mắt bầu dục đen nhỏ, không mũi, không má hồng, mặt lì; viền đen dày đều như bút dạ; màu phẳng, cấm đổ bóng | chibi đầu một phần ba, cằm hơi vuông, có tai, cổ ngắn, thân trẻ con khoảng ba đầu; mắt nâu có điểm sáng, lông mày đậm, mũi chấm, miệng đổi theo cảm xúc, má hồng gạch chéo; biểu cảm manga làm quá (mắt cong, mắt sao, mắt trắng tròn, mắt xoắn, nước mắt) kèm ký hiệu (mồ hôi, lấp lánh, dấu giận, hơi phì, bóng đèn, mây mưa); nét mận sẫm gần đen, thon đầu; đổ bóng cel nhẹ; không viền sticker, ký hiệu vẽ sát người để tách nền không tách rời |
| `neo/nhan-vat.png` (mới) | không có | tờ `ban-chibi-a` của mr-neu, thu về 2752×1536. Skill minh-y đã có sẵn luật kèm ảnh neo nhân vật "nếu đã có" |
| Sổ tay mục 0, Chặng 2, mục 5 | S1; kho nhận vật liệu S1 | S3 cho nhân vật; kho: nhân vật chỉ nhận S3, không trộn nhân vật S1 với S3 trong một video; tờ nhân vật mới kèm ảnh neo |
| DESIGN gốc 3.5 | bảng đo từ Veo | thêm đoạn đầu về S3; ký hiệu thuộc về sticker; không viền |
| Skill minh-y (bản nguồn) | — | bước 3 thêm "biểu cảm gọi tên rõ, được làm quá", tối đa hai tư thế có ký hiệu lớn mỗi tờ; quy ước kho ghi S3 cho nhân vật |

**Chưa đổi:** `style-do-vat.txt`, `style-nen.txt` (S1), Xu, TAC-NHAN-FLOW. Chuỗi S2 ở `thu-style-s2/` thôi không sinh.

**Sinh thử lần một (cùng ngày):** hai tờ thử (bạn, bố chú rể) ra đúng dáng và biểu cảm, Long "ok rồi", nhưng bảo bỏ viền sticker trắng ("bỏ… hoặc thay bằng viền đen, hoặc không có viền luôn"). Đã chọn không viền: bỏ câu viền trắng, thêm vào Avoid "white sticker border, die-cut outline, outer glow"; bỏ chữ "sticker" ở câu mở đầu; ký hiệu cảm xúc vẽ sát người (công cụ tách nền chỉ gộp mảnh cách nhau dưới khoảng 1,2% cạnh ngắn). Ảnh neo gỡ viền trắng bằng cách loang nền từ mép ảnh (bản có viền cất ở `sau/neo-nhan-vat-co-vien-trang.png`).

**Chưa kiểm:** chuỗi sau khi bỏ viền chưa sinh lại. Tờ thử ở `thu-style-s3/DAN-VAO-FLOW.md`. Skill minh-y bản nguồn đã sửa, Long cần tải lên claude.ai.

**Bản lưu.** `ban-luu/2026-11-05b_style-chibi-bieu-cam/`.

---

## 2026-11-05 · Hiệu ứng nhấn mạnh thông tin

**Vì sao.** Sau `gio-cao-su` v4, Long thấy video "thiếu điểm nhấn, hơi basic" và nhờ nghiên cứu hiệu ứng làm đặc trưng. Phép thử `thu-dac-trung` có ba lượt:
- v1: loang nở sau vật, đèn sân khấu, quầng sáng;
- v2: đổi nền bằng mực tràn, cộng bộ phát sáng đầy đủ của `thu-hieu-ung-dau`.

Long xem v2: "hiệu ứng phát sáng hơi lố quá… cho nó nhẹ nhẹ… dạng cung cấp thông tin/nhấn mạnh thôi chứ cái kia dành cho các hiệu ứng combat rồi… ghi vào luật gốc là thêm mấy hiệu ứng nhấn mạnh thông tin… cho nó đặc trưng". Trước đó Long cũng bỏ loang nở ("không cần nữa, chỉ cần sau này đổi chất liệu nền") và thấy phông bộ 2 "tạm dùng được".

**Đổi gì.**
| Chỗ | Từ | Sang |
|---|---|---|
| Sổ tay mục 4 | chỉ có luật hiệu ứng được phát sáng (2026-10-28) | thêm "Nhấn mạnh thông tin": mỗi video có vài hiệu ứng nhấn thông tin mức nhẹ; chớp trắng, khung đen trắng, tia lửa, vòng xung kích, rung mạnh chỉ cho combat |
| DESIGN gốc 3.8 (mới) | không có | luật nhấn thông tin và các kiểu đã có: đổi nền mực tràn, chữ chốt phát sáng nhẹ, làm tối nhẹ phần còn lại, quầng mỏng bám dáng, khoanh bút dạ; bỏ loang nở |
| DESIGN gốc 2.1 | chỉ Be Vietnam Pro | ghi chú đang thử Baloo 2 / Itim / Mali (`phongcach/fonts/`), bảng phông chưa thay |

Style sticker S1, Xu, `hf-*.js` của các dự án không đổi. Chuỗi style thử S2 nằm riêng ở `phongcach/thu-style-s2/`, chưa phải chuẩn.

**Bản lưu.** `ban-luu/2026-11-05_nhan-thong-tin/`.

---

## 2026-10-30 · Dọn mạch: lệnh chung `hf`, một xưởng, luật một bản

**Vì sao.** Long: "làm một video 3–4 phút mà mất hơn 4 tiếng, bước nào cũng bị chặn". Claude Code soát nhật ký 8 phiên Antigravity, 35 phiên Claude Code và toàn bộ luật. Ở bac-ho-v2, khối 1 mất 4 tiếng, khoảng 2 tiếng là gỡ lỗi công cụ: 70 phút cho lỗi Chrome mã 21, 45 phút cho công cụ tìm tư liệu treo ở Wikimedia, 137 lần chạy hỏng vì sandbox của Antigravity. Sáu gốc rễ: (1) mẹo lách của máy nằm trong văn xuôi nên tác nhân phải tự gõ lại lệnh, 18 dự án mang bản chép của cùng một script né scipy; (2) một dòng luật máy đã cũ ("Windows chặn Chrome riêng của hyperframes") chính là nguồn lỗi mã 21; (3) hai bản sao của cả xưởng lệch nhau (`C:\hyperframestest - antigravity` có hai video được phép mà sổ tay gốc không có); (4) sandbox terminal của Antigravity chặn mạng và cổng nội bộ; (5) `npx` lên mạng kiểm phiên bản, bị chặn thì treo; (6) không có giới hạn thời gian gỡ lỗi (một phiên đọc mã nguồn HyperFrames 50 phút không báo).

**Đổi gì.**
| Chỗ | Từ | Sang |
|---|---|---|
| `cong-cu\hf.cmd`, `hf.py` (mới) | tác nhân tự gõ `npx`, đặt biến trình duyệt, nhớ `--describe false`, chép script né lỗi | một lệnh `hf may / moc / tulieu / bao / tachnen / check / snap / preview / render`; mọi chỗ riêng của máy nằm trong mã |
| render | `HYPERFRAMES_BROWSER_PATH=chrome.exe`, phải nhờ chủ kênh đóng Chrome, vẫn có lúc hỏng | bước thử trình duyệt dùng `chrome-headless-shell`, bước chụp vẫn dùng `chrome.exe` (`PRODUCER_HEADLESS_SHELL_PATH`); không cần đóng Chrome. Thời hạn chờ trang 180 s thay cho 45 s (trang có clip phim mất 95 s) |
| `cong-cu\HUONG-DAN-HF.md` (mới) | chỗ riêng của máy rải ở sổ tay mục 6 và LUAT-GOC mục 4 | một chỗ: `hf` làm gì, vì sao, số đo thời gian, chỗ chưa chữa được, cách vá lỗi máy mới |
| `tools\tach-nen\tachnen.py` | dừng khi Windows chặn scipy; mỗi dự án chép script bọc | tự né scipy khi nạp bị chặn |
| `cong-cu\lay-tu-lieu.py` | ảnh Wikimedia hẹp hơn 1920 px tải bản gốc, chờ tới 180 s mỗi file | luôn tải bản thu nhỏ, bỏ file treo sau 30 s |
| `VIDEO-DUOC-PHEP.md` (mới) | danh sách nằm trong sổ tay mục 10, sửa sổ tay mỗi video | file riêng; thêm `uong-ruou`, `thu-phi-2028` (trước chỉ ở sổ tay bản sao) |
| `CLAUDE.md` mục 0 | — | thêm `hf`, `VIDEO-DUOC-PHEP.md`, LUAT-GOC; "một xưởng, hai tác nhân" |
| `CLAUDE.md` Chặng 0–6 | lệnh thô (`whisper`, `lay-tu-lieu.py`, `check`, `snapshot --describe false`); "video 3 phút mất 10 phút" | lệnh `hf`; `hf may` đầu phiên; ước giờ render từ số đo khối 1 (ảnh tĩnh ~18 s video/phút, có clip phim ~8,5 s/phút); `check` cả video ~7 phút |
| `CLAUDE.md` mục 5 | ảnh tham chiếu chọn từ cảnh Veo theo `veo-prompt.txt` | tham chiếu là tờ đã sinh khi cùng người, vật hay nơi xuất hiện ở hai tờ trở lên (cách đang làm thật, vd bac-ho-v2) |
| `CLAUDE.md` mục 6 | "Chỗ riêng của máy này" (Chrome, Gemini, preview, render 0.8.160, DLL) | trỏ sang `hf` và HUONG-DAN-HF; giữ quyết định render 0.8.160 |
| `CLAUDE.md` mục 8 | — | thêm các điều trước chỉ nằm ở LUAT-GOC: không đụng ra ngoài xưởng, không đụng cài đặt bảo mật Windows, không tự dừng preview, không tắt Chrome của chủ kênh, chi tiết "không xóa", "không cài", "không API" |
| `CLAUDE.md` mục 9 | — | lỗi máy không phải luật (vá vào `hf`); gỡ lỗi tối đa 10 phút rồi báo; ước giờ từ số đo, báo tiến độ bằng số |
| `CLAUDE.md` mục 10, 11 | mục 10 "Đang theo dõi" chứa lẫn luật đã chốt (gắn màu, cách dựng tư liệu thật, ảnh thật làm nền) | mục 10 "Tư liệu thật và sound effect" (chuyển nguyên văn); mục 11 "Đang theo dõi" giữ các quan sát còn mở |
| `antigravity\LUAT-GOC.md` | chép luật cứng (mục 3) và chỗ riêng của máy (mục 4), hay lệch với sổ tay | chỉ trỏ đường đọc và nói chỗ riêng của Antigravity (sandbox, Downloads, bộ nhớ bị nén, đổi model) |
| `antigravity\README.md` | giữ khớp hai nơi bằng tay | thêm bước tắt sandbox, mở đúng workspace; bỏ việc giữ khớp |
| `antigravity\BAN-GIAO-3D.md` | mục 8 "hai bên làm song song" | mục 8 hết hiệu lực; gộp mục 9 "Nhật ký mở rộng 3D" (26/10) từ bản ở workspace cũ; chép `PROMPT-3D.md` |
| Dự án | `bac-ho-v2`, `thu-phi-2028`, `uong-ruou`, `thu-3d-chernobyl`, `-hoden`, `-netmuc`, `-quetthat`, `-thienthach-v2`, `-toba` chỉ ở `C:\hyperframestest - antigravity` | chép về `C:\hyperframestest` (chép, không di chuyển; bản cũ để Long tự xóa) |

**Không đổi.** Chuẩn nhìn (DESIGN, ba khối style, Xu), các chặng và nhịp dừng chờ duyệt, luật chia việc vẽ, luật tư liệu thật (chỉ dời chỗ), quyết định render bằng 0.8.160.

**Đã chạy thử (30/10).** `hf may` sạch; `hf render` ở `thu-hieu-ung-dau` khi Chrome của Long đang chạy ngầm (15 s video, 1,9 phút, chụp bằng Chrome 156); `hf check`, `hf snap`; `hf tachnen` một tờ 3 vật; `hf moc` trên bản chép giọng đọc bac-ho-ra-di (khớp 99%). `hf tulieu` chạy đúng nhưng không tải được ảnh nào: lúc thử, `upload.wikimedia.org` không trả byte nào cho máy này (chi tiết ở HUONG-DAN-HF, "Chỗ chưa chữa được").

**Bổ sung cùng tối (sau khi lưu bản `sau/`).** `cong-cu\lay-tu-lieu.py`: ảnh Wikimedia treo quá 30 s thì tự lấy lại qua `commons.wikimedia.org/w/thumb.php`. Lý do: lúc 22 giờ máy chủ ảnh im lặng với máy này, cả Chrome của Long cũng treo, còn trang Commons vẫn trả; một tiếng sau tự hết. Chạy thử: giả treo thì lấy được qua đường vòng; chạy thật thì một file treo được cứu, 3/3 ứng viên trong 41 s. `HUONG-DAN-HF.md` sửa theo (bỏ "phải tải tay" khỏi "Chỗ chưa chữa được"). Bản `sau/lay-tu-lieu.py` trong bản lưu là bản trước lần bổ sung này.

**Bản lưu.** `ban-luu/2026-10-30_don-mach/`: `truoc/` (sổ tay, LUAT-GOC, README, BAN-GIAO-3D, DESIGN gốc, style, Xu, công cụ trước khi sửa, sổ tay và LUAT-GOC của workspace cũ, bộ file bac-ho-v2), `sau/`.

---

## 2026-10-28 (đợt 2) · Mở hiệu ứng phát sáng

**Vì sao.** Long gửi một video mẫu có cảnh đấu võ (quầng màu quanh người, chớp trắng, vòng xung kích, vệt chém) và hỏi HyperFrames làm được không. Claude Code dựng thử cùng một cảnh đấu 7,5 s thành hai bản ở `thu-hieu-ung-dau`: bản phẳng theo luật cũ và bản phát sáng. Long xem xong nói "bản phát sáng đẹp hơn rõ", rồi bảo bỏ luật cấm vì "nó hạn chế nhiều hiệu ứng đẹp quá" (28/10).

**Đổi gì.**
| Chỗ | Từ | Sang |
|---|---|---|
| `CLAUDE.md` mục 4 | "Không quầng sáng, không tia sáng, không chuyển sắc, kể cả cho hiệu ứng nhấn." | Hiệu ứng (va chạm, vận khí, nhấn, chuyển cảnh) được phát sáng; nét, mảng màu và bóng của hình vẽ giữ như cũ. |
| `DESIGN.md` mục 0 | "Không quầng sáng, không tia sáng, không chuyển sắc." | Hình vẽ không quầng, không chuyển sắc; hiệu ứng được phát sáng (3.7). |
| `DESIGN.md` 1.3.5 | cấm chuyển sắc, quầng, phát sáng "kể cả cho hiệu ứng nhấn" | mảng màu hình vẽ phẳng; hiệu ứng được phát sáng và chuyển sắc |
| `DESIGN.md` 1.4.4 | bỏ quầng sáng, bụi sáng | chỉ bỏ quầng, bụi sáng **đứng yên làm nền**; quầng của hiệu ứng theo 3.7 |
| `DESIGN.md` 2.2 (từ khóa lớn) | "Không quầng, không phát sáng, không chuyển sắc." | chớp hay quầng chỉ lúc chữ bật ra; chữ đứng đọc thì không nằm trong quầng |
| `DESIGN.md` mục 9 | "Không quầng sáng, không tia sáng, không chuyển sắc, không bụi sáng." | hình vẽ không quầng; hiệu ứng theo 3.7 |
| `DESIGN.md` | — | thêm 3.7 "Hiệu ứng phát sáng": được dùng gì, vẫn giữ gì, thư viện mẫu `thu-hieu-ung-dau/hf-dau.js` |

**Không đổi.** Ba khối style (`style-*.txt`, prompt Nano Banana vẫn ghi tránh gradient và glow cho ảnh sinh ra), Xu, luật bóng phẳng và chiều sâu bằng thứ bậc nét, nền HF thuần đứng yên (1.4.1).

**Antigravity** (Long bảo sửa cho khớp, cùng ngày). `antigravity/LUAT-GOC.md` mục 3: dòng bút mực chỉ còn áp cho hình vẽ, thêm dòng "Hiệu ứng được phát sáng". `antigravity/BAN-GIAO-3D.md` mục 5: gạch hai chỗ lệch đã hết lệch (vành khí quyển, chớp trắng lúc va chạm), ghi lý do.

**Bản lưu.** `ban-luu/2026-10-28b_mo-hieu-ung-phat-sang/`: `truoc/` (sổ tay, DESIGN gốc, style, Xu, LUAT-GOC, BAN-GIAO-3D), `du-an-bac-ho/` (video gần nhất), `thu-hieu-ung-dau/` (phép thử), `sau/`.

---

## 2026-10-28 · Render bằng hyperframes@0.8.160

**Vì sao.** Long thấy render dạo này rất lâu, cả ở Claude Code lẫn Antigravity (video 3 phút mất 2 tiếng), trong khi trước kia cả video chỉ khoảng 30 phút. Claude Code đo trên `bac-ho-ra-di-tim-duong-cuu-nuoc`: mỗi dự án mới tạo bằng `init` tự ghim bản HyperFrames mới nhất (starbuck 0.8.155, nitendo-vs-sony 0.8.160, rồi 0.8.169 … 0.8.210); các bản mới chụp khung chậm hơn và tụt dần theo độ dài video. Bản mới chỉ nhanh khi chụp được kiểu "drawElement", kiểu này tắt khi trang có `mix-blend-mode` (lớp hạt giấy `.hat` của kênh, bộ dò đọc cả luật CSS) hay khi chạy nhiều tiến trình. Cùng video 3 phút, `-w 2`: 0.8.210 mất 97,5 phút, 0.8.160 mất 10 phút, hình giống nhau. Long bảo ghi luật (28/10).

**Bản lưu.** Trước: `ban-luu/2026-10-28_render-0.8.160/truoc/` (sổ tay, LUAT-GOC, DESIGN gốc, ba khối style, Xu). Sau: `.../sau/`. Bộ file dự án: `.../du-an-bac-ho-ra-di-tim-duong-cuu-nuoc/`. Log đo: `.../do-dac/`. DESIGN, style, Xu, minh-y không đổi.

| # | Ở đâu | Từ | Sang | Vì sao |
|---|---|---|---|---|
| R1 | sổ tay mục 6, "Chỗ riêng của máy này" | không có luật về bản render | render bằng `hyperframes@0.8.160`; `check`, `snapshot`, `preview` vẫn dùng bản ghim; kèm lý do, số đo, chỗ để log | 97,5 phút so với 10 phút trên cùng video |
| R2 | sổ tay Chặng 6, Render | "Video 14 phút mất khoảng 2 tiếng, `-w 1` hay `-w 2` như nhau" | render bằng `hyperframes@0.8.160`; video 3 phút khoảng 10 phút với `-w 2` (số tạm) | cho khớp R1 |
| R3 | `antigravity/LUAT-GOC.md` mục 4 (Dòng lệnh, Render) | chạy đúng bản ghim cho mọi lệnh; "video 14 phút ≈ 2 tiếng" | riêng `render` dùng `hyperframes@0.8.160`, kèm lý do và số đo; số cũ giữ làm lịch sử | Antigravity cũng chạy bản ghim nên dính cùng bệnh |

**Đánh đổi.** Bản 0.8.160 không có bước chặn đỉnh tiếng dưới −1 dBTP (tiếng nhỏ hơn khoảng 1 dB) và không có drawElement, dò khung tĩnh, mã hóa trong lúc chụp; với trang có hạt giấy thì các thứ đó không giúp gì. Đã thử bản mới không hạt giấy, 1 tiến trình (bật được drawElement): đoạn 62 giây mất 4 phút 09, vẫn chậm hơn 0.8.160 có hạt giấy, 2 tiến trình (3 phút 27).

### Chưa làm trong đợt này

- Chưa kiểm lỗi Chrome thoát mã 21 (LUAT-GOC mục 4, "mọi bản từ 0.8.167") có xảy ra với 0.8.160 không.
- Các dự án cũ không sửa `package.json`.

## 2026-10-26 · Bỏ nét vẽ Kuwahara khỏi gắn màu footage và ảnh thật

**Vì sao.** Long xem `longvd-chonngay` v1 (23/10) và chê ảnh thật, footage "vỡ nát, mờ tịt". Ảnh gốc rộng 1920 px, không nhỏ; lỗi do nét vẽ Kuwahara 0,75 trong chuỗi gắn màu v2b (chọn từ mẫu Domino's ngày 10/10) gom ảnh thành mảng loang. So ba mức 0,75 / 0,25 / 0 trên cùng ba cảnh, cắt 100%: Long chọn bỏ hẳn (26/10), xem v2 rồi bảo ghi thành luật cho các video sau. Nguyên văn: `ban-luu/2026-10-26_bo-kuwahara/YEU-CAU.md`.

**Bản lưu.** Trước: `ban-luu/2026-10-26_bo-kuwahara/truoc/` (sổ tay, HUONG-DAN công cụ, DESIGN gốc, ba khối style, Xu). Sau: `.../sau/`. Bộ file `longvd-chonngay` bản v2: `.../du-an-longvd-chonngay/`. Ảnh so sánh: `.../so-sanh-kuwahara.jpg`. DESIGN, style, Xu, minh-y không đổi.

| # | Ở đâu | Từ | Sang | Vì sao |
|---|---|---|---|---|
| K1 | sổ tay mục 10, "Khi dựng" | không có luật riêng; gắn màu theo mẫu v2b (muted-editorial + Kuwahara 0,75) | thêm "Gắn màu": chỉ `muted-editorial`, không Kuwahara, áp mọi video sau; ảnh nhỏ phóng kín sẽ lộ mềm nên ghi kích thước vào gợi ý chọn | Long chốt 26/10 sau v1 |
| K2 | sổ tay Chặng 6, mục 10 (ảnh thật làm nền, đoạn so với kênh Vui Vẻ, mẫu Domino's) | "gắn màu v2b" | "gắn màu `muted-editorial`, không Kuwahara"; dòng mẫu Domino's giữ lịch sử, thêm ghi chú đã bỏ Kuwahara | cho khớp K1 |
| K3 | sổ tay Chặng 6, render | "Nhiều ảnh gắn Kuwahara thì render `-w 1`" | video 14 phút mất khoảng 2 tiếng, `-w 1` hay `-w 2` như nhau (số tạm), chạy nền và báo giờ xong | `longvd-chonngay` v1 `-w 1` 127 phút, v2 `-w 2` 121 phút |
| K4 | `cong-cu\HUONG-DAN.md`, mục Dựng | chuỗi `$g` có `"kuwahara":0.75, kuwaharaRadius, kuwaharaSharpness, kuwaharaSaturation` | `"effects":{"kuwahara":0}`; ghi chú ảnh nhỏ và render sửa theo | cho khớp K1 |
| K5 | `antigravity/LUAT-GOC.md` mục 3, 4 | không có luật gắn màu; "trang nặng (gắn màu Kuwahara)"; "nhiều ảnh v2b (Kuwahara) thì render `-w 1`" | mục 3 thêm "Gắn màu" (chỉ `muted-editorial`, không Kuwahara); mục 4 sửa ghi chú trang nặng và render (14 phút ≈ 2 tiếng, `-w 1` hay `-w 2` như nhau, số tạm) | Long bảo sửa cho khớp, 26/10. Bản trước, sau: `ban-luu/2026-10-26_bo-kuwahara/truoc|sau/antigravity/`, ghi chú `THEM-LUAT-GOC.md` |

### Chưa làm trong đợt này

- ~~`antigravity/LUAT-GOC.md` còn nhắc Kuwahara~~: Long bảo sửa cùng ngày, xem K5.
- Các dự án cũ và mẫu `domino-30-phut/mau/mau-footage.html` giữ nguyên Kuwahara.

## 2026-10-24 · Viết lại Chặng 1–6 cho đối sách full HF

**Vì sao.** Từ đợt 2026-10-10, sổ tay ghi Chặng 2–6 "đang viết lại" và vẫn mang chữ Veo (đọc `veo-prompt.txt`, đặt clip Veo). Cách chạy thật chỉ nằm ở `thu-hf-01/QUAN-SAT.md` và các mục cuối VAT-LIEU của từng video. Long bảo viết lại theo cách đang chạy, ngày 24/10. Nguyên văn: `ban-luu/2026-10-24_chang-full-hf/YEU-CAU.md`.

**Căn cứ.** Các mục ghi theo chặng ở cuối VAT-LIEU của `giao-thong-thuy-dien`, `duong-seoul`, `duong-seoul-p2`, `ngay-dep-test-anti`, `longvd-chonngay`; `cong-cu/HUONG-DAN.md`; `tools/whisper/HUONG-DAN.md`.

**Bản lưu.** Trước: `ban-luu/2026-10-24_chang-full-hf/truoc/` (sổ tay, DESIGN gốc, ba khối style, Xu). Sau: `.../sau/CLAUDE.md`. Bộ file `longvd-chonngay` (VAT-LIEU, DESIGN, index, compositions, thư viện, hạt giấy): `.../du-an-longvd-chonngay/`. DESIGN, style, Xu, minh-y không đổi.

| # | Ở đâu | Từ | Sang | Vì sao |
|---|---|---|---|---|
| H1 | sổ tay, đầu "Chặng 1–6" | khung "Đang viết lại", đi tạm theo `thu-hf-01` | ghi nguồn và ngày viết lại; VAT-LIEU là sổ ghi của dự án, xong mỗi chặng thêm một mục có ngày (kết quả, chỗ khác kế hoạch, việc chờ, file rác) | năm video gần nhất đều làm vậy |
| H2 | Chặng 1 | chạy whisper và khopdong.py | thêm báo tỉ lệ khớp; sửa tay đoạn whisper nuốt thì ghi `ghi_chu`, giữ bản chưa sửa | theo HUONG-DAN whisper và `longvd-chonngay` |
| H3 | Chặng 2 | phương án sân khấu: đề xuất 2–3 phương án, viết mục bút mực | Nguyên liệu: minh-y viết VAT-LIEU; vật thể chính đề xuất trong "Ý chung", `PHUONG-AN.md` chỉ khi Long muốn | không video nào từ `giao-thong-thuy-dien` viết PHUONG-AN; Long chọn vậy ở `longvd-chonngay` (câu 5) |
| H4 | Chặng 3 | storyboard và VAT-LIEU, tham chiếu từ `veo-prompt.txt` | Sinh ảnh và tìm tư liệu, chạy song song: ảnh do Long trên Flow; tư liệu thật theo HUONG-DAN (không chạy hai công cụ song song); sound effect khi được thử | storyboard nay là mục Sân khấu của VAT-LIEU; không còn prompt Veo |
| H5 | Chặng 2 | không có | kho chưa có thì tìm vật liệu S1 trong các dự án cũ, chép không di chuyển; link bài báo do Long đưa hoặc duyệt | cách làm ở `longvd-chonngay` |
| H6 | Chặng 4 | chạy tách nền, mở `_xem-nhanh.png` | thêm: chép ảnh từ chỗ Long để vào `vat-lieu-goc` với tên gọn; `--gop n` khi dính; ghi bảng tờ → sticker, tờ nên sinh lại, file rác | theo các mục "Tách nền" |
| H7 | Chặng 5 | "dựng khối 1 trước" | mỗi sân khấu một sub-composition; thư viện chép từ dự án gần nhất; mốc từ `mocgio.json`; check, snapshot, preview; render `_khoi1_vN` | theo các mục "Dựng khối 1" |
| H8 | Chặng 6 | đối chiếu và đặt clip Veo, giữ hình cuối, ô xám chờ clip, chụp chỗ cắt Veo↔HF | dựng đủ sân khấu, soát trước render (check từng đoạn khi quá hạn giờ, soi snapshot), render `-w 1` khi nhiều Kuwahara, đo tiếng, trích khung, báo số liệu | không còn clip Veo |
| H9 | sau Chặng 6 | không có | quan sát ghi cuối VAT-LIEU; thứ dùng được thì đề nghị đưa vào mục 10 hoặc thành luật | theo mục 9 |

### Chưa làm

- Sổ tay mục 5, phần "Ảnh tham chiếu", vẫn quyết theo `veo-prompt.txt` và trỏ "báo cáo chặng 3"; minh-y quyết tham chiếu theo ảnh mỏ neo và tờ gốc. Hai bên lệch, chờ Long chốt rồi sửa mục 5.
- Sổ tay mục 1, câu cuối, còn "cùng chuỗi style với cảnh Veo".
- `ban-luu/README.md` chưa liệt kê các bản từ 2026-10-20 trở đi (luật không sửa file trong `ban-luu`).

## 2026-10-20c · Điều khoản chủ quyền cho bản đồ

**Vì sao.** Skill minh-y nhắc "điều khoản chủ quyền trong sổ tay" nhưng sổ tay chưa có điều khoản nào. Long chốt nội dung ngày 20/10.

**Bản lưu.** Trước: `ban-luu/2026-10-20c_chu-quyen-ban-do/truoc/`. Sau: `.../sau/`.

| # | Ở đâu | Từ | Sang | Vì sao |
|---|---|---|---|---|
| C1 | sổ tay mục 3, dưới "Bản đồ" | không có | bản đồ có Việt Nam hay Biển Đông phải thể hiện Hoàng Sa, Trường Sa thuộc Việt Nam; gọi Biển Đông, không "South China Sea", không đường lưỡi bò; ảnh Wikimedia không đạt thì dựng bằng code từ dữ liệu địa lý thật và tự đặt hai quần đảo | Long chốt |
| C2 | minh-y bước 6, việc "Hiểu" | "theo đúng điều khoản chủ quyền trong sổ tay" | tóm tắt điều khoản, trỏ sổ tay mục 3; khi gợi ý ảnh bản đồ phải ghi đã kiểm ba điều | khớp sổ tay |

### Chưa làm

- Long cần tải bản nguồn minh-y mới lên claude.ai (gồm cả đợt 2026-10-20b và 2026-10-20c).

## 2026-10-20b · Luật bản đồ linh hoạt

**Vì sao.** Sổ tay mục 3 cấm vẽ bản đồ bằng code (bài học Coca: đường viền vẽ tay thô), còn skill minh-y bảo dựng bản đồ bằng code từ dữ liệu địa lý thật. Lệch này lộ ra ở video `giao-thong-thuy-dien` (Long chọn ảnh bản đồ Wikimedia theo sổ tay). Ngày 20/10 Long chốt: linh hoạt, hiệu ứng khó thì code cho dễ làm, đơn giản thì lấy ảnh trên Wikimedia.

**Bản lưu.** Trước: `ban-luu/2026-10-20b_ban-do/truoc/`. Sau: `.../sau/`.

| # | Ở đâu | Từ | Sang | Vì sao |
|---|---|---|---|---|
| B1 | sổ tay mục 3, câu 2 | "Không vẽ bản đồ hay nơi chốn bằng code." | "Không vẽ nơi chốn bằng code." và mục "Bản đồ: chọn linh hoạt theo hiệu ứng": hiệu ứng khó → code từ dữ liệu địa lý thật (GeoJSON, TopoJSON); chỉ nhãn, mũi tên → ảnh bản đồ Wikimedia, ghi công; không vẽ tay đường viền, không sinh bằng Nano Banana | Long chốt |
| B2 | sổ tay mục 3, bài học Coca | "code bắt chước đường viền tự nhiên" | thêm "bằng tay"; bản đồ từ dữ liệu địa lý thật không mắc lỗi này | làm rõ ranh giới |
| B3 | minh-y bước 1, việc "Hiểu" | "bản đồ dựng từ dữ liệu địa lý thật" | bản đồ code từ dữ liệu thật hoặc ảnh Wikimedia, theo sổ tay mục 3 | khớp sổ tay |
| B4 | minh-y bước 6, việc "Hiểu" | "Bản đồ dựng bằng code từ dữ liệu địa lý thật…, không sinh ảnh bản đồ." | chọn theo hiệu ứng, ghi rõ chọn cách nào và vì sao | khớp sổ tay |

### Chưa làm

- Long cần tải bản nguồn minh-y mới lên claude.ai (bản đã tải trước đó là bản của đợt 2026-10-20, đã kiểm trùng nội dung).
- minh-y còn câu "Bản đồ có Việt Nam hay Biển Đông phải theo đúng điều khoản chủ quyền trong sổ tay", nhưng sổ tay chưa có điều khoản đó. Chờ Long quyết có viết không. Đã làm ở đợt 2026-10-20c.

## 2026-10-20 · Ảnh thật làm nền sân khấu

**Vì sao.** Video `giao-thong-thuy-dien` (18/10) thử đặt ảnh thật (Wikimedia, kho công) làm nền sân khấu, sticker và chữ HF đè lên, thay cho nền sinh bằng Nano Banana. Long duyệt khối 1, dựng cả video ba bản; ở v2 Long chê ảnh ngã tư Gò Vấp không cho thấy rõ "đi bên phải", thay bằng ảnh Quốc lộ 1A có mũi tên (v3). Ngày 20/10 Long bảo ghi lại để phiên sau tự biết, nhưng không phải sân khấu nào cũng dùng ảnh thật làm nền, phải chia cho hợp lý. Nguyên văn: `ban-luu/2026-10-20_anh-that-lam-nen/YEU-CAU.md`.

**Bản lưu.** Trước: `ban-luu/2026-10-20_anh-that-lam-nen/truoc/` (sổ tay, minh-y, `cong-cu/HUONG-DAN.md`). Sau: `.../sau/`. Bộ file dự án `giao-thong-thuy-dien` (VAT-LIEU, index, compositions, hf-video.js) ở `.../du-an-giao-thong-thuy-dien/`. DESIGN, khối style, Xu không đổi.

| # | Ở đâu | Từ | Sang | Vì sao |
|---|---|---|---|---|
| N1 | sổ tay mục 10 | dòng "Thử ở `giao-thong-thuy-dien`… Chưa phải luật" | mục "Ảnh thật làm nền sân khấu": khi nào làm nền (nơi thật cần nhận ra, ảnh nhìn ngang hoặc dọc đường, có đất trống phía trước, cạnh dài từ ~900 px), khi nào phủ kín (ảnh đúng mà không có chỗ cho sticker), khi nào không dùng (cơ chế, số liệu, giả định, nơi chung chung, ảnh nước ngoài thay Việt Nam); ảnh phải nói được đúng ý câu; có phương án dự phòng; cách dựng tóm tắt | Long cho dùng tiếp, yêu cầu chia hợp lý |
| N2 | sổ tay mục 10, dòng hai kênh mẫu | "chưa thử ở kênh mình" | "đã thử ở `giao-thong-thuy-dien` theo cách riêng (không làm mờ, gắn màu v2b)" | cập nhật |
| N3 | minh-y bước 2, "Hình thật" | "Ảnh thật làm phông (quan sát từ kênh Vui Vẻ, chưa thử)… để Long quyết" | "Ảnh thật làm nền sân khấu" chia ba trường hợp (làm nền / phủ kín / vẫn vẽ hoặc nền giấy), luật "ảnh phải nói đúng ý câu", số đo 40% thời lượng ở video thử (số tạm), phương án dự phòng, Xu không đứng trên ảnh làm nền | như N1 |
| N4 | minh-y bước 2, mỗi sân khấu có | "Nền: một ảnh nền." | nền là ảnh sinh, ảnh thật (khi được phép và hợp) hoặc nền giấy | như N1 |
| N5 | minh-y bước 6, Thấy thật | "phủ kín hay làm phông" | "phủ kín hay làm nền sân khấu" kèm nhân vật đứng lên, tiêu chí chọn ảnh, mũi tên hay vạch code cần thêm | để Claude Code chọn ảnh đúng ngay từ đầu |
| N6 | minh-y Tự kiểm | không có | ảnh làm nền chỉ ở "Thấy lại" cần nhận ra đúng nơi; nói đúng ý câu; có dự phòng | soát |
| N7 | `cong-cu/HUONG-DAN.md` mục Dựng | không có | mục "Ảnh thật làm nền sân khấu": gắn màu `<img>` bằng `media-treatment`, bóng tiếp đất, lật ngang trên khung bọc, ảnh nhỏ, tắt lớp bị che, render `-w 1`, tìm thêm ảnh trong `.work/tim-<dòng>/` | cách dựng đã chạy ở video thử |

### Chưa làm

- Long cần tải bản nguồn minh-y mới lên claude.ai.
- Còn lệch giữa minh-y (việc "Hiểu": "bản đồ dựng bằng code từ dữ liệu địa lý thật") và sổ tay mục 3 ("không vẽ bản đồ bằng code"). Ở `giao-thong-thuy-dien` Long chọn theo sổ tay (ảnh bản đồ Wikimedia). Chưa sửa vì không thuộc đợt này; chờ Long quyết.

## 2026-10-13 · minh-y viết sẵn đầu vào cho công cụ tìm tư liệu

**Vì sao.** Công cụ `cong-cu/lay-tu-lieu.py`, `cong-cu/chup-bao.py` (dựng 09/10 cho w1d4) đọc `assets/tulieu/truy-van.txt` và `bao.txt`. Trước đây Claude Code tự chuyển danh sách "Thấy thật" của minh-y thành hai file đó; Long muốn minh-y viết sẵn. Nguyên văn: `ban-luu/2026-10-13b_minh-y-dau-vao-cong-cu/YEU-CAU.md`.

**Bản lưu.** Trước: `ban-luu/2026-10-13b_minh-y-dau-vao-cong-cu/minh-y-truoc/`. Sau: `.../minh-y-sau/`.

| # | Ở đâu | Từ | Sang | Vì sao |
|---|---|---|---|---|
| M1 | minh-y Bước 6 | danh sách Thấy thật và Tin bằng lời | thêm khuôn hai file `truy-van.txt` (`#dòng \| A/B \| truy vấn tiếng Anh \| nguồn`) và `bao.txt` (`#dòng \| link \| tiêu đề \| câu bôi nguyên văn \| nguồn ghi trên video`) | Claude Code chép ra chạy ngay |
| M2 | minh-y Đầu ra 5, 6 | không có | kèm hai code block `// bao.txt`, `// truy-van.txt` khi video được phép | như trên |
| M3 | minh-y Tự kiểm | không có | soát cột, ngôn ngữ, Mixkit 1–2 từ, câu bôi không chép từ trí nhớ, link chỉ từ Long | tránh bịa trích dẫn |
| M4 | `cong-cu/HUONG-DAN.md` bước 2 | Claude Code tự viết hai file | chép hai code block từ VAT-LIEU; cột câu bôi trống thì đọc trang rồi điền | khớp minh-y mới |

### Chưa làm

- Long cần tải bản nguồn mới lên claude.ai.

## 2026-10-13 · Cách đặt tư liệu thật vào skill minh-y

**Vì sao.** Chủ kênh thấy footage và bài báo trong video Domino's đặt bừa: chỗ cần thì không có, chỗ có thì thừa. Phân tích video "Ngành xổ số lớn như thế nào" của kênh Lóng, đặt cạnh Domino's v4 (`phan-tich/kenh-mau/BAO-CAO-FOOTAGE.md`), cho thấy tổng lượng hình thật hai bên gần bằng nhau (38% và 43%). Domino's lệch ở bốn chỗ: dùng footage để lấy không khí, rải ảnh nhỏ giữa tranh vẽ, cho cùng một bài báo hiện lại nhiều lần, và để trống phần đời sống Việt Nam bây giờ. Chủ kênh chốt: tư liệu thật chỉ dùng cho video được cho phép từng video. Nguyên văn: `ban-luu/2026-10-13_footage-minh-y/YEU-CAU.md`.

**Bản lưu.** Trước: `ban-luu/2026-10-13_footage-minh-y/so-tay-truoc/`, `minh-y-truoc/`. Sau: `so-tay/`, `minh-y-sau/`. DESIGN, khối style, Xu không đổi.

| # | Ở đâu | Từ | Sang | Vì sao |
|---|---|---|---|---|
| T1 | minh-y bước 1 | bốn việc: Tin, Thấy lại, Hiểu, Cảm; "footage thật chưa được Long chốt" | thêm việc "Thấy thật" (hình thật của đúng thứ cần nhận ra, chỉ khi video được phép, không có thì vẽ) và bốn câu hỏi chọn việc theo thứ tự | kênh Lóng dùng hình thật để nhận ra và để tin, không để lấy không khí |
| T2 | minh-y Đầu vào | không có | mục 8: video có được dùng tư liệu thật không; mặc định là không | luật chủ kênh chốt 13/10 |
| T3 | minh-y bước 1, việc "Tin" | chỉ bài báo | thêm văn bản luật, ghi "TRÍCH: …" | kênh Lóng dùng ba lần cho mức phạt, hoa hồng, bí mật người trúng |
| T4 | minh-y bước 2 | không có | mục "Hình thật": chuỗi theo phần, phủ kín khung, bài báo hiện một lần và đứng suốt đoạn đọc số, chữ đè chỉ năm hoặc tiêu đề, gạch chéo đỏ cho thứ phi pháp, Xu đứng ở góc, footage lấy không khí tối đa một cú, ảnh thật làm phông (thử) | số đo trên kênh Lóng; Domino's lệch ở các điểm này |
| T5 | minh-y bước 6, Đầu ra, Tự kiểm | không có mục tư liệu | mục "Thấy thật" trong VAT-LIEU (thứ cần nhận ra, loại hình, từ khóa, phủ kín hay phông, phương án vẽ); ba dòng tự kiểm | để soát được |
| T6 | minh-y tờ đạo cụ, Đầu vào | `style-nhan-vat.txt` | `style-do-vat.txt` | việc còn treo từ đợt 2026-10-07 (H1) |
| T7 | sổ tay mục 0 | không ghi bản nguồn skill | `phongcach/skills/minh-y/SKILL.md` là bản nguồn, tải lên claude.ai | bản skill trên máy là bản đồng bộ, sửa trực tiếp có thể bị ghi đè |
| T8 | sổ tay mục 10, nhật ký | chỉ có mục tư liệu thật riêng cho w1d4 | thêm quan sát cách đặt và luật "chỉ cho video chủ kênh cho phép" | như trên |

### Chưa làm trong đợt này

- ~~Tải `phongcach/skills/minh-y/SKILL.md` lên claude.ai.~~ Chủ kênh đã tải (báo ngày 2026-10-13).
- Sổ tay mục 10 thêm các luật khi dựng tư liệu thật (cùng ngày, sau khi tải skill); không cất bản riêng vì chỉ thêm vào mục "Đang theo dõi".
- Thử luật mới trên một video được phép dùng tư liệu thật, rồi xem lại các số tạm (2–4 s mỗi cú, 8–18 s mỗi bài báo, khoảng 1,9 lần mỗi phút).
- Chưa thử "ảnh thật làm phông" với bút mực của kênh.
- Domino's v4 không sửa lại.

## 2026-10-10 · Đối sách full HyperFrames

**Vì sao.** Chủ kênh chốt: kênh làm video hoàn toàn bằng HyperFrames; Veo chỉ là bộ công cụ tạo nền, nhân vật, đồ vật. Quy trình Veo (khối VEO, clip Veo, chuỗi `style-veo`/`style-sticker`) không phải đối sách nữa, cất lại để dùng sau. Nguyên văn: `ban-luu/2026-10-10_full-hf/YEU-CAU.md`.

**Bản lưu.** Trước: `ban-luu/2026-10-10_full-hf/so-tay-truoc/`. Sau: `ban-luu/2026-10-10_full-hf/so-tay/`. DESIGN, Xu không đổi.

| # | Ở đâu | Từ | Sang | Vì sao |
|---|---|---|---|---|
| F1 | `phongcach/style-veo.txt`, `style-sticker.txt` | nằm ở `phongcach/` | dời vào `ban-luu/2026-10-10_full-hf/phongcach-cat/` | quy trình cũ, cất không xóa |
| F2 | sổ tay mục 0, mục 5 | chuỗi style gốc là `style-veo` (nền) và `style-sticker` (sticker) | `style-nhan-vat` (nhân vật), `style-do-vat` (đồ vật), `style-nen` (nền) | khớp khối S1 đang dùng từ 07/10 |
| F3 | sổ tay mục 1 | nhip-doan, khối VEO/HF, clip Veo đặt vào video | nhip-hf, mọi dòng HF, minh-y viết VAT-LIEU, Flow chỉ sinh nguyên liệu | đối sách full HF |
| F4 | sổ tay Chặng 0, mục 7 | `veo-prompt.txt`, `assets/veo`, `assets/veo-clip` | ghi là quy trình cũ; thêm `mach.txt`, ba file style S1, `assets/tulieu` | như trên |
| F5 | sổ tay Chặng 2–6 | viết theo Veo | thêm khung tạm theo cách chạy ở `thu-hf-01`; chờ viết lại | chủ kênh chưa chốt từng chặng |

### Chưa làm trong đợt này

- Viết lại Chặng 2–6 cho đối sách full HF (đề xuất 12 trong `thu-hf-01/QUAN-SAT.md`).
- DESIGN.md vẫn là chuẩn bút mực (cel chàm, hạt giấy) trong khi lớp code ở `thu-hf-01` đã theo S1 (Long chốt 07/10); cần một đợt sửa DESIGN có cất bản (đề xuất 9).

## 2026-10-07 · Khối style riêng cho đạo cụ (lần thử 1 dây chuyền 100% HyperFrames)

**Vì sao.** Trong lần thử `thu-hf-01`, tờ đạo cụ dùng chung khối `style-nhan-vat.txt` (style S1, Long đặt ngày 07/10). Khối này toàn câu tả nhân vật chibi, nên máy bán hàng Coca-Cola ra thành nhân vật có đầu, mặt, mắt, tay chân; câu "plain inanimate object…" trong prompt không thắng nổi. Long duyệt đề xuất tách khối style cho đồ vật. Căn cứ: `thu-hf-01/QUAN-SAT.md` mục 1.

**Bản lưu.** Không cần: chỉ thêm file mới, không file nào bị thay. Sổ tay, DESIGN, `style-nhan-vat.txt`, `style-nen.txt` không đổi.

| # | Ở đâu | Từ | Sang | Vì sao |
|---|---|---|---|---|
| H1 | `phongcach/style-do-vat.txt` (mới) | tờ đạo cụ dùng `style-nhan-vat.txt` | tờ đạo cụ dùng `style-do-vat.txt`: giữ nét và màu của S1 (viền đen dày đều, đầu nét tròn, màu phẳng, tối đa một mảng tối), bỏ tỷ lệ chibi và mặt, cấm mặt, mắt, tay chân, linh vật | đồ vật không mọc mặt |
| H2 | `tools/tach-nen/tachnen.py` | `tachnen.cmd` dừng vì Windows Application Control chặn DLL của numba (từ 04/10) | `tachnen.py` tự thay pymatting bằng module rỗng trước khi nạp rembg; bản trước: `tools/tach-nen/tachnen-truoc-2026-10-07.py` | công cụ không dùng alpha matting; sticker ra trùng từng byte với bản cũ; Long cho phép sửa công cụ chung |

### Chưa làm trong đợt này

- Skill minh-y (trên claude.ai) vẫn ghi "Tờ đạo cụ — dùng `style-nhan-vat.txt`"; cần sửa thành `style-do-vat.txt`, kể cả mục Đầu vào và Tự kiểm.
- Chưa sinh lại máy bán hàng để kiểm khối mới (`thu-hf-01/CHI-DAN-FLOW.md`, Batch 3).
- Style S1 (`style-nhan-vat.txt`, `style-nen.txt`) chưa có mục riêng trong nhật ký này; sổ tay và DESIGN chưa sửa theo S1 (bàn giao thử nghiệm cấm sửa trong lần thử).

## 2026-10-02 · Bỏ CapCut, clip Veo đặt thẳng vào HyperFrames

**Vì sao.** Toàn bộ video vốn đã là một project HyperFrames có mốc giây từng dòng (`mocgio.json`), nên ghép clip Veo bằng tay trong CapCut là bước thừa. Chủ kênh cũng chốt không dùng API trả phí để sinh ảnh hay clip: ảnh và clip vẫn tự làm trên giao diện, Claude Code chỉ sắp xếp và dựng. Nguyên văn yêu cầu: `ban-luu/2026-10-02_bo-capcut/YEU-CAU.md`.

**Bản lưu.** Trước: `ban-luu/2026-10-02_bo-capcut/so-tay-truoc/`. Sau: `ban-luu/2026-10-02_bo-capcut/so-tay/`. DESIGN, chuỗi style, Xu không đổi.

| # | Ở đâu | Từ | Sang | Vì sao |
|---|---|---|---|---|
| G1 | sổ tay 1 | dòng VEO chỉ là khung giữ chỗ; chủ kênh ghép clip Veo đè lên trong CapCut | clip Veo đặt thẳng vào `index.html` theo mốc từng dòng; render HyperFrames là video hoàn chỉnh | bỏ một bước tay, mốc đã có sẵn |
| G2 | sổ tay Chặng 0, 7 | không có chỗ cho clip | thư mục `assets\veo-clip\`, tên theo số dòng (`05.mp4`), chỉ cần có trước Chặng 6 | Claude Code nhận clip theo tên, không đoán bằng hình |
| G3 | sổ tay 2 | năm chặng | sáu chặng; Chặng 6: đối chiếu thư mục, đặt clip theo khung dòng, cắt đuôi clip dài, giữ hình cuối và báo khi clip ngắn, tắt tiếng, khung xám từng dòng cho dòng thiếu, chụp chỗ cắt | quy hết việc ghép về một chặng có điểm duyệt |
| G4 | sổ tay 8 | không có | không dùng dịch vụ tính tiền (API Gemini, Nano Banana Pro, Veo) | chủ kênh chốt, tránh mất tiền ngoài ý muốn |
| G5 | sổ tay 10 | — | theo dõi cách đặt clip mới trên video đầu (Häagen-Dazs) | chưa thử trên video thật |

Âm thanh clip Veo (câu hỏi còn mở trong tài liệu hướng dẫn người vận hành): chốt là tắt.

### Chưa làm trong đợt này

- Tài liệu "Quy trình làm video — Sinh Viên Kinh Tế" (bản cho người vận hành) vẫn ghi bước ghép CapCut ở mục 6; cần sửa theo.
- Các dự án cũ không sửa.

---

## 2026-09-30 (đợt 2) · HF tự chủ, đầu vào prompt Veo

**Vì sao.** Chủ kênh thấy từ khi có vật liệu Nano Banana Pro, HF gần như phụ thuộc vào nguyên liệu đến từ Veo. Chủ kênh không coi việc dùng vật liệu là lỗi, vì vật nhìn đẹp hơn. Nhưng HF mất đi tính sáng tạo và đặc trưng riêng, cả ở nền. Những thứ như biểu đồ, sóng, tầng tầng lớp lớp, nền motion graphic dựng không cần vật liệu Veo lại hiệu quả và chuyên nghiệp hơn nhiều.

Thứ hai: chủ kênh thường phải hỏi xem tờ nào cần ảnh tham chiếu. Từ nay chủ kênh nạp prompt Veo làm đầu vào, và Claude Code tự chỉ ra tờ nào, nền nào cần tham chiếu, tham chiếu cảnh nào. Nguyên văn yêu cầu: `ban-luu/2026-09-30b_hf-tu-chu/YEU-CAU.md`.

**Bản lưu.** Trước: `ban-luu/2026-09-30_chuan-veo-moi/` (trùng từng byte với bản đang dùng ngay trước đợt này). Sau: `ban-luu/2026-09-30b_hf-tu-chu/`.

| # | Ở đâu | Từ | Sang | Vì sao |
|---|---|---|---|---|
| E1 | sổ tay 3, DESIGN 0.4 | một câu hỏi: "code có vẽ đẹp được thứ này không?" | hai câu hỏi theo thứ tự. **Câu 1**: khối có cần người xem nhận ra một vật, người, nơi cụ thể không; không cần thì là **HF thuần**, cả khối bằng code. **Câu 2** giữ như cũ cho phần phải vẽ. Thêm: không lấy vật liệu chỉ vì Veo có sẵn | sửa ở gốc: luật cũ chỉ hỏi "ai vẽ", không hỏi "có cần vẽ vật không", nên khối nào cũng kéo sticker vào |
| E2 | sổ tay 3 | khối cần nơi có thật thì dùng ảnh nền Veo | chỉ khi cần người xem **nhận ra** nơi đó; ý về dòng chảy, mạng lưới, phạm vi thì dựng hình trừu tượng (nút, đường, vùng), không vẽ bản đồ bằng code | giữ bài học Coca mà không đẩy mọi thứ sang ảnh |
| E3 | sổ tay 3 | "thứ gì không có trong danh sách thì không được tự vẽ" | giữ; thêm: danh sách để soát, không để hạn chế; lỗi Coca là code bắt chước đường viền tự nhiên, không phải code vẽ nhiều | luật cũ bị đọc thành "vẽ ít đi" |
| E4 | sổ tay 1 | "vật và người trong khối HF lấy từ sticker" | khối HF không bắt buộc có vật hay người; nhiều khối là HF thuần | |
| E5 | sổ tay chặng 2 | phương án sân khấu và vật thể chính | mỗi phương án ghi từng khối HF là thuần hay có vật liệu, kèm lý do; vật thể chính có thể là hình code | quyết từ sớm, không để lọt sang chặng 3 |
| E6 | sổ tay chặng 3, 4 | VAT-LIEU luôn có prompt các tờ | có dòng Tham chiếu và Thứ tự sinh; video toàn khối thuần thì chỉ còn mục "Những thứ code tự vẽ"; không có sticker thì bỏ chặng 4 | |
| E7 | DESIGN 1.4 | nền sân khấu số liệu: giấy (hoặc xanh đêm) | **nền motion graphic code**: giấy + hạt, mảng phẳng một màu hằng số, dải tầng phẳng, lưới mảnh; không chuyển sắc, không quầng, không bokeh | nền là một phần sân khấu riêng của HF |
| E8 | DESIGN 5.4 (mới) | — | "Sân khấu HF thuần": vốn hình (biểu đồ, sóng xếp tầng, tầng lớp, lưới ô, dòng chảy, sơ đồ nút, thang đo, nền), sáu điều làm cho chuyên nghiệp (hệ canh, ít màu, chiều sâu bằng tầng phẳng, chuyển động có hệ, một hình chính, bút mực), phép kiểm "bỏ chữ vẫn đọc ra ý". **Đang thử**, số tạm | đặt tên và chuẩn cho thứ HF làm tốt |
| E9 | DESIGN 0, 6, 9 | HF định nghĩa chủ yếu qua Veo; vật chính ngầm là sticker | đoạn "HF có sân khấu riêng"; vật chính có thể là hình code; khối HF thuần nối với Veo bằng lớp hằng số và thứ mang sang, không bắt chước cảnh | |
| F1 | sổ tay chặng 0, 7 | không có đầu vào prompt Veo | `assets\veo-prompt.txt` (đầu ra Minh Ý dán nguyên, mỗi prompt mở bằng số dòng `#5`); ảnh Veo khi có vào `assets\veo\` (`05.jpg`, `05-2.jpg`) | để Claude Code tự thấy cảnh nào có gì |
| F2 | sổ tay 5 | "vật hay người có trong Veo thì lấy ảnh Veo làm tham chiếu, nhắc chủ kênh sinh ảnh Veo trước" | **Claude Code tự quyết, không hỏi**. Mỗi tờ, mỗi nền có dòng Tham chiếu (ảnh nào, cho vật nào, vì sao, hoặc "không cần" kèm lý do). Cần khi thứ đó có trong prompt Veo; chọn cảnh thấy rõ nhất (người: toàn thân; nơi: cùng nơi, cùng giờ); tối đa 3 ảnh mỗi tờ (tạm); vật phải giống sticker khác thì kèm tờ đó và sinh tờ đó trước; nền không cùng nơi thì chỉ chép giờ và màu trời; thiếu thông tin thì đoán, ghi rõ, báo một lần | chủ kênh không phải hỏi lại mỗi video |

Không đổi: chuỗi style, Xu, bút mực, bảng màu.

---

## 2026-09-30 · Chuẩn nhìn mới theo cảnh Veo

**Vì sao.** Kênh vừa nâng cấp cảnh Veo, qua ba lượt sửa chuỗi style: vẽ kín bối cảnh, màu từ nơi thật; ánh sáng theo giờ tô bằng mảng phẳng; cho phép biển hiệu và logo thật. Chủ kênh đã duyệt kết quả. HF cần theo cùng ngôn ngữ nhìn để cắt qua lại vẫn là một thế giới. Tài liệu bàn giao: `ban-luu/2026-09-30_chuan-veo-moi/BAN-GIAO.md`. Chủ kênh duyệt toàn bộ bảng đối chiếu và năm câu C1–C5 theo đề xuất trong phiên.

**Bản lưu.** Trước: `ban-luu/2026-09-29_truoc-chuan-veo-moi/`. Sau: `ban-luu/2026-09-30_chuan-veo-moi/`.

### Chuỗi style và prompt

| # | Đổi gì | Từ | Sang | Vì sao |
|---|---|---|---|---|
| A1 | File chuỗi style | một file `phongcach/style.txt` (chuỗi giản lược: bảng màu khóa, ánh sáng đều, cấm mọi chữ), dùng chung cho sticker, nền, Veo | hai file: `style-veo.txt` (nguyên văn chuỗi Veo mới, dùng cho Veo và ảnh nền nơi chốn), `style-sticker.txt` (cùng gốc, thay bối cảnh bằng nền trơn). `style.txt` giữ nguyên trên đĩa, thôi dùng | sticker, nền và Veo ra cùng một lò |
| A2 | Nền của tờ sticker | nền một màu có sắc (sổ tay mục 5) | **giữ nguyên**; bản sticker đề xuất ghi "white background" được đổi thành "a plain flat background of one solid color" | tách nền không bắt được lỗ thật trên nền trắng (C1) |
| A3 | Màu nền tờ | không trùng màu vật | thêm: không dùng xanh dương, xanh đêm | mặt tối chàm của vật sẽ trùng nền, bị khoét |
| A4 | Câu chủ thể trong chuỗi sticker | bản đề xuất: "A single isolated subject" | "Each subject is isolated…", "bold outlines on each subject" | tờ gom nhiều vật; "single" làm máy vẽ một vật hoặc lệch độ kỹ |
| A5 | Chữ trên sticker | cấm mọi chữ, số, logo; không gọi tên thương hiệu | cho phép logo, tên thương hiệu thật khi vật ngoài đời có nó, đúng chính tả, không số (C2 phương án b) | chữ thế giới thuộc về ảnh; chữ thông tin vẫn là của HF |
| A6 | Ảnh nền nơi chốn | chuỗi giản lược, "plain wall… quiet shapes" | `style-veo.txt`, vẽ kín mép, chừa khoảng trống cho chữ HF; chỉ giữ biển hiệu định danh nơi chốn (C4) | nền HF và cảnh Veo là cùng một nơi; biển hiệu thừa tranh với chữ thông tin |
| A7 | Hạt giấy trong sticker | "very faint paper grain" | bỏ | HF phủ tấm hạt giấy riêng, tránh hai lớp hạt |
| A8 | Câu "mỗi cảnh một chủ thể rõ" | có trong chuỗi, cần nhắc canh độ kỹ | không còn trong chuỗi sticker; vẫn nhắc canh bằng mắt | chuỗi mới không có câu đó |

### DESIGN.md (bản gốc)

| # | Mục | Từ | Sang | Vì sao |
|---|---|---|---|---|
| B0 | đầu file | "Bản chép cho video McDonald's", "bản nháp 2" | "Bản gốc", chuẩn Veo mới; ghi rõ số đo cũ là số tạm | sửa dòng còn treo từ 29/09 |
| B1 | 0 | tả kênh: "màu nước loang, từ khóa lớn phát sáng" | tả theo chuẩn Veo mới: nét thứ bậc, màu phẳng, cel, không phát sáng, tái hiện nơi thật | đoạn đầu tiên người dựng đọc |
| B1b | 0.5 | dòng hiệu ứng có "loang nước, tia sáng"; nền có "ánh sáng, loang nhẹ" | chỉ còn nét rung và hạt giấy | không phát sáng, không loang |
| B2 | 1 | một bảng màu đo từ 9 clip ngày 20/09 (1.1 nền và mực, 1.2 nhấn, 1.3 nhân vật) | **hai lớp**: 1.1 hằng số thương hiệu (`--giay`, `--muc`, `--muc-nhat`, `--muc-xa`, `--phan`, `--bong-cham`, `--bong-dem`, `--bong-than`, `--da`, `--ma-hong`, `--nhan-do`, `--nhan-vang`, tất cả số tạm); 1.2 lớp màu cảnh đo từ khung Veo kề bên, ghi vào bản chép dự án | cú cắt Veo ↔ HF không nhảy màu |
| B3 | 1.2 cũ, 1.5 luật 3 | "Trắng hồng phát sáng", "quầng sáng sau vật chính" | bỏ | cấm phát sáng kể cả khi nhấn |
| B4 | 1.4 luật 5 | khối màu phải có loang nước (đã bị 3.6 "thắng") | màu phẳng mờ có hạt giấy; không loang, không chuyển sắc, không quầng | sửa tận gốc, bỏ lớp "dòng này thắng dòng kia" |
| B5 | 1.5 → 1.4 | tối đa 2 tông nền mỗi video, chọn từ bảng | hai loại nền theo nội dung: sân khấu số liệu nền giấy; cảnh nơi chốn ảnh nền theo Veo. "Vẽ kín mép" chỉ cho cảnh nơi chốn | theo mục 4.4 bàn giao |
| B6 | 9 | "màu nước, ánh sáng chéo mềm, bụi sáng" | viết lại: chung nét, sáng, màu, dáng; nối cắt (cùng giờ, cùng trời, hoặc mở bằng ảnh nền Veo) ghi là **đang thử** | mục cũ tả style đã bỏ |
| B7 | 7 luật 4 | nền đổi ít nhất mỗi 3–4 ý | nền đổi theo 1.4; chống lặp dựa vào B/M/C | mâu thuẫn với luật nền, sửa tận gốc |
| C-a | 3.6.5 | bóng đổ mềm `blur(10px)`, đục 0,22; elip tiếp đất mờ | bóng phẳng mép gọn, `--bong-cham` đục 0,30 (tạm), không blur; trên ảnh nền lấy màu mặt tối của ảnh | bóng mờ là chuyển sắc, lộ ngay cạnh cảnh cel |
| C-b | 3.6.5 | hướng sáng trên-trái cả video | theo khối Veo kề bên, mặc định trên-trái, mỗi khối một hướng, ghi vào storyboard | cú cắt không đảo bóng |
| C-c | 3.6.7 (mới) | vật code chỉ tô một màu phẳng | vật có thể tích (thanh, hộp, bậc) có một mặt tối phẳng `--bong-cham` 0,28–0,32 (tạm); không áp cho đường, mũi tên, chữ, sticker | chữa lời chê "thô như vẽ bằng Paint" |
| C-d | 3, 3.1 (mới), 3.6.1 | vật thể 2–3 px, nhân vật 4–6 px; câu hỏi mở về nét dày cho vật biểu tượng | thứ bậc ba bậc: đậm (nhân vật, Xu, vật chính) 4–6 px; mảnh (đồ vật, khung, chỉ) 2,6–3,2 px; xa `--muc-xa` ~2 px | theo chuỗi Veo; trả lời câu 10.8 |
| C-e | 3.6.5 | hậu cảnh `blur(3px)` + nhạt 15–20% | chiều sâu bằng nét xám xanh và giảm tương phản; blur hậu cảnh chỉ khi storyboard ghi lý do. Tiền cảnh mờ giữ như cũ (dùng tiết kiệm) | Veo không làm mờ |
| C-f | 3.6.3 | mực bắt đầu `#2A2530`, mục tiêu "ngả màu, không đen tuyền" | giữ nguyên tắc khớp mực sticker; số bắt đầu `#0D0B08` / `#3B3936` (Tupperware); thêm `--muc-xa`; bỏ mục tiêu ngả màu; ghi số ba video làm quan sát | ba video đo ra gần đen; chuỗi Veo ghi near-black |
| C-g | 3.6.6 | năm điều, điều 5 "bóng mềm, hậu cảnh mờ hơn" | bảy điều: bóng phẳng; thứ bậc nét; mặt tối vật code; thêm phép cắt Veo ↔ HF | theo chuẩn mới |
| C-h | 3.6.7, 3.6.8 cũ | mục riêng video McDonald's (và Tupperware ở bản chép) nằm trong bản gốc | bản gốc không chứa mục riêng; 3.6.8 là mẫu mục riêng, bản chép dự án thêm "3.6.9 Riêng video <tên>". Mục riêng cũ cất ở `ban-luu` | bản gốc dùng được cho mọi video |
| D1 | 2.2 lớp B | từ khóa lớn trắng + quầng đỏ phát sáng | mực trên nền sáng, hoặc giấy trên mảng phẳng đỏ / nền tối; không quầng | cấm phát sáng |
| D2 | 2.1a (mới) | "chữ trong Veo là chữ AI bịa" | phân vai chữ: thông tin là HF, thế giới là ảnh; không lẫn; chữ thế giới sai chính tả thì sinh lại ảnh | mục 4.5 bàn giao |
| D3 | 5.2 M7 | "Bung sáng": vệt sáng, hạt sáng | "Bung nét": tia nét mực và mảng phẳng | giữ động tác cao trào, bỏ phát sáng |
| D3b | 5.3 C4, 2.4 | "Quét loang mực": vệt loang nước | "Quét mực": mảng phẳng mép cong | không loang nước |
| D3c | 5.1 | B1 "nền loang"; chung "hạt bụi/ánh sáng" | nền giấy hoặc ảnh nơi chốn; hậu cảnh bằng `--muc-xa` | không loang, không bụi sáng |
| D3d | 3.5 | tô "màu phẳng + bóng đổ 1 tầng" | một mặt sáng và một mặt tối phẳng, bóng chàm | cel |
| D3e | 10 | câu 3 (kết cấu loang, ánh sáng), câu 8 (nét dày vật biểu tượng) | gạch, ghi đã trả lời | |
| D3f | Phụ lục | — | ghi rõ khung cũ là clip 20/09; khung Veo mới cắt vào `khung-veo-moi/` | để đo lại số tạm |

### Xu

| # | Đổi gì | Từ | Sang | Vì sao |
|---|---|---|---|---|
| D4 | vị trí bản gốc | không ghi rõ, 6 bản chép giống hệt nhau (gốc thực tế ở `xu-hyperframes/xu-hyperframes/`) | `phongcach/xu/xu-character.js` + README | Chặng 0 cần một chỗ để chép |
| D4b | mặt tối (C3) | mảng tô phẳng, không mặt tối | mặt tối phẳng `#252D66` đục 0,28 (tạm): áo, chân phải, dưới tóc mái, phía phải mặt, tai phải, bóng đầu xuống cổ áo. `XU.svg({ light: "right" })` lật mặt tối; `XU.svg({ shade: false })` y hệt bản cũ. Tay chưa có mặt tối | cel như Veo. Dáng, tỉ lệ, biểu cảm, mực không đổi |
| D5 | tỉ lệ | Xu cao ~1,6 đầu (chibi Veo 2–2,5) | giữ | bản sắc kênh, không đổi dáng |
| D6 | font trong Xu | dấu `?` và `₫` dùng Baloo 2 (DESIGN 2.1 cấm font thứ hai) | ghi nhận, chưa sửa | lệch có sẵn, ngoài phạm vi đợt này |

Các bản chép Xu trong các dự án cũ (coca-5xu, ford-5do, mcdonalds, hop-nhua-tupperware, xu-chimmoi, xu-hyperframes) **không đổi**.

### Sổ tay CLAUDE.md

| Mục | Đổi |
|---|---|
| 0 | hai file style mới; `style.txt` thôi dùng; thêm CHANGELOG, `ban-luu`, bản gốc Xu |
| Chặng 0 | chép `style-veo.txt`, `style-sticker.txt`, Xu và DESIGN từ `phongcach` |
| 3 | ảnh nền nơi chốn theo chuỗi Veo, sân khấu số liệu nền giấy; chữ chia hai vai (thay "chữ và số không bao giờ nằm trong sticker") |
| 4 | tóm lược bút mực theo chuẩn mới; Xu bước 1 thêm mặt tối |
| 5 | khuôn prompt: nền tờ không trắng, không xanh; tên thương hiệu khi vật thật mang nó; chuỗi nào cho tờ nào; ảnh nền nơi chốn |
| 9 | luật mới do chủ kênh chốt 2026-09-30: **cất bản trước khi đổi** vào `ban-luu`, ghi CHANGELOG |
| 10 | theo dõi chuẩn Veo mới, phép cắt Fremont/NUMMI, bảng màu hằng số cần đo lại |

### Chưa làm trong đợt này

- **Phép thử Fremont và NUMMI**: chưa có dự án, kịch bản, clip Veo. Cần chủ kênh làm Chặng 0 và đặt 2–3 clip Veo mới vào.
- **Đo lại bảng màu hằng số** trên clip Veo mới (cùng lúc với phép thử).
- Các dự án cũ không sửa.
