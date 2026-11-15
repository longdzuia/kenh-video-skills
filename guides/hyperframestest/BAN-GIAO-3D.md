# Bàn giao nghiên cứu 3D trong HyperFrames (2026-10-25)

Claude Code soạn ngày 2026-10-25, để Antigravity nghiên cứu tiếp phần 3D. Đọc sau `LUAT-GOC.md` và sổ tay. Mọi thứ dưới đây là **phép thử, chưa phải luật kênh, chưa dùng trong video thật nào**. Số nào ghi "tạm" là tạm.

## 1. Đang ở đâu

- Từ 2026-10-21 đến 25, Claude Code và chủ kênh thử dựng 3D bằng three.js bên trong HyperFrames. Có 7 dự án thử, đều đã render.
- **Chủ kênh ưng nhất:** cảnh địa cầu trong vũ trụ (`thu-3d-style`, bản v2), tức quả cầu màu thật ép phẳng kiểu vẽ tay, viền phấn, bay qua mặt trăng rồi phóng vào Việt Nam. Bản này chủ kênh nói "ưng ý".
- **Chủ kênh chê:** khối hộp xếp tầng, cột chồng chi phí (cảnh khối trong `thu-3d`). "Tầng tầng lớp lớp với khối hộp nhìn chán lắm."
- **Chủ kênh khen:** hiệu ứng bản đồ ("làm khá tốt, đẹp nhất"), cảnh quy mô bằng vật thật, sa bàn.
- **Bản mới nhất:** `thu-3d-thienthach` (thiên thạch Chicxulub, góc nhìn khủng long). Đã gửi chủ kênh, chưa có nhận xét.

## 2. Bảy dự án thử

Tất cả nằm ngay trong workspace. Mỗi dự án có `GHI-CHU.md` riêng: số liệu, nguồn, chỗ lệch DESIGN.

| Dự án | Nội dung | Bản render | Chủ kênh nói |
|---|---|---|---|
| `thu-3d` | địa cầu phóng vào Việt Nam (có Hoàng Sa, Trường Sa); khối tầng, tháp | `renders\thu-3d_v1.mp4` | bản đồ "bất ngờ", khối hộp chán |
| `thu-3d-vantai` | cung ngoại thương Mỹ–EU; tàu Thượng Hải → Rotterdam qua Malacca, Suez, vòng Mũi Hảo Vọng khi Biển Đỏ bị chặn; Hormuz | `renders\thu-3d-vantai_v1.mp4` | "hay đấy" |
| `thu-3d-vatly` | tàu lượn trên giá Bitcoin 2017–2018 thật; bảng Galton 800 bi | `renders\thu-3d-vatly_v2.mp4` (v1 lỗi mất bi) | chưa nhận xét riêng |
| `thu-3d-quymo` | GDP Việt Nam 2024 bằng cọc tiền 500.000đ phủ kín sân bóng; sa bàn vòng tuần hoàn của tiền | `renders\thu-3d-quymo_v1.mp4` | "cái 3D này hay đấy" |
| `thu-3d-style` | v1: địa cầu và Galton theo bút mực, nền giấy, cel; **v2: địa cầu trong vũ trụ, màu thật** | `renders\thu-3d-style_v1.mp4`, **`renders\thu-3d-style_v2-vutru.mp4`** | v1 "cũng đẹp"; **v2 "ưng ý"** |
| `thu-3d-thienthach` | thiên thạch lao tới; góc nhìn khủng long (nấm lửa, tường bụi); Trái Đất sau va chạm | `renders\thu-3d-thienthach_v1.mp4` | chưa nhận xét |

Mã nguồn: `index.html` của từng dự án, mỗi file là một trang. `thu-3d-style\ban-v1-giay.html` là bản v1 (nền giấy) giữ lại.

**Mẫu để chép khi làm cảnh mới:**
- `thu-3d-style\index.html` cho bản đồ, vũ trụ;
- `thu-3d-thienthach\index.html` cho nhiều cảnh, lửa, mặt đất;
- `thu-3d-style\ban-v1-giay.html` cho bút mực trên nền giấy.

## 3. Công thức kỹ thuật đã chạy được trên máy này

### 3.1 Khung composition 3D

- three.js 0.181.2 nạp bằng importmap từ jsDelivr (`three` và `three/addons/`). GSAP 3.14.2 nạp thường.
- HyperFrames có sẵn bộ nối `three`: mỗi lần tua nó đặt `window.__hfThreeTime` và phát sự kiện `hf-seek` (`e.detail.time`). Mọi cảnh vẽ lại trong một hàm `renderAt(t)` gọi từ `hf-seek`, không dùng `requestAnimationFrame`.
- Root phải có `data-duration`. Phải đăng ký một timeline GSAP rỗng `window.__timelines["main"]` dài đúng bằng `data-duration`; thiếu thì lint báo `missing_timeline_registry`.
- Dựng nặng (đọc dữ liệu, vẽ canvas, ép màu): khai `window.__hf.buildReady["<tên>"]` là một Promise ngay trong `<script>` thường ở `<head>`. Module three xong việc thì gọi resolve, kể cả khi lỗi (đặt trong `finally`).
- Dữ liệu và ảnh để trong `assets\`, đọc bằng `fetch` hoặc `Image` lúc dựng, không tải mạng lúc tua.
- **InstancedMesh, LineSegments2 đổi vị trí theo thời gian phải đặt `frustumCulled = false`.** Thiếu dòng này, render nhiều tiến trình mất hết bi Galton (v1 của `thu-3d-vatly`), trong khi snapshot vẫn thấy.
- Một renderer cho nhiều cảnh: mỗi cảnh một `THREE.Scene`, chọn cảnh theo `t`.
- Nhãn HTML gắn vào điểm 3D: `vector.project(camera)` ra tọa độ px mỗi khung. Điểm ở mặt khuất của quả cầu thì ẩn (tích vô hướng pháp tuyến với hướng về máy quay).

### 3.2 Đổ sáng cel (DESIGN 3.6.5, 3.6.7)

- `MeshToonMaterial` với `gradientMap` là DataTexture 2 điểm [0, 255], lọc `NearestFilter`: mặt hướng sáng và mặt khuất là hai mảng phẳng.
- `AmbientLight` màu `(1 − α + α·màu bóng)`, cường độ π. `DirectionalLight` màu `1 − ambient`, cường độ π.
  - Kết quả: mặt sáng giữ đúng màu vật, mặt tối bằng màu vật nhân lớp bóng có độ đục α, đúng như lớp multiply trong DESIGN.
  - Bóng đổ (shadow map) rơi vào vùng chỉ có ambient nên cùng màu mặt tối.
  - Hàm mẫu `denCel(scene, mauBong, alpha)` trong `thu-3d-thienthach\index.html`.
- α tạm:
  - 0,36 với chàm `#252D66` trên nền sáng (DESIGN ghi 0,30; 3D cần đậm hơn chút);
  - 0,55 với xanh đêm `#0e1523` trên nền vũ trụ.
- `renderer.shadowMap.type = PCFShadowMap` (mép gọn, không mềm). Vật liệu có `polygonOffset` để nét mực không bị mặt nuốt.
- Hướng sáng gắn theo máy quay: từ trên-trái, bóng lệch xuống-phải.

### 3.3 Nét mực

- **Đường thẳng dày theo px:** `Line2`, `LineSegments2` (three/addons), nhớ đặt `material.resolution.set(1920, 1080)`. Vẽ dần bằng `geometry.instanceCount`.
- **Viền mép quả cầu:** tính hình học mỗi khung (vòng tròn chạm mắt nhìn), vẽ bằng `Line2`, có gợn rất nhẹ cố định. Hàm `vienCau`, `capNhatVien`.
  - Nền sáng: mực `#161616`, 6 px.
  - Nền tối: phấn `#ece6da`, 5 px (DESIGN 3.6.3).
- **Viền vật tròn, đá, cây:** khối lật mặt (cùng geometry, `BackSide`, màu mực, phóng 1,05–1,3).
- **Viền hộp:** `EdgesGeometry` chia nhỏ, run nhẹ theo hạt giống, hai đầu vượt góc (hàm `vienCanh` ở `ban-v1-giay.html`).
- **Chưa làm:** nét đậm nhạt, đầu vuốt nhọn (DESIGN 3.6.1). Nét 3D đang đều bề dày.

### 3.4 Thẻ chữ của kênh

- Lớp `.chip` chép từ `duong-seoul-p2`: nền trắng, viền mực 6–7 px, bo 24 px, Be Vietnam Pro 800, chữ in hoa; `.do`, `.vang` cho thẻ nhấn.
- Đường chỉ là `<line>` SVG cùng chấm ở điểm gắn, cập nhật mỗi khung.
- Hạt giấy: lớp `.hat` (`hat-giay.png` multiply 8%) như các video gần đây.

### 3.5 Bản đồ, địa cầu

- **Dữ liệu biên giới:** `assets\geo\countries-10m.json` (world-atlas 2.0.2, Natural Earth 1:10m, phạm vi công cộng) cùng `assets\lib\topojson-client.min.js`.
- **Vẽ lên canvas phẳng** theo kinh vĩ độ rồi bọc lên `SphereGeometry`. Hàm `v3(lon, lat, r)` khớp UV của SphereGeometry.
  - Vòng vắt qua kinh tuyến 180 (Nga, Fiji, Nam Cực) phải nối lại rồi vẽ ba lần lệch ±360°.
- **Phóng gần mà vẫn sắc:** thêm "mảnh nét cao" cho riêng một vùng, là `SphereGeometry` với `phiStart/phiLength/thetaStart/thetaLength` và canvas riêng 100–160 px mỗi độ.
- **Màu thật (bản chủ kênh ưng):**
  - nguồn: ảnh NASA Blue Marble Next Generation, có địa hình và độ sâu biển, tháng 8/2004, 5400×2700, phạm vi công cộng (`thu-3d-style\assets\anh\`);
  - làm mờ nhẹ rồi ép về mảng phẳng: đất 8 màu theo màu gần nhất, biển 3 màu theo độ sáng (độ sâu);
  - ranh đất và biển lấy theo Natural Earth để khớp nét bờ mực;
  - hàm `banDoToanCau` / `tamBanDo`, `epMauPhang`.
- **Chủ quyền (sổ tay mục 3):** Natural Earth gán 7 mảnh đảo Hoàng Sa cho Trung Quốc (id `156`) và để Trường Sa thành mục riêng `Spratly Is.` (không có id).
  - Code tách các mảnh đó: mảnh của 156 có tâm trong hộp kinh độ 110,5–113,5, vĩ độ 15–17,6; và toàn bộ `Spratly Is.`.
  - Rồi vẽ chấm đỏ, khung nét đứt, nhãn "QUẦN ĐẢO HOÀNG SA / VIỆT NAM", "QUẦN ĐẢO TRƯỜNG SA / VIỆT NAM", "BIỂN ĐÔNG".
  - **Mọi cảnh có Biển Đông đều phải giữ phần này.**
- **Tuyến tàu biển:** chuỗi điểm mốc đặt tay theo luồng thật, làm mềm Catmull-Rom rồi ép lên mặt cầu. Đã soát không lấn đất ở Malacca, Biển Đỏ, Suez, Hormuz. Đây là tuyến minh họa, không phải dữ liệu AIS.

### 3.6 Máy quay, tất định, vật lý

- **Máy quay** đi theo các mốc (thời điểm, điểm nhìn, khoảng cách, góc ngẩng, phương vị), làm mềm bằng ease in-out. Khoảng cách nội suy theo log nên bay từ xa vào thấy đều.
- **Bám theo vật:** lấy trung bình vị trí vật ở vài mốc quanh `t` cho khỏi giật.
- **Ngẫu nhiên:** chỉ dùng `mulberry32(seed)`. Nhiễu giá trị 2D tự viết (`taoNhieu`). Không `Math.random`, không `Date`.
- **Kiểm tất định:** snapshot cùng giây hai lần rồi so mã băm file. Đã đạt ở `thu-3d-style`.
- **Bảng Galton không dùng động cơ vật lý:** đường bay từng viên tính sẵn. Bi không va nhau khi bay.
- **Tàu lượn:** kéo xích tới đỉnh, sau đó tốc độ theo bảo toàn năng lượng, tra bảng tính sẵn.

### 3.7 Lệnh và thời gian trên máy này

- Theo `LUAT-GOC.md` mục 4: `HYPERFRAMES_BROWSER_PATH`, `--describe false`, `npx.cmd`, bản ghim `hyperframes@0.8.183` trong `package.json` của các dự án thử.
- Snapshot cảnh 3D nặng thêm `PRODUCER_PAGE_NAVIGATION_TIMEOUT_MS=180000`.
- Render các bản 3D bằng `-w 2`, GPU phần cứng: 20–46 s video mất khoảng 2–4 phút.
- Đọc khung từ MP4 để soát: `ffmpeg -ss <giây> -i <mp4> -frames:v 1 ...`.

## 4. Nguồn dữ liệu đã dùng

- **Biên giới:** Natural Earth qua world-atlas (phạm vi công cộng).
- **Ảnh vệ tinh:** NASA Blue Marble NG (phạm vi công cộng). Ghi công ở góc dưới.
- **Giá Bitcoin:** API công khai Coinbase Exchange (`/products/BTC-USD/candles`), không cần tài khoản. Stooq đòi xác minh trình duyệt, không lách.
- **Số liệu tạm, chưa kiểm sâu** (chi tiết và đường dẫn trong `GHI-CHU.md` từng dự án):
  - thương mại hàng hóa Mỹ–EU 2024 (nguồn thứ cấp);
  - Hormuz khoảng 20 triệu thùng/ngày (EIA);
  - Thượng Hải → Rotterdam qua Suez hay vòng châu Phi (porteconomicsmanagement.org);
  - GDP Việt Nam 2024: 11.511,9 nghìn tỷ đồng (Tổng cục Thống kê ước tính);
  - tờ 500.000đ 152 × 65 mm (NHNN); cọc 100 tờ dày 1 cm là giả định;
  - Chicxulub: 66 triệu năm, đá khoảng 10 km, hố khoảng 180 km, khoảng 3/4 số loài (kiến thức phổ thông, chưa dẫn nguồn).

## 5. Chỗ lệch DESIGN hay sổ tay, đang chờ chủ kênh

- ~~**Vành khí quyển xanh nhạt** quanh địa cầu (`thu-3d-style` v2): vành phẳng 7 px, không phát sáng, nhưng DESIGN cấm quầng. Bỏ thì xóa dòng `vanhKhi`.~~ Đã gỡ 2026-10-28: DESIGN không còn cấm quầng (sổ tay mục 4, DESIGN 3.7); vành là mảng phẳng nên giữ được.
- ~~**Chớp trắng phủ kín khung** lúc va chạm (`thu-3d-thienthach`).~~ Đã gỡ 2026-10-28: chớp trắng lúc va chạm nay được dùng (DESIGN 3.7).
- **Độ đục mặt tối** 0,36 và 0,55 (tạm).
- **Nét đều bề dày**, chưa đậm nhạt (3.6.1).
- **Cây, đồi, khủng long, người, nhà trên sa bàn dựng bằng khối hình học.** Sổ tay mục 3 nói đó là việc của ảnh. Video thật phải sinh sticker và ảnh nền bằng Flow; phần chuyển động giữ được.
- **Thiên thạch phóng to so với tỉ lệ thật; bản đồ là Trái Đất ngày nay.** Cả hai đã ghi trên hình.

## 6. Hướng nghiên cứu còn mở

Từ trao đổi với chủ kênh, chưa ai làm:
- nét đậm nhạt, đầu vuốt nhọn cho nét 3D (phần duy nhất của DESIGN 3.6 chưa áp);
- tách bộ vật liệu 3D dùng chung (cel, nét mực, thẻ chữ, địa cầu) thành một file, để video sau chỉ gọi vào; hiện mỗi dự án chép mã;
- tách rời một món đồ ra từng phần: ly trà sữa 35.000đ, hay điện thoại kèm nước sản xuất linh kiện;
- đám đông bằng hạt (100.000 hạt làm dân số), nhớ quan sát "ký hiệu thay người bị chê" ở sổ tay mục 10;
- bản đồ: tô dần từng nước theo năm; nhiều luồng xuất khẩu của Việt Nam cùng lúc, độ dày theo sản lượng;
- thiên thạch bản thật: đổi khối tạm sang sticker, ảnh nền; có thể làm bản "Trái Đất vỡ đôi" nếu chủ kênh muốn (đã nói rõ là không đúng sự kiện);
- ngoài 3D: plugin GSAP miễn phí (DrawSVG, MorphSVG, MotionPath), biểu đồ kinh tế "ăn theo nhau" (cung–cầu), vật lý Rapier 2D thật cho sticker, Rive cho Xu (dài hạn, chưa được giao).

## 7. File rác (để chủ kênh tự xóa, không tự xóa)

- `thu-3d-vatly\renders\thu-3d-vatly_v1.mp4`: bản lỗi mất bi.
- `thu-3d-style\assets\anh\blue-marble-topo-bathy-200412-5400.jpg`: ảnh tháng 12, không dùng.
- Thư mục `.hyperframes\artifacts\snapshots\` trong các dự án thử: ảnh chụp soát.

## 8. Hai bên làm song song

> **Hết hiệu lực từ 2026-10-30.** Các dự án 3D của Antigravity đã chép về `C:\hyperframestest`; từ nay cả hai tác nhân làm chung ở đây (sổ tay mục 0). Phần dưới giữ để biết lịch sử.


- Workspace của Antigravity là `C:\hyperframestest - antigravity`, bản chép cả xưởng ngày 24/10, thêm `thu-3d-thienthach` chép ngày 25/10.
- Claude Code tiếp tục ở `C:\hyperframestest`.
- Hai bản 3D lúc bàn giao giống nhau từng file; từ đây hai bên đi riêng. Muốn gộp kết quả thì chép có ghi chép vào `GHI-CHU.md` của dự án, không chép đè.
- Đọc sổ tay, DESIGN, skill ở `C:\hyperframestest` và `%USERPROFILE%\.claude\skills` thì được; **ghi** chỉ trong workspace `C:\hyperframestest - antigravity`.

## 9. Nhật ký mở rộng 3D tại Antigravity (2026-10-26)

### 9.1 Bốn dự án thử mới

| Dự án | Nội dung | Bản render | Điểm kỹ thuật chính |
|---|---|---|---|
| `thu-3d-thienthach-v2` | Bản nâng cấp thiên thạch Chicxulub: 3D FBM plasma shader, miệng hố lún biến dạng đỉnh 3D, nấm lửa cuộn xoáy | `renders\thu-3d-thienthach-v2_v1.mp4` | Shader lửa/khói 3D FBM + Kuwahara-style cel steps, viền mực khóa theo pixel (`taoVienPixel`) |
| `thu-3d-chernobyl` | Giải phẫu thảm họa hạt nhân Chernobyl 1986: cắt lớp lõi lò RBMK-1000, vụ nổ hất tung nắp chắn Elena 2.000 tấn + cột tia ion hóa, luồng gió phóng xạ Cesium-137 khắp châu Âu | `renders\thu-3d-chernobyl_v1.mp4` | Vật liệu Sơn bột Gouache, cụm 180 thanh nhiên liệu/điều khiển (`InstancedMesh`), địa cầu châu Âu có nhãn Thụy Điển phát hiện đầu tiên |
| `thu-3d-hoden` | Giải phẫu Hố đen Siêu khối lượng Gargantua & Tàu thăm dò `Endurance-X` 12 mô-đun, Sự kiện Xé toạc Ngôi sao (TDE / Spaghettification) và Tia phản lực Quasar 99,9% $c$ xuyên Thiên hà Xoắn ốc 3D | `renders\thu-3d-hoden_v1.mp4` | Shader **Sơn bột Gouache + Gạch bóng Bút mực (Cross-Hatching) + Rãnh tấm ghép Cơ khí**, Thấu kính Hấp dẫn GLSL đồng bộ tâm 3D, ngôi sao Voronoi kéo giãn đỉnh |
| `thu-3d-toba` | Siêu núi lửa Toba (74.000 năm trước — Sumatra): Địa cầu phóng xuống Đông Nam Á (giữ Hoàng Sa, Trường Sa) & cột nấm bình lưu Toba; Sa bàn 2.5D đàn voi cổ đại Stegodon, hổ răng kiếm & bộ lạc Homo sapiens giữ lửa; Địa cầu Mùa đông núi lửa 6 năm & Nút cổ chai di truyền (3.000–10.000 người sống sót) | `renders\thu-3d-toba_v1.mp4` | Kế thừa 100% **5 bí quyết Quả Địa Cầu `thu-3d-style` v2** cho Cảnh 1 & 3 + **Sa bàn Tranh cắt lớp 2.5D có khớp động (`rung-toba-25d.js`)** cho sinh vật sống ở Cảnh 2 |

### 9.2 Công thức khử cảm giác "nhựa" (Plastic 3D) cho khối cơ khí & vũ trụ (`thu-3d-hoden\assets\lib\shader-ho-den.js`)

1. **Vật liệu Sơn bột Gouache + Gạch bóng Bút mực + Rãnh Cơ khí (`taoVatLieuSonMuc`):**
   - Thay `MeshToonMaterial` trơn bằng GLSL Shader lượng tử hóa ánh sáng 4 bậc kèm nhiễu hạt cọ 3D (`fbm3`).
   - **Gạch bóng chéo bằng bút mực (Procedural Cross-Hatching):** tự động kẻ các đường nét mực đen `#161514` đan chéo theo tọa độ màn hình trong vùng tối và nửa tối.
   - **Rãnh tấm ghép cơ khí (`uPanelScale`):** dùng đạo hàm không gian màn hình (`fwidth`) để kẻ đường ghép tấm kim loại và viền sáng vát cạnh trên thân tàu vũ trụ, lò phản ứng mà không cần vẽ UV texture ngoài.
2. **Đồng bộ màn Thấu kính Hấp dẫn (Full-screen Quad) với tọa độ 3D (`dongBoThauKinhHoDen`):**
   - Chiếu tâm Hố đen 3D và một điểm trên mặt cầu Chân trời Sự kiện qua `camera` mỗi khung hình để cập nhật `uHoleCenter` và `uHoleRadius` trong không gian màn hình, giúp Vòng Einstein và vòm Đĩa bồi tụ bị bẻ cong luôn khớp 100% với vật thể 3D khi máy quay di chuyển.
3. **Viền mực cho vật thể biến dạng đỉnh (Vertex Deformation) hoặc cắt tiến độ UV (`discard`):**
   - Không gắn mesh con `taoVienPixel` (`THREE.BackSide`) lên `InstancedMesh` (vì mesh con không có `instanceMatrix`) hoặc lên mesh có Vertex Shader biến dạng mạnh/cắt `discard` theo `vUv` (vì bản sao mặt lưng sẽ để lộ bóng đen ở phần chưa biến dạng/đã `discard`).
   - Thay bằng viền mực silhouette tính trực tiếp trong Fragment Shader: `float edgeOutline = 1.0 - smoothstep(0.18, 0.28, abs(dot(N, V)));`.

### 9.3 Công thức kết hợp Địa cầu `thu-3d-style` v2 + Sa bàn 2.5D có Khớp động cho sinh vật sống (`thu-3d-toba`)

1. **Giữ nguyên 5 bí quyết của `thu-3d-style` v2 cho mọi cảnh Địa cầu (`dia-cau-toba.js`):**
   - Dùng dữ liệu thật (`NASA Blue Marble 5400×2700` + `Natural Earth 1:10m`), lượng tử hóa từng pixel qua `epMauPhang` về đúng 8 màu đất + 3 màu biển phẳng (hoặc bảng màu `DAT_MUA_DONG` cho cảnh băng giá/mùa đông núi lửa).
   - Chia sẻ `CanvasTexture` toàn cầu giữa các cảnh (`topoData.texToanCauXanh`) để thời gian dựng trang ban đầu luôn nhanh (`< 1,5 s`).
   - Khi đặt cụm vật thể 3D (như cột nấm núi lửa `tobaGroup`) lên bề mặt địa cầu tại tọa độ `(lon, lat)`, **bắt buộc dùng hệ cơ sở thuận tay phải (`det = +1`)**: `makeBasis(fr.east, fr.up, fr.north.clone().negate())`. Nếu dùng `(east, up, north)` sẽ bị `det = -1` làm lật mặt pháp tuyến và đảo ngược `BackSide` viền mực.
2. **Sa bàn Cắt lớp 2.5D có Khớp động (`rung-toba-25d.js`) cho cảnh có sinh vật sống & con người:**
   - Tuyệt đối không ghép khối trụ/hộp/cầu 3D thô để làm thú hay người. Thay vào đó, vẽ từng bộ phận (thân, đầu, vòi, tai, 4 chân, cánh chim, cánh tay cầm đuốc) bằng mảng màu phẳng Gouache + viền mực `#161616` trên `CanvasTexture` rồi gắn lên các `PlaneGeometry` có tâm xoay khớp nối (`pivotY`):
     - Dịch tâm xoay chuẩn theo trục Y của Three.js: `geo.translate(0, (pivotY - 0.5) * h3D, 0)` (với `pivotY` tính từ đỉnh bức vẽ Canvas `0.0` xuống đáy `1.0`).
     - Để khớp đùi/vai của thú 4 chân (voi Stegodon, hổ răng kiếm) xoay mượt mà không lộ vòng tròn mực đen trên thân: tô kín bầu đùi cùng màu thân, nhưng **chỉ viền mực 2 cạnh ống chân và bàn chân** (để hở phần cung tròn đỉnh đùi cho tiệp liền 100% vào mảng màu thân).



> Gộp ngày 2026-10-30 từ bản ở `C:\hyperframestest - antigravity\antigravity\BAN-GIAO-3D.md` (đợt dọn mạch). Các dự án nhắc ở mục này nay đã có bản chép ở `C:\hyperframestest\`.
