# Ghi chép dựng phác — Món #3: Hệ gia trưởng (2026-11-25)

Bước 5 của chặng nội dung (`CLAUDE.md` mục 2a): dựng phác hoàn chỉnh món đinh đầu tiên theo khung Tập 1 mới (bảng tier 2 chữ, chiến lược test cuốn chiếu 1 món hoàn chỉnh).

- **Video dựng phác:** `renders\thu-he-gia-truong_v1.mp4` (1920×1080, 16:9, 30 fps, **102,08 s**).
- **Bảng kịch bản có ảnh từng nhịp:** mở `XEM-BANG.html` bằng trình duyệt.
- **Giọng đọc tạm:** `edge-tts` miễn phí 100% (`.work\sinh-giong.py`), chuẩn hóa mức âm `-16 LUFS`, nén khoảng ngắt thừa giữa câu kiểu máy đọc, **cắt sạch đuôi xuống 2–5 ms** ở nhịp 10, 12, 14, 15 để nhịp xen nhảy phựt cướp lời ngay lập tức và nhịp 16 phanh gấp về im tuyệt đối 1,00 s.

## 1. Phân màu giọng & tốc độ từng vai

| Vai | Giọng `edge-tts` | Tốc độ (`rate`) & Cao độ (`pitch`) | Ghi chú xử lý |
|---|---|---|---|
| **Mèo** (dẫn chính) | `vi-VN-NamMinhNeural` (nam trẻ) | Nhịp 1, 3, 4, 18, 20: `+2%`..`+4%`, `+0Hz`<br>Nhịp 7 (rụt rè): `-12%`, `-2Hz`<br>Nhịp 10 → 12 → 14: **`+10%` → `+20%` → `+30%`** (`+0`→`+4Hz`)<br>Nhịp 17 (kiệt sức): **`-14%`**, `-6Hz`<br>Nhịp 22 (lảng nhanh): `+7%`, `+2Hz` | Nhịp 10, 12, 14 cắt sát đuôi 0 ms pad (còn 2–5 ms); nhịp 22 giữ 0,50 s khựng đầu câu + chèn huýt sáo vào khoảng nghỉ giữa câu. |
| **Hệ gia trưởng** (vai phụ) | `vi-VN-HoaiMyNeural` (nữ sắc) | Nhịp 5 (hào hứng): `+16%`, `+6Hz`<br>Nhịp 8 (đổi style gắt): `+18%`, `+10Hz`<br>Nhịp 11 (cắt ngang + loa): `+24%`, `+12Hz`<br>Nhịp 13 (cực nhanh soi mói): `+28%`, `+14Hz`<br>Nhịp 15 (**đổi ngọt xớt**): **`-2%`**, `+16Hz` | Nhịp 8, 11, 13 tăng dải trung-cao + nén nhẹ để sắc/gắt; nhịp 15 giảm dải chói 4,5 kHz và cắt sát ngay sau chữ `"nhé!"`. |
| **Bạn ngoài khung** (nhịp 21) | `vi-VN-NamMinhNeural` (đổi màu rõ) | `+10%`, **`+22Hz`** | Lọc dải 220–4800 Hz + vang phòng nhẹ (`aecho`) tạo cảm giác tiếng vọng từ ngoài khung hình. |

## 2. Bảng đối chiếu mốc giây thực tế (22 nhịp)

| # | Loại | Vai | Ước (s) | Thực (s) | Lệch (s) | Bắt đầu → Kết thúc | Audio thoại | Tốc độ / Ghi chú |
|---:|---|---|---:|---:|---:|---|---|---|
| 1 | Lời | Mèo | 6,00 | 5,86 | -0,14 | `0:00.00 → 0:05.86` | `0.15 → 5.74` (5,59 s) | `+2%`, tự nhiên |
| 2 | **Lặng** | — | **2,00** | **2,00** | **0,00** | `0:05.86 → 0:07.86` | — | **Giữ nguyên 2,00 s** (lật thẻ + ting) |
| 3 | Lời | Mèo | 5,50 | 6,02 | +0,52 | `0:07.86 → 0:13.89` | `7.96 → 13.76` (5,80 s) | `+3%`, gõ que cốc cốc |
| 4 | Lời | Mèo | 7,00 | 7,14 | +0,14 | `0:13.89 → 0:21.03` | `13.99 → 20.95` (6,96 s) | `+2%`, chữ đề bài khớp lời |
| 5 | Xen | Hệ gia trưởng | 6,50 | 7,01 | +0,51 | `0:21.03 → 0:28.04` | `21.25 → 27.96` (6,71 s) | `+16%`, đập bàn tắt nhạc phụt |
| 6 | **Lặng** | — | **2,50** | **2,50** | **0,00** | `0:28.04 → 0:30.54` | — | **Giữ nguyên 2,50 s** (im nhạc, chỉ `rột... rột...` + quạt) |
| 7 | Lời | Mèo | 4,00 | 4,62 | +0,62 | `0:30.54 → 0:35.16` | `30.64 → 35.10` (4,46 s) | `-12%`, rụt rè ngập ngừng |
| 8 | Xen | Hệ gia trưởng | 3,50 | 4,05 | +0,55 | `0:35.16 → 0:39.20` | `35.30 → 39.17` (3,87 s) | `+18%`, đổi style cổ động/manga + sét |
| 9 | **Lặng** | — | **1,50** | **1,50** | **0,00** | `0:39.20 → 0:40.70` | — | **Giữ nguyên 1,50 s** (cắt sạch nhạc, 1 tiếng *tạch*) |
| 10 | Lời | Mèo | 6,00 | 6,87 | +0,87 | `0:40.70 → 0:47.58` | `40.78 → 47.57` (6,79 s) | **`+10%`**, cắt sạch đuôi (2 ms) → B11 chen thẳng |
| 11 | Xen | Hệ gia trưởng | 1,50 | 1,30 | -0,20 | `0:47.58 → 0:48.88` | `47.58 → 48.84` (1,26 s) | `+24%`, cướp lời ngay lập tức |
| 12 | Lời | Mèo | 5,50 | 5,69 | +0,19 | `0:48.88 → 0:54.57` | `48.90 → 54.57` (5,67 s) | **`+20%`**, comment Word mờ, cắt sạch đuôi (5 ms) |
| 13 | Xen | Hệ gia trưởng | 2,50 | 3,18 | +0,68 | `0:54.57 → 0:57.74` | `54.57 → 57.71` (3,14 s) | `+28%`, cực nhanh soi mói, cướp lời |
| 14 | Lời | Mèo | 7,50 | 6,55 | -0,95 | `0:57.74 → 1:04.30` | `57.76 → 64.29` (6,53 s) | **`+30%`**, mưa Zalo mờ, cắt sạch đuôi (3 ms) |
| 15 | Xen | Hệ gia trưởng | 3,50 | 4,25 | +0,75 | `1:04.30 → 1:08.55` | `64.30 → 68.55` (4,25 s) | **`-2%` ngọt xớt**, cắt phựt 100% sau `"nhé!"` |
| 16 | **Lặng** | — | **2,00** | **2,00** | **0,00** | `1:08.55 → 1:10.55` | — | **Giữ nguyên 2,00 s** (**im tuyệt đối 1,00 s** + `phù...`) |
| 17 | Lời | Mèo | 6,50 | 7,13 | +0,63 | `1:10.55 → 1:17.67` | `70.73 → 77.52` (6,79 s) | **`-14%`**, rã rời + 1 nốt đàn trầm |
| 18 | Lời | Mèo | 7,00 | 6,47 | -0,53 | `1:17.67 → 1:24.14` | `77.81 → 84.06` (6,25 s) | `+2%`, kéo thẻ nhử sát ô A |
| 19 | **Lặng** | — | **1,50** | **1,50** | **0,00** | `1:24.14 → 1:25.64` | — | **Giữ nguyên 1,50 s** (xước đĩa tắt nhạc + liếc xéo) |
| 20 | Lời | Mèo | 5,50 | 6,26 | +0,76 | `1:25.64 → 1:31.91` | `85.74 → 91.70` (5,96 s) | `+4%`, hất thẻ rơi bộp ô B |
| 21 | Xen | Bạn | 3,50 | 3,91 | +0,41 | `1:31.91 → 1:35.82` | `92.03 → 95.74` (3,71 s) | `+10%`, `+22Hz` vọng ngoài khung |
| 22 | Lời | Mèo | 4,50 | 6,26 | +1,76 | `1:35.82 → 1:42.08` | `96.32 → 101.43` (5,11 s) | `+7%`, khựng 0,5 s + huýt sáo + cốc cốc cuối |
| **Tổng** | | | **95,50** | **102,08** | **+6,58** | `0:00.00 → 1:42.08` | | Lệch tổng +6,9%, 5 nhịp Lặng chuẩn 100% |

## 3. Lưu ý về TTS & độ lệch thời lượng (để chỉnh trước khi thu giọng thật)

1. **Nhịp 22 (+1,76 s so với ước 4,5 s):** Câu thoại có 21 từ cộng thêm 0,50 s khựng đầu nhịp, 0,74 s huýt sáo giữa câu và 0,52 s gõ que kết món nên thực tế dài **6,26 s** (nghe vừa tai, không bị vội). Nếu muốn gọn về ~5 s khi thu thật thì gộp huýt sáo ngắn còn ~0,4 s và đọc nhanh hơn ở vế `"À ờ thì..."`.
2. **Nhịp 14 (-0,95 s so với ước 7,5 s):** Ở tốc độ `+30%` câu dài 43 từ lướt hết trong **6,55 s** — tạo cảm giác dồn dập nghẹt thở rất tốt, nhưng khi thu giọng thật chủ kênh nên kiểm xem có cần giảm nhẹ tốc độ một chút để chữ `"1 giờ sáng"` / `"2 giờ đêm"` vẫn nghe rõ từng âm tiết.
3. **Nhịp 13 (`Arial`, `Times New Roman`, +0,68 s):** Giọng `vi-VN-HoaiMyNeural` đọc từ tiếng Anh ở tốc độ `+28%` hơi dính nhẹ (`Arial` và `Times New Roman` có độ máy nhẹ, và nhịp dài 3,18 s so với ước 2,5 s). Khi thu thật nói nhanh tự nhiên 2 tên font này sẽ rất buồn cười và gọn hơn (~2,5 s).
4. **Nhịp 10 (+0,87 s) & Nhịp 4 (`Word`):** Ở nhịp 4 giọng `NamMinhNeural` phát âm chữ `"Word"` hơi nặng âm Việt (gần giống `"quật"`), còn `"slide"` rõ. Ở nhịp 10 đã đổi chữ đọc thành `"tác tên"` thay vì `"tag tên"` để tránh máy đọc sai, nhưng 35 từ ở `+10%` vẫn dài 6,87 s so với ước 6,0 s — chấp nhận được để lấy đà từ từ trước khi tăng tốc ở nhịp 12 và 14.
5. **Nhịp 15 (+0,75 s):** Vì chuyển về tốc độ vừa (`-2%`) với giọng ngọt để tương phản mạnh với nhịp 14 (`+30%`), câu kéo 4,25 s (ước 3,5 s). Hiệu ứng phanh gấp sang 1 giây im tuyệt đối ở nhịp 16 ăn nhịp rất đã.

## 4. Danh sách hình TẠM cần sinh thật sau khi duyệt nhịp

| Nhịp | Hiện đang dùng (code SVG vẽ tay / tái sử dụng) | Cần sinh khi chốt bước 6 |
|---|---|---|
| B2, B3, B18, B20 | Chân dung Hệ gia trưởng vẽ SVG phác (`phac-ve.js`) | Tờ gốc nhân vật **Hệ gia trưởng** (`style-nguoi.txt`: kính cận, nghiêm túc, cầm bút đỏ) |
| B4 | Quán cà phê 4 sinh viên vẽ SVG + `M0-meo-goc.png` | Cảnh quán cà phê 4 sinh viên ngồi cười nói (`style-nen.txt` + nhân vật) |
| B5 | Hệ gia trưởng đập bàn SVG + 3 icon code | Tư thế Hệ gia trưởng đập rầm hai tay xuống bàn, kính lóe sáng |
| B6 | Góc rộng 3 đứa ngồi đơ SVG + `M0-meo-goc.png` | Góc rộng 3 bạn (gồm Mèo) mặt đơ cứng, 1 bạn ngậm ống hút ly trà đá cạn |
| B7 | `M0-meo-goc.png` + tay giơ & mồ hôi SVG | Mèo rụt rè giơ tay ngang vai, cười gượng (sửa từ tờ gốc Mèo) |
| B8 | Đổi style cổ động/manga vẽ SVG nét đậm | Tranh đổi style cổ động/manga gắt: Hệ gia trưởng chỉ thẳng tay màn hình, kính lóe tia sét |
| B9 | `M0-meo-goc.png` + lớp tai cụp SVG | (Tùy chọn) Mèo mặt lì cụp hai tai xuống |
| B11, B13, B15 | Đầu Hệ gia trưởng vẽ SVG (loa / kính lúp / thả ngược cười hiền) | 3 biểu cảm Hệ gia trưởng (quát loa, soi kính lúp, mỉm cười hiền lành) |
| B16, B17 | Mèo ngồi bệt kiệt sức + linh hồn vẽ SVG | Mèo ngồi bệt nhỏ xíu, mặt trắng bệch, mắt thâm kiệt sức (sửa từ tờ gốc Mèo) |


---

# Cập nhật bản v2 — Lắp đủ đồ họa thật, giọng thật Mèo & SFX nâng cấp (2026-11-26)

- **Video bản v2:** `renders\thu-he-gia-truong_v2.mp4` (1920×1080, 16:9, 30 fps, **98,38 s**, 49 MB — giữ nguyên bản v1 và lưu dự phòng `.work\index_v1.html`, `.work\bang-kich-ban_v1.js`).
- **Tài nguyên mới (10 ảnh 4K + 1 file giọng thật Mèo):** sao lưu đủ trong `vat-lieu-v2\`; tách nền sạch bằng BiRefNet (`tachnen.cmd`) và đóng gói gọn vào `assets\anh-v2\`.
- **Giọng đọc v2 (`assets\giong-v2\`):**
  - **11 nhịp Mèo** cắt hoàn toàn từ giọng thu thật của chủ kênh (`hegiatruong-giongmeo.mp3`), căn tốc độ từng nhịp: dẫn chính giãn nhẹ `0,90x–0,92x` tự nhiên (`-16 LUFS`), **nhịp 7 hội thoại rụt rè** giãn `0,86x`, kéo nhỏ `-3,5 dB` (`-19,5 LUFS`) kèm EQ không gian quán; chuỗi tra tấn **nhịp 10 → 12 → 14** tăng tốc `1,04x → 1,12x → 1,22x` và cắt sạch đuôi `0 ms`; **nhịp 17 kiệt sức** chậm `0,82x`, dịu trầm; **nhịp 22** giữ `0,50 s` khựng đầu nhịp + mở khe `0,78 s` chèn huýt sáo giữa câu.
  - **6 nhịp thoại phụ** (Hệ gia trưởng B5, B8, B11, B13, B15; Bạn ngoài khung B21) dùng `edge-tts` miễn phí, phân màu âm lượng/không gian rõ ràng (B5 vang quán nhẹ `-17,5 LUFS`, B11 hiệu ứng loa phóng thanh `420–3200 Hz`, B15 dịu ngọt `-18,5 LUFS`, B21 vang ngoài khung `-19,0 LUFS`).
  - **5 nhịp Lặng giữ nguyên tuyệt đối:** B2 = 2,00 s, B6 = 2,50 s, B9 = 1,50 s (im `-91,0 dB` trước tiếng tạch), B16 = 2,00 s (**im tuyệt đối `-91,0 dB` trọn 1,00 s đầu** rồi thở hắt), B19 = 1,50 s (xước đĩa rồi im `-91,0 dB`).
- **Đồ họa & 3 lỗi bản v1 đã xử lý dứt điểm:**
  1. Thẻ bảng tier đồng bộ **tỉ lệ dọc 3:4** (chữ đậm rõ đọc tốt trên điện thoại) cho cả `#2 Con nhà người ta` (ô A), `#3 Hệ gia trưởng` (bay từ ô A đáp nảy gọn vào ô B) và `#1 Nô lệ ChatGPT` (ô C).
  2. Mũi tên đỏ, sóng âm và nhãn `"Bạn ngoài khung:"` nhịp 21 chuyển hoàn toàn sang **mép phải / góc trên-phải sau lưng Mèo**, tuyệt đối không đè lên bảng tier S–D.
  3. 3 icon code nhịp 5 (*Mô hình 3D*, *200 phiếu*, *Phỏng vấn*) đặt đúng 2 mảng tường kem trống hai bên đầu Hệ gia trưởng (không che mặt hay tay); HGT-1 (B11) & HGT-2 (B13) đặt chạm đáy khung hình chắc chắn; bỏ toàn bộ nhãn `TẠM` và nhãn đếm nhịp phác.
- **SFX nâng cấp (`assets\sfx\NGUON.md`):** 14 nhóm hiệu ứng dùng file CC0 / thư viện HyperFrames thật (đập bàn 3 lớp thật, rít ống hút + đá + quạt trần thật, quán cà phê thật, nổ kịch tính thật, công tắc tạch thật, bút dạ khoanh thật, gõ gỗ đôi thật, xước đĩa phanh trực tiếp từ chính BGM `trivial-call.mp3`, 3 màu ting luân phiên, riser thật); chỉ còn 4 âm đặc thù (`rung-dt-v2`, `tho-hat-v2`, `dan-tram-v2`, `huyt-sao-v2`) và trống dồn `trong-don-v2.wav` tổng hợp êm sạch, không rè.
