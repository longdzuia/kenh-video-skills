---
name: "nhip-hf"
description: "Chia mạch và tách dòng kịch bản tiếng Việt cho dây chuyền dựng 100% HyperFrames (không còn Veo), ra danh sách mạch và kịch bản #n.mp3-HF-câu. Dùng mặc định khi đưa kịch bản mới để tách câu, gắn mã, chạy nhịp, chia mạch."
---

# NHỊP HF — chia mạch và tách dòng cho dây chuyền 100% HyperFrames

## Việc của skill

Nhận một kịch bản tiếng Việt đầy đủ. Trả về ba thứ: danh sách mạch, phần tự kiểm, và kịch bản đã tách dòng gắn mã. Làm xong thì dừng, chờ người dùng duyệt.

Skill này không viết prompt, không tả hình, không chọn sân khấu, không phân việc cho từng dòng. Những việc đó thuộc về skill minh-y chạy trong Claude Code, ở khâu nguyên liệu.

## Bối cảnh dây chuyền

Từ tháng 10/2026, video của kênh dựng 100% trong HyperFrames, không còn clip Veo. Mỗi cảnh là một sân khấu dựng dần: ảnh nền làm phông, nhân vật và đạo cụ đã tách nền đứng lên phông, rồi lần lượt trượt vào, bật ra, đổi tư thế, rời đi. Mỗi dòng kịch bản là một nhịp của sân khấu, tức là một lần thứ trên màn hình thay đổi. Minh-y đọc kịch bản đã tách dòng và danh sách mạch, phân mỗi dòng vào một trong bốn việc (Tin, Thấy lại, Hiểu, Cảm), gom các dòng thành sân khấu, rồi lên danh sách nguyên liệu.

Vì vậy skill này chỉ còn hai tầng: mạch và dòng. Không còn khối, không còn phân vai VEO hay HF.

Giọng đọc là một file liền cả bài. Mã `#n.mp3` chỉ là số thứ tự dòng, không phải tên file âm thanh riêng. Nếu kịch bản đã gắn mã sẵn thì giữ nguyên cách tách và số mã của người dùng, chỉ chia mạch và kiểm.

Bản nhip-doan cũ vẫn còn, dùng cho video làm theo dây chuyền có Veo. Không mang luật của nó sang đây.

## Bước 1 — Chia mạch

Đọc hết kịch bản trước, rồi chia mạch theo chỗ câu chuyện thật sự rẽ: sang một phần mới, bước vào hay bước ra một nơi, một thời khác, chuyển từ kể sang giải thích ở tầm cả một đoạn. Không cắt mạch giữa chừng một mạch ý.

Mỗi mạch có:
- **Tên ngắn:** nói mạch kể chuyện gì.
- **Khoảng mã:** từ dòng nào đến dòng nào.
- **Đang ở đâu:** một cụm ngắn nói câu chuyện đang diễn ra ở nơi nào, thời nào, ví dụ "nhà máy GM ở Fremont, California, đầu thập niên 1980". Nếu mạch không gắn với một nơi cụ thể thì ghi "giải thích chung". Nếu là đoạn người kể nói thẳng với người xem thì ghi "nói với người xem". Đây là thông tin cho minh-y gom sân khấu, không phải tả hình: không tả góc máy, màu, bố cục.

Kịch bản của kênh hay mở kiểu cold open: đoạn đắt nhất được đưa lên đầu, rồi đến câu giới thiệu kiểu "và tôi là Sinh Viên Kinh Tế, ở video này tôi sẽ nói về…", rồi quay lại kể từ đầu. Khi gặp cấu trúc này:
- đoạn đưa lên đầu là một mạch riêng;
- câu giới thiệu là một dòng trọn, thuộc mạch riêng hay thuộc mạch mở, tùy độ dài;
- chỗ quay lại kể từ đầu luôn là ranh giới mạch.

## Bước 2 — Tách dòng

Mỗi dòng là một nhịp: một lần thứ người xem cần nhìn trên sân khấu thay đổi.

- **Một dòng kết thúc khi thứ người xem cần nhìn thay đổi.** Ví dụ: một người, một vật, một nơi hay một mốc thời gian mới bước vào; nhân vật chuyển sang làm một việc khác; câu chuyển từ khẳng định sang bằng chứng, hay từ bằng chứng sang hệ quả; một câu lật; một con số hay một thuật ngữ xuất hiện.
- **Chỉ tách ở chỗ giọng đọc tự nhiên nghỉ:** dấu chấm, chấm phẩy, hai chấm, dấu phẩy giữa hai vế. Không tách giữa số và đơn vị, giữa tên và chức danh, hay giữa những chữ mà tách ra thì nghe cụt.
- **Độ dài:** dòng thường dài 15 đến 30 tiếng, khoảng 3 đến 6 giây, hiếm khi dưới 8 tiếng. Dòng dài quá 35 tiếng thì xét tách ở chỗ nghỉ gần nhất, nếu ở đó có một thay đổi đáng nhìn. Không có thì giữ, và ghi vào phần tự kiểm. Đây là số tạm.
- **Mắt nhường tai.** Chỗ kể chuyện thì tách mau, vì mỗi hành động của nhân vật là một tư thế mới trên sân khấu. Chỗ đang bóc một cơ chế hay một lập luận thì để dòng dài hơn, đừng băm vụn, vì lúc đó người xem cần nghe hơn cần nhìn.
- **Giữ trọn một dòng, không tách:** câu mang đi (bài học cốt lõi của bài), câu đóng, câu giới thiệu kênh, và đoạn người kể quay sang nói với người xem. Những câu này cần khoảng lặng để hạ cánh.
- **Không sửa, thêm, bớt một chữ nào,** giữ nguyên dấu câu. Nối các dòng lại theo thứ tự phải ra đúng nguyên văn kịch bản. Dòng không được đọc thành lời, như tiêu đề hay ghi chú, thì bỏ ra và báo lại.

Mọi dòng mang nhãn `HF`. Nhãn này giữ lại chỉ để các công cụ đang đọc định dạng `#n.mp3-NHÃN-câu` trong Claude Code không phải sửa; nó không mang nghĩa phân vai.

## Bước 3 — Tính giây và tự kiểm

- **Đếm tiếng:** tách bằng khoảng trắng, bỏ dấu câu. Số viết bằng chữ số đếm theo cách đọc thành lời: 2009 đọc là "hai nghìn không trăm lẻ chín", tính sáu tiếng.
- **Giây bằng số tiếng nhân 0,21.** Con số này chỉ để ước lượng; mốc thời gian thật do Claude Code lấy từ chính giọng đọc.
- Nếu người dùng đưa tổng thời lượng thật, so với tổng ước tính; lệch quá mười phần trăm thì báo.
- Có gì bất thường thì không tự sửa cho vừa: báo con số, nêu lý do nội dung, để người dùng quyết. Lệch trong im lặng là lỗi nặng nhất; lệch có báo cáo thì không phải lỗi.

## Định dạng đầu ra

In đúng ba phần theo thứ tự, toàn bộ bằng tiếng Việt.

**Phần một, danh sách mạch**, trong một code block. Người dùng lưu thành `assets\mach.txt` của dự án để minh-y đọc. Mỗi mạch một dòng:

```
Mạch [số] — [tên ngắn] — #[mã đầu]–#[mã cuối] — [đang ở đâu]
```

**Phần hai, phần tự kiểm:**

```
Tổng: [a] dòng | [b] giây ước tính
Số mạch: [m]
Mạch mở: [cold open hay kể thẳng], #[mã]–#[mã], [giây] giây
Dòng ngắn nhất: #[mã], [n] tiếng
Dòng dài hơn 35 tiếng: [mỗi dòng: mã, số tiếng, giữ vì ...; hoặc "không"]
Dòng giữ trọn theo luật: [mã và loại: câu mang đi / câu đóng / câu giới thiệu / nói với người xem]
Nguyên văn: [khớp / lệch ở đâu]
Thời lượng thật: [so sánh, hoặc "không có"]
```

**Phần ba, kịch bản gắn mã**, trong một code block duy nhất. Mỗi dòng một nhịp theo dạng `#n.mp3-HF-dòng`, đánh số liên tục từ 1, không tiêu đề, không ghi chú, không dòng trống. Phần này lưu thẳng thành `assets\kichban.txt` (mã hóa UTF-8), nên định dạng phải đúng từng ký tự.

## Những con số còn tạm

- **15 đến 30 tiếng** cho một dòng thường: mang từ nhip-doan, đo trên các video còn Veo; chưa kiểm trong lối sân khấu.
- **35 tiếng** cho ngưỡng xét tách: đặt mới khi bỏ mốc 33 tiếng của dòng VEO; chưa đo.
- **0,21 giây một tiếng**: tốc độ đọc theo hồ sơ cũ, chỉ để ước lượng.

Khi một con số có vẻ sai với kịch bản đang làm, báo ra chứ đừng lặng lẽ bẻ cho vừa. Người dùng không muốn rút luật từ vài video rồi vá thêm luật sau mỗi lỗi. Góp ý sau một video thì sửa cho video đó; chỉ sửa luật của skill khi người dùng bảo.

## Ranh giới

Không viết prompt. Không tả hình, góc máy, ánh sáng hay style. Không phân việc Tin, Thấy lại, Hiểu, Cảm cho từng dòng. Không chọn sân khấu, nhân vật hay nguyên liệu. Khi người dùng yêu cầu dời ranh giới mạch hay tách lại dòng nào, sửa rồi in lại đủ ba phần.
