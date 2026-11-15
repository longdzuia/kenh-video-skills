# Kênh xếp hạng — Sổ tay style

Nov 13, 2026 · @Tuấn long

## Đã chốt

Sau buổi 13/11, kênh xếp hạng đã có đủ bốn mảnh để dựng tập đầu: style người nguệch ngoạc mà vẫn ra người, phông vẽ có hồn và có chữ, lối dựng cảnh sinh liền người với cảnh rồi cắt phựt kèm rung, và nhân vật kênh là mèo xám tai sứt. Mọi thứ dưới đây là giả thuyết đã qua một vòng thử, chưa phải luật.

| Hạng mục | Đã chốt | Bằng chứng |
| --- | --- | --- |
| Dựng cảnh | Sinh ảnh có nhân vật ngồi sẵn trong cảnh, 2–3 tư thế sửa từ một tấm gốc | Ba tấm "Ai là triệu phú": nền gần như đứng im giữa các tư thế |
| Chuyển cảnh | Bản B và bản C; bỏ bản A | Long xem trên điện thoại: A (chỉ cắt phựt) không nổi |
| Style người | Người ra người: nét nguệch ngoạc nhưng có cằm, tai, mũi một nét, lông mày; đầu khoảng một phần ba người; mỗi nhân vật một dấu riêng. Đã bỏ đầu trứng | Bản đầu trứng đứng cạnh mèo thì người không ra người; tờ người mới và dàn sáu nhân vật đang chờ chạy |
| Style nền | Vẽ nguệch, có dấu vết người sống, có chữ; cảnh thật giữ màu và chữ ký nơi chốn | Tấm giảng đường có nắng chiều, tấm sân khấu "Ai là triệu phú" |
| Đổi style | Kho nhiều vũ khí theo cảm xúc, khuôn chung giữ danh tính | Bản manga đạt, không bị nhựa |
| Nhân vật kênh | Mèo xám than đứng hai chân, mắt lệch mí nặng, tai trái sứt, đuôi gãy khúc | Bản xám đọc rõ hơn hẳn bản đen ở cỡ nhỏ |

## Dựng cảnh và chuyển cảnh

Một cảnh là hai đến ba tấm tranh cùng khung, chỉ nhân vật đổi tư thế, HyperFrames cắt phựt giữa chúng theo nhịp lời đọc và thêm rung. Cách này đi theo lối hoạt hình tiết kiệm của các kênh mẫu.

**Quy trình đã chạy được**

1. Sinh phông trống của cảnh (xem phần Style nền).
2. Ghép nhân vật vào phông bằng Nano Banana, đính hai ảnh: phông trước, tờ gốc nhân vật sau.
3. Sửa tư thế 2 và 3 từ **chính tấm gốc vừa ra**, không sửa nối tiếp từ tư thế 2, vì sai lệch sẽ cộng dồn.
4. Đưa ba tấm cho Claude Code dựng.

**Vì sao sinh liền người với cảnh:** nhân vật tách nền dán đè lên thì luôn nằm trước mọi vật, không ăn màu ánh sáng của cảnh, và lệch cỡ nét. Sinh liền một lần giải quyết cả ba chỗ đó. Lối tách nền chỉ dành cho nhân vật chạy vào, đi ngang, hay bật lên trên nền trống.

**Kiểm tra nền đứng im:** so từng điểm ảnh ba tấm "Ai là triệu phú" (2576×1438), vùng ghế trống bên phải gần như không đổi, khác biệt chỉ nằm quanh nhân vật. Vậy hoán đổi nguyên tấm được; chỉ khi thấy nền nhấp nháy mới cần cắt vùng nhân vật dán lên tấm gốc.

**Phóng to:** ảnh 4K phóng khoảng 1,3 lần vẫn nét trên khung 1080p. Cận mặt mạnh hơn thì sinh riêng một tấm.

**Ba bản chuyển cảnh đã thử**

| Bản | Cách làm | Kết quả |
| --- | --- | --- |
| A | Chỉ cắt phựt | Không nổi, bỏ |
| B | Cắt phựt + rung khung 0,3 giây tắt dần + phóng nhẹ 1,2–1,3 lần vào mặt ở tư thế 2 và 3 | Hợp |
| C | Như B + nhân vật rung nhẹ liên tục trong lúc giữ tấm, nền đứng yên | Hợp |

Nhịp đã dùng: giữ tư thế 1 khoảng 2 giây, cắt sang tư thế 2, cắt sang tư thế 3, rồi cắt về tư thế 1. Cú quay về mặt lì là chỗ người xem bật cười.

**Prompt ghép nhân vật vào cảnh** (ảnh 1: phông, ảnh 2: tờ gốc nhân vật)

```text
Use the first attached image as the scene and keep it exactly as it is: the same camera, the same colors and every object in the same place. Place the character from the second attached image sitting in the contestant's chair on the left, drawn in exactly the same crude doodle style as the second image: the same egg-shaped head, the same messy hair tuft, the same blue t-shirt, grey shorts and flip-flops. He is not holding the laptop or the energy drink: they are gone, and both of his hands grip the armrests. He sits stiff as a board, sweat drops flying off his head, eyes wide with tiny pupils, staring at the empty chair on the right. His legs are partly hidden behind the front of the chair. The purple stage light gives his white skin and clothes a slight flat purple tint. Same line weight as the scene. Do not change anything else.
```

**Prompt sửa tư thế** (đính tấm gốc có nhân vật; thay câu tư thế cho từng tấm)

```text
Edit the attached image. Keep everything exactly the same: the stage, the camera, the colors, both chairs, the empty chair on the right staying empty, the character's size and his position in the chair, and the purple tint on his skin and clothes. Change only his pose and expression: he clutches his head with both hands, elbows out, mouth wide open in panic, eyes huge with tiny shaking pupils, his messy hair tuft standing up even higher, a few more sweat drops flying off his head. He is not holding any laptop or can. Same crude doodle line weight as the rest of the image. Do not change anything else.
```

Tư thế 3 đã dùng: `he leans forward and jabs one finger toward the empty chair, eyes blazing with fake confidence, a huge cocky grin, his other hand still on the armrest`.

## Style nhân vật người

Người phải ra người, nhân vật phải ra nhân vật. Từ tối 13/11 bỏ lối đầu trứng: đứng cạnh con mèo có tai, mũi, ria, người đầu trứng lại kém tính nhân vật hơn con vật, nhìn không ra một sinh viên. Giữ nét tay run, màu phẳng và mọi lệnh cấm bóng bẩy; trả lại cho người cằm, tai, mũi một nét, và nhất là lông mày, thứ gánh phần lớn biểu cảm.

**Cái "con người" của các kênh mẫu đến từ đâu** (rút từ ba video mẫu, mỗi video 16 khung):

- Mặt người đơn giản nhưng cường điệu: mũi hồng to tướng, mắt trợn, mồ hôi túa; dám vẽ xấu thật.
- Nhiều khoảng trống, người phụ chỉ là bóng xám không mặt.
- Cắt dán: nhân vật vẽ đặt lên ảnh thật (poster, lớp học, gói mì, ảnh chụp màn hình).
- Đổi style để tạo cú đấm (xem Kho vũ khí).
- Mỗi nhân vật có một dấu riêng nhìn là nhận ra.

Chuẩn gần nhất là kênh những mối tình tuổi thơ: tóc xoăn, kính, có mũi, có cằm, tô màu dở, vẫn nguệch mà nhìn là ra một người cụ thể.

**Khối style người** (đầu mọi prompt nhân vật người)

```text
A quick, deliberately crude hand-drawn webcomic doodle by an amateur Vietnamese YouTube storyteller, drawn fast, slightly off-model and not symmetrical. The whole image is the drawing itself, not a photo of a screen or any device. Black lines with uneven pressure, some strokes overshooting a little, some not fully closed. The character is clearly a real human, simplified: the head is about one third of the body height, a real face shape with a jaw and chin, simple C-shaped ears, a small nose drawn with one stroke, thick expressive eyebrows, eyes as small white shapes with black dot pupils, a mouth that can stretch wide. A real neck and shoulders, simple arms and legs, hands drawn simply with four fingers. Proportions slightly exaggerated for comedy but clearly a person. Flat bucket-fill colors, skin a flat pale cream, no shading, no gradients, no highlights, no blush, no fabric folds, no paper texture, no vignette. Not anime and not a polished character design: it looks like a funny comic drawn by a person, not by a professional illustrator.
```

**Núm vặn là tỷ lệ đầu.** Ra như tranh minh họa sách giáo khoa thì đổi "about one third" thành "almost half". Ra lại giống trứng là đã đi quá xa phía kia. Càng ra người, Nano Banana càng muốn kéo về lối minh họa chỉn chu; câu "Not anime and not a polished character design" là cái phanh.

Sinh từng nhân vật một tờ, mỗi đứa trong một cuộc trò chuyện mới. Đính tờ cậu gánh team làm tham chiếu nét cho các đứa còn lại (câu cuối mỗi prompt); chưa có tờ đó thì xóa câu cuối.

**Dàn nhân vật cho đề các kiểu thành viên nhóm thảo luận**

| Kiểu | Dáng | Dấu riêng |
| --- | --- | --- |
| Cậu gánh team | Nam, gầy, khom | Chỏm tóc dựng đứng, quầng thâm |
| Đứa lặn mất tăm | Nữ, nhỏ người | Mũ hoodie xanh trùm nửa đầu, dép tổ ong |
| Đứa chỉ biết "ok" | Nam, tròn trịa | Tóc úp bát, ngón cái giơ đông cứng |
| Nhóm trưởng kiểm soát | Nữ, cao gầy | Búi tóc chặt cắm bút, kính vuông |
| Diễn giả không làm gì | Nam | Tóc vuốt keo có lọn xoăn rủ trán, cà vạt lệch |
| Đứa chép nguyên văn từ AI | Nam, lêu nghêu | Tai nghe to đeo cổ |

Ý chưa viết prompt: đứa chuyên cãi "nhưng mà", đứa nộp bài đúng 23 giờ 59, đứa chỉ làm phần slide cho đẹp.

**Tờ gốc cậu gánh team**

```text
A quick, deliberately crude hand-drawn webcomic doodle by an amateur Vietnamese YouTube storyteller, drawn fast, slightly off-model and not symmetrical. The whole image is the drawing itself, not a photo of a screen or any device. Black lines with uneven pressure, some strokes overshooting a little, some not fully closed. The character is clearly a real human, simplified: the head is about one third of the body height, a real face shape with a jaw and chin, simple C-shaped ears, a small nose drawn with one stroke, thick expressive eyebrows, eyes as small white shapes with black dot pupils, a mouth that can stretch wide. A real neck and shoulders, simple arms and legs, hands drawn simply with four fingers. Proportions slightly exaggerated for comedy but clearly a person. Flat bucket-fill colors, skin a flat pale cream, no shading, no gradients, no highlights, no blush, no fabric folds, no paper texture, no vignette. Not anime and not a polished character design: it looks like a funny comic drawn by a person, not by a professional illustrator. One character alone, full body, standing, centered with lots of empty space: a thin slouching Vietnamese male university student around twenty, messy black hair with one tuft sticking straight up as his signature trait, big dark circles under his eyes, eyebrows drooping, a tired forced smile. He wears a plain blue t-shirt, dark grey shorts and black flip-flops. He hugs an open grey laptop to his chest with one arm and holds a can of energy drink in the other hand. Plain solid flat pure white background. No written words.
```

**Tờ gốc đứa lặn mất tăm**

```text
A quick, deliberately crude hand-drawn webcomic doodle by an amateur Vietnamese YouTube storyteller, drawn fast, slightly off-model and not symmetrical. The whole image is the drawing itself, not a photo of a screen or any device. Black lines with uneven pressure, some strokes overshooting a little, some not fully closed. The character is clearly a real human, simplified: the head is about one third of the body height, a real face shape with a jaw and chin, simple C-shaped ears, a small nose drawn with one stroke, thick expressive eyebrows, eyes as small white shapes with black dot pupils, a mouth that can stretch wide. A real neck and shoulders, simple arms and legs, hands drawn simply with four fingers. Proportions slightly exaggerated for comedy but clearly a person. Flat bucket-fill colors, skin a flat pale cream, no shading, no gradients, no highlights, no blush, no fabric folds, no paper texture, no vignette. Not anime and not a polished character design: it looks like a funny comic drawn by a person, not by a professional illustrator. One character alone, full body, centered with lots of empty space: a small Vietnamese female university student in an oversized green hoodie with the hood half pulled up as her signature trait, straight black hair poking out, loose black pants and Vietnamese honeycomb foam sandals, a backpack on one shoulder. She tiptoes away with comically long sneaky steps, looking back over her shoulder with guilty sideways eyes, eyebrows raised high, one finger pressed to her lips, three sweat drops flying off her head. Plain solid flat pure white background. No written words. Use the attached image only as a reference for drawing style, line weight and proportions; do not copy his face, hair or clothes.
```

**Tờ gốc đứa chỉ biết "ok"**

```text
A quick, deliberately crude hand-drawn webcomic doodle by an amateur Vietnamese YouTube storyteller, drawn fast, slightly off-model and not symmetrical. The whole image is the drawing itself, not a photo of a screen or any device. Black lines with uneven pressure, some strokes overshooting a little, some not fully closed. The character is clearly a real human, simplified: the head is about one third of the body height, a real face shape with a jaw and chin, simple C-shaped ears, a small nose drawn with one stroke, thick expressive eyebrows, eyes as small white shapes with black dot pupils, a mouth that can stretch wide. A real neck and shoulders, simple arms and legs, hands drawn simply with four fingers. Proportions slightly exaggerated for comedy but clearly a person. Flat bucket-fill colors, skin a flat pale cream, no shading, no gradients, no highlights, no blush, no fabric folds, no paper texture, no vignette. Not anime and not a polished character design: it looks like a funny comic drawn by a person, not by a professional illustrator. One character alone, full body, standing, centered with lots of empty space: a chubby round-faced Vietnamese male university student with a neat bowl haircut as his signature trait, wearing a bright yellow hoodie and jeans. His eyes are closed in two happy curves, eyebrows relaxed, a huge blank empty smile, one hand frozen in a big thumbs up, the other hand holding a phone. He looks completely carefree and has clearly done nothing. Plain solid flat pure white background. No written words. Use the attached image only as a reference for drawing style, line weight and proportions; do not copy his face, hair or clothes.
```

**Tờ gốc nhóm trưởng kiểm soát**

```text
A quick, deliberately crude hand-drawn webcomic doodle by an amateur Vietnamese YouTube storyteller, drawn fast, slightly off-model and not symmetrical. The whole image is the drawing itself, not a photo of a screen or any device. Black lines with uneven pressure, some strokes overshooting a little, some not fully closed. The character is clearly a real human, simplified: the head is about one third of the body height, a real face shape with a jaw and chin, simple C-shaped ears, a small nose drawn with one stroke, thick expressive eyebrows, eyes as small white shapes with black dot pupils, a mouth that can stretch wide. A real neck and shoulders, simple arms and legs, hands drawn simply with four fingers. Proportions slightly exaggerated for comedy but clearly a person. Flat bucket-fill colors, skin a flat pale cream, no shading, no gradients, no highlights, no blush, no fabric folds, no paper texture, no vignette. Not anime and not a polished character design: it looks like a funny comic drawn by a person, not by a professional illustrator. One character alone, full body, standing, centered with lots of empty space: a tall thin Vietnamese female university student with her hair pulled into a very tight high bun with a pen stuck through it as her signature trait, square glasses, a neat white shirt and a long dark skirt. She holds a clipboard with a long checklist in one hand and points sharply forward with the other, eyebrows slammed down in a furious frown, mouth wide open mid-shout, a small angry vein popping on her forehead. Plain solid flat pure white background. No written words. Use the attached image only as a reference for drawing style, line weight and proportions; do not copy his face, hair or clothes.
```

**Tờ gốc diễn giả không làm gì**

```text
A quick, deliberately crude hand-drawn webcomic doodle by an amateur Vietnamese YouTube storyteller, drawn fast, slightly off-model and not symmetrical. The whole image is the drawing itself, not a photo of a screen or any device. Black lines with uneven pressure, some strokes overshooting a little, some not fully closed. The character is clearly a real human, simplified: the head is about one third of the body height, a real face shape with a jaw and chin, simple C-shaped ears, a small nose drawn with one stroke, thick expressive eyebrows, eyes as small white shapes with black dot pupils, a mouth that can stretch wide. A real neck and shoulders, simple arms and legs, hands drawn simply with four fingers. Proportions slightly exaggerated for comedy but clearly a person. Flat bucket-fill colors, skin a flat pale cream, no shading, no gradients, no highlights, no blush, no fabric folds, no paper texture, no vignette. Not anime and not a polished character design: it looks like a funny comic drawn by a person, not by a professional illustrator. One character alone, full body, standing, centered with lots of empty space: a Vietnamese male university student with slick gelled hair combed to one side and one shiny curl falling on his forehead as his signature trait, wearing a white shirt one size too big and a crooked red tie. He holds a microphone with his little finger sticking out, his other arm spread wide like a famous motivational speaker, eyebrows raised confidently, chin up, a dazzling overconfident smile, though he clearly has no idea what he is talking about. Plain solid flat pure white background. No written words. Use the attached image only as a reference for drawing style, line weight and proportions; do not copy his face, hair or clothes.
```

**Tờ gốc đứa chép nguyên văn từ AI**

```text
A quick, deliberately crude hand-drawn webcomic doodle by an amateur Vietnamese YouTube storyteller, drawn fast, slightly off-model and not symmetrical. The whole image is the drawing itself, not a photo of a screen or any device. Black lines with uneven pressure, some strokes overshooting a little, some not fully closed. The character is clearly a real human, simplified: the head is about one third of the body height, a real face shape with a jaw and chin, simple C-shaped ears, a small nose drawn with one stroke, thick expressive eyebrows, eyes as small white shapes with black dot pupils, a mouth that can stretch wide. A real neck and shoulders, simple arms and legs, hands drawn simply with four fingers. Proportions slightly exaggerated for comedy but clearly a person. Flat bucket-fill colors, skin a flat pale cream, no shading, no gradients, no highlights, no blush, no fabric folds, no paper texture, no vignette. Not anime and not a polished character design: it looks like a funny comic drawn by a person, not by a professional illustrator. One character alone, full body, standing, centered with lots of empty space: a lanky Vietnamese male university student with a messy fringe and big headphones hanging around his neck as his signature trait, wearing a wrinkled grey t-shirt and shorts. He slouches and stares at his phone with a completely blank face, eyebrows flat, mouth hanging open, one finger lazily tapping the screen, a small question mark floating above his head. Plain solid flat pure white background. No written words. Use the attached image only as a reference for drawing style, line weight and proportions; do not copy his face, hair or clothes.
```

**Thay người trong cảnh đã có** (ảnh 1: tấm cảnh có nhân vật cũ, ảnh 2: tờ gốc người mới; làm cho từng tư thế để giữ nguyên cảnh)

```text
Edit the first attached image. Keep everything exactly the same: the stage, the camera, the colors, both chairs, the character's pose, size, position and expression, and the purple tint on him. Replace only the character's drawing with the character from the second attached image: the same human face with jaw, ears, nose and eyebrows, the same messy hair with the tuft sticking up, the same blue t-shirt, grey shorts and flip-flops, drawn in the same crude doodle style. Do not change anything else.
```

## Style nền

Nền không có một style duy nhất mà là một cái thang, mỗi câu thoại leo lên đúng nấc nó cần. Phông vẽ phải có dấu vết người sống và có chữ thì mới có hồn; cảnh thật thì giữ nguyên màu và chữ ký của nơi đó.

| Nấc | Dùng khi | Làm bằng |
| --- | --- | --- |
| Nền trống | Cận mặt, phản ứng (nhiều nhất) | Code tô một màu phẳng |
| Vài nét | Cần biết đang ở đâu | Sinh chung với nhân vật (một mép bàn, một cái đèn) |
| Phông vẽ đầy đủ | Đến một nơi mới | Khối phông + chi tiết sống |
| Ảnh thật làm nền | Nơi chốn, vật có thật | Ảnh thật, nhân vật vẽ đặt lên (cắt dán) |
| Chuyển cảnh thật vào style | Nhại một nơi ai cũng biết | Khuôn chuyển cảnh thật |

Phông vẽ không được *giỏi* hơn nhân vật, và màu lùi xuống một chút so với nhân vật nhưng không được chết cả khung.

**Khối phông vẽ**

```text
A quick, deliberately crude hand-drawn cartoon background, as if an amateur Vietnamese YouTube storyteller drew it fast. The whole image is the drawing itself filling the frame, not a photo of a screen, a tablet or any device. Slightly crooked perspective that is not technically correct. Black lines with uneven pressure, some strokes overshooting, some not fully closed. The place looks lived-in, with small traces of the people who use it. One clear time-of-day cue drawn as flat shapes, for example afternoon sunlight from a window as flat pale yellow patches on the floor. Flat bucket-fill colors, a little softer than the characters that will stand on top, with one or two warm accents. No shading, no smooth gradients, no textures, no vignette. Open floor in the lower part of the image for characters to stand. No people anywhere. Writing that belongs to the place is welcome, such as signs, banners, slogans, logos and chalk writing, hand-lettered in the same crude style and spelled exactly as given in quotes.
```

**Chi tiết sống, ví dụ giảng đường** (tấm Long ưng nhất)

```text
A Vietnamese university lecture room seen from the back rows: long wooden desks in rows, a green chalkboard with half-erased chalk writing reading "Chương 3: Cung và cầu", a red banner hanging slightly crooked above the board reading "HỌC, HỌC NỮA, HỌC MÃI", a pulled-down projector screen, a lecturer's desk with a plastic flower vase, a ceiling fan, a forgotten water bottle and a crumpled paper on one desk, one plastic chair pulled out of line, late afternoon sun through the side windows.
```

Các phông khác đã phác: quán trà đá vỉa hè Hà Nội, phòng ký túc xá.

**Luật chữ:** chữ được giữ, vì cảnh Việt Nam sống nhờ chữ. Luôn đưa nguyên văn trong ngoặc kép; không đưa thì mô hình tự bịa chữ vô nghĩa. Chữ trên bảng đen nên đổi theo từng video.

**Khuôn chuyển cảnh thật vào style** (đính ảnh chụp thật; thay phần chữ ký nơi chốn)

Với cảnh thật, luật khác hẳn phông vẽ: giữ màu gốc và mọi chi tiết khiến người ta nhận ra nơi đó, chỉ đổi cách vẽ ánh sáng thành mảng phẳng có viền tay.

**Bản "Ai là triệu phú" đã đạt** (ảnh 1: ảnh chụp sân khấu, ảnh 2: tấm giảng đường làm mỏ neo nét; khung 16:9)

```text
Redraw the first attached photo as a quick, deliberately crude hand-drawn cartoon background, as if an amateur Vietnamese YouTube storyteller traced it fast. The whole image is the drawing itself, not a photo of a screen or any device. Keep the composition, the original colors and every signature element that makes this place recognizable: the deep purple and blue darkness of the studio, the two tall bright red glowing arches, the white curved stand in the center on a round raised platform, the two tall chairs facing each other, the cones of pale purple and bluish white spotlight beams coming down from above, and a large round glowing emblem behind the center with the title "AI LÀ TRIỆU PHÚ" hand-lettered around it. Remove the two people sitting in the chairs and leave both chairs empty. Simplify everything else into a few wobbly lines and flat bucket-fill colors. Black lines with uneven pressure, some strokes overshooting, some not fully closed. The dark areas are flat solid color, not heavy scribbled hatching. Light is drawn, not rendered: spotlights, glows and neon become flat bright shapes with simple hand-drawn outlines and a few short radiating lines. No smooth gradients, no bloom, no 3D rendering, no photo texture. No people. Use the second attached image only as a reference for line weight, line wobble and level of detail; do not copy its room, desks, colors or composition.
```

Với một nơi khác, thay đoạn từ "the deep purple…" đến "…hand-lettered around it" bằng những thứ một người quen chỗ đó nhìn lướt là nhận ra, và bỏ câu xóa người nếu ảnh không có người.

Về logo thật của chương trình: rủi ro khiếu nại với một bản vẽ tay nhại lại là nhỏ, Long quyết giữ tên thật; một tên nhại vẫn là lựa chọn nếu muốn câu đùa nằm sẵn trên sân khấu.

## Kho vũ khí đổi style

Cú đổi style buồn cười vì người xem thấy cùng một gã vẽ nguệch ngoạc bỗng gồng hết sức, nên đích đến chọn trong họ mực và in ấn để không dính bệnh nhựa AI. Danh tính sống sót nhờ dấu riêng và ảnh tham chiếu là tờ gốc nhân vật.

**Khuôn chung** (đính tờ gốc nhân vật; thay STYLE và DETAILS)

```text
Redraw the character in the attached image as [STYLE], as if the same amateur artist suddenly tried very hard in a completely different style. Keep him clearly recognizable: the same hairstyle, the same clothes, the same props and the same colors as in the attached image. Change only the drawing: [DETAILS]. Visible hand-made marks of the medium. No smooth digital gradients, no glow, no airbrushed skin, no 3D rendering. No written words.
```

Nhớ thay hết ngoặc vuông trước khi bấm, hoặc nhờ Claude viết sẵn prompt hoàn chỉnh.

| Vũ khí | Dùng khi | Trạng thái |
| --- | --- | --- |
| Manga đen trắng | Quyết tâm, bùng nổ, chế độ nghiêm túc | Đạt; hai bản bị thay áo thành sơ mi, vest nên đã khóa thêm quần áo |
| Kinh dị mực bẩn | Hạng chót, nỗi sợ hạn nộp, sự thật phũ | Chưa thử |
| Shoujo lấp lánh | Crush, thứ hoàn hảo đến vô lý | Chưa thử |
| Áp phích cổ động | Vinh danh lố, "chiến sĩ thi đua" | Chưa thử |
| Tranh Đông Hồ | Triết lý "xưa nay vẫn thế" | Chưa thử |
| Pixel 8-bit | Rớt hạng, game over | Chưa thử |
| Truyện tranh Mỹ thập niên 60 | Anh hùng gánh cả nhóm | Chưa thử |
| Sơn dầu quý tộc | Đẳng cấp vô lý (sát ranh giới nhựa nhất) | Chưa thử |
| Anime truyền hình thập niên 90 | Hoài niệm; làm thân cho pha rút thẻ SS | Chưa thử |

**Phần điền cho từng vũ khí**

```text
MANGA — STYLE: one dramatic panel from a black-and-white Japanese manga | DETAILS: realistic proportions, sharp intense eyes, a clenched jaw, dramatic black ink brush lines, hand-drawn speed lines bursting from behind, screentone dot shading and cross-hatching, visible pen strokes, ink on paper, no color

KINH DỊ — STYLE: a panel from a black-and-white horror manga | DETAILS: dense scratchy cross-hatching, heavy pools of black ink, wide staring eyes with tiny shaking pupils, cold sweat, a slightly distorted face, unsettling shadows creeping in from the edges, no color

SHOUJO — STYLE: a panel from a 1990s shoujo romance manga | DETAILS: huge eyes full of sparkles drawn as white ink dots, delicate thin lines, hand-drawn flowers and sparkles floating around, soft dot screentone, a dreamy expression with hatched blush lines, no color

CỔ ĐỘNG — STYLE: a vintage Vietnamese propaganda poster from the 1960s to 1980s | DETAILS: only bold flat red, yellow and cream colors, a heroic upward gaze toward the horizon, simple bold woodcut-like shapes, sun rays radiating behind him, rough uneven ink print texture

ĐÔNG HỒ — STYLE: a traditional Vietnamese Dong Ho folk woodblock print | DETAILS: thick black woodblock outlines, flat earthy colors like ochre, indigo, rust red and moss green, warm handmade paper with visible fibers, a stiff folk-art pose, colors slightly misregistered

PIXEL — STYLE: a character sprite from a 1990s 8-bit video game | DETAILS: chunky visible pixels, a limited palette of about eight flat colors, no anti-aliasing, a defeated game-over pose, a simple pixel background

MỸ 60S — STYLE: a panel from a 1960s American superhero comic book | DETAILS: bold black ink outlines, flat primary colors printed with visible halftone dots, slightly misaligned color printing, a powerful heroic pose, dramatic action lines

SƠN DẦU — STYLE: a 17th-century European oil portrait of a nobleman | DETAILS: thick visible brushstrokes, a dark brown background, dramatic side light like a candle, cracked old varnish, a pompous serious expression, an ornate lace collar added over his clothes

ANIME 90S — STYLE: a frame from a 1990s TV anime | DETAILS: flat cel colors with one hard-edged shadow tone, thin clean ink lines, slightly faded film colors, light film grain, an exaggerated reaction with a giant sweat drop
```

**Mức đổi:** nhẹ là giữ nét nguệch nhưng đẩy cực đoan (cận sát, mắt trợn, đường tốc độ); giữa là nhân vật vẫn nguệch nhưng thế giới quanh nó thành kịch tính; nặng là vẽ lại trọn bằng khuôn trên, chỉ dành cho vài khoảnh khắc đắt nhất mỗi video.

**Nhịp:** cú đổi giữ 1–2 giây, cắt phựt vào kèm tiếng nhấn, rồi cắt thẳng về khung nguệch ngoạc với mặt lì.

**Vũ khí không cần sinh ảnh:** nhại khung trường quay ("Ai là triệu phú", bản tin thời sự, quảng cáo đêm khuya, màn hình báo điểm thi), nhân vật vẫn nguệch, HyperFrames dựng khung bằng code.

**Chữ ký có thể có:** món nào lên SS thì luôn là một pha rút thẻ gacha (thân anime 90s, khung thẻ và hào quang do code vẽ); món rớt hạng chót thì là khung kinh dị hoặc bi tráng.

## Nhân vật kênh: mèo xám

Nhân vật kênh là một con mèo xám than béo lùn, đứng hai chân như người, mắt lệch mí nặng với cái nhìn khinh khỉnh, làm giám khảo khó tính. Mèo hợp với kênh xếp hạng vì xếp hạng là phán xét, và trên mạng không loài nào nổi tiếng phán xét bằng mèo. Tên chưa đặt.

**Dấu riêng** (đi theo qua mọi trang phục và cú đổi style): tai trái sứt một miếng, đuôi gãy khúc gần chóp, một mắt to một mắt nhỏ dưới mí nặng.

**Vai:** hình đại diện của người dẫn. Giọng đọc là của kênh; mèo đứng cạnh bảng, phản ứng và ra tay xếp hạng, thỉnh thoảng lẻn vào cảnh như kẻ đứng xem.

**Hành vi chữ ký:** món bị chê thì mèo nhìn thẳng máy quay rồi lấy chân gạt nó rơi khỏi bảng, đó là hạng D. Món lên SS là lúc hiếm hoi nó mất bình tĩnh: mắt bật to, lông xù, đuôi xù như chổi.

**Vì sao chọn màu xám**

| Màu | Kết quả |
| --- | --- |
| Đen | Khó đọc: nét bên trong thành âm bản trắng trên đen, mặt và thân chung một khối, chỉ còn hai mắt lơ lửng |
| Xám than | Chọn: nét đen đọc theo quy ước thường, bụng xám nhạt hơn một bậc làm mảng sáng; khóc, liếm chân, hoảng sợ đều đọc ngay |
| Xanh dương | Đọc rõ và buồn cười, nhưng gần Doraemon, gần Tom, và đụng màu với kênh Mr. Nếu |
| Cam | Đọc rõ, nhưng béo, mí nặng, màu cam là chữ ký của Garfield |
| Be | Nhạt, mất chất |

Không chép dấu của kênh mèo tím đã xem (thân tím, bụng trắng hình bầu dục, dấu x ở rốn); chỉ lấy nguyên lý thân màu trung bình, nét đen, bụng sáng hơn.

**Tạo tờ gốc**: sinh bản mèo mun đứng, rồi sửa sang màu xám.

```text
A quick, deliberately crude hand-drawn doodle by an amateur Vietnamese YouTube storyteller, drawn fast, slightly off-model and not symmetrical. The whole image is the drawing itself, not a photo of a screen or any device. Black outer lines with uneven pressure, some strokes overshooting, some not fully closed. One character alone, full body, standing upright on two legs like a person, centered with lots of empty space around it: an anthropomorphic fat scruffy black cat. Its head is huge and flat, almost half of its body height, and its left ear has a ragged bite-shaped notch missing as its signature trait. Its eyes are two big white ovals with heavy half-closed lids and small black dot pupils, one eye slightly bigger than the other, giving a deeply unimpressed, judging stare straight at the viewer. A tiny flat mouth and a few long uneven whiskers drawn as thin white strokes on the black fur. A round pear-shaped belly, short stubby legs, simple mitten-like paws resting on its belly, and a thin tail with a sharp kink near the tip. Lines inside the black shape are thin white strokes. Solid flat black fur with no fur texture, no shading, no gradients, no highlights, no blush. No clothes. Plain solid flat pure white background. No written words.
```

```text
Edit the attached image. Keep the cat exactly the same: the same pose, the same body shape, the same notched left ear, the same kinked tail, the same eyes and expression. Change its fur to dark charcoal grey, clearly lighter than the black lines, as one flat fill, and its belly to a slightly lighter shade of the same color in a soft irregular shape with no marks on it. Redraw every line, both the outline and the inner lines such as the mouth, eyebrows, arms and paws, as black lines with uneven pressure, like normal cartoon line art. Do not change anything else.
```

**Luật khi mặc đồ và đổi biểu cảm**

- Mũ đặt giữa hai tai để vết sứt luôn lộ ra.
- Không gì được che mắt (bản cướp biển bịt mắt mất nửa câu đùa).
- Luôn sửa từ tờ gốc không mặc đồ; cần cả đồ lẫn biểu cảm thì chỉ chồng một lớp sửa.
- Tay chân chĩa ra ngoài, nổi trên nền, đừng đè lên bụng.

**Prompt mẫu trang phục: đội cờ đỏ** (đã kiểm, chuẩn)

```text
Edit the attached image. Keep the cat exactly the same: the same body, the same grey fur and lighter grey belly, the same notched left ear, the same kinked tail, the same uneven half-closed eyes, the same line style. Dress it as a Vietnamese school discipline monitor: a white school shirt, a red armband on its upper arm reading "CỜ ĐỎ", holding a small notebook in one paw and a pen in the other, squinting with suspicion as if it just caught someone breaking the rules. Nothing covers its eyes. The costume is drawn in the same crude doodle style with flat colors. Plain solid flat pure white background. Do not change anything else.
```

Đổi bộ đồ thì thay đoạn từ "Dress it as…" đến "…breaking the rules". Đổi biểu cảm thì dùng câu "Change only its expression and pose: …" thay cho câu mặc đồ.

**Kho ý tưởng**

| Loại | Ý tưởng | Trạng thái |
| --- | --- | --- |
| Trang phục | Cướp biển, Dracula | Đã ra (do sót ngoặc vuông, không chủ đích) |
| Trang phục | Giám khảo nấu ăn, quan tòa | Đã ra với bản xanh |
| Trang phục | Đội cờ đỏ | Prompt sẵn, đang chạy |
| Trang phục | MC "Ai là triệu phú", bảo vệ trường, siêu nhân tự chế, bán hàng livestream, quân vương, học sinh cấp ba quá khổ, cô chủ nhiệm, học bá, ngày tốt nghiệp, bác xe ôm | Chưa thử |
| Biểu cảm | Sốc SS, khóc tủi thân, liếm chân mặc kệ, ngủ gật bong bóng mũi, cáo già xoa tay | Đã ra; bản xám đọc rõ |
| Biểu cảm | Khinh bỉ tột độ, chê dở, nhận điểm 2 hồn lìa khỏi xác, bị gọi lên bảng, quay cóp cổ dài, chào cờ mắt chết | Chưa thử |
| Hành vi | Gạt cốc khỏi bàn | Chưa thử |
| Trong cảnh | Ngủ gục bàn cuối giảng đường, đứng bảng đen viết sai | Prompt sẵn, chưa chạy |

## Lỗi đã gặp

Phần lớn lỗi trong buổi này đến từ câu chữ của prompt, không phải từ Nano Banana: mô hình làm đúng từng chữ, kể cả chữ ta không định nói.

| Lỗi | Nguyên nhân | Cách tránh |
| --- | --- | --- |
| Nét "quá giỏi", trông nhựa | Tả phong cách thay vì tả người vẽ | Tả người vẽ nghiệp dư, cấm cụ thể: đổ bóng, chuyển sắc, ánh sáng, nếp vải, ửng má |
| Nền giấy ngả màu, tối dần ở mép | Thói quen làm đẹp của AI | Cấm paper texture và vignette, đòi nền phẳng đều |
| Vẽ thành ảnh chụp máy tính bảng | Cụm "drawn on a cheap drawing tablet" bị hiểu nghĩa đen | Bỏ cụm đó, thêm "the whole image is the drawing itself, not a photo of a screen or any device" |
| Tự dán nhãn LAPTOP, DUST lên đồ vật | Nhắc tên đồ vật là mô hình viết luôn tên | Chữ nào cần thì đưa nguyên văn trong ngoặc kép; chữ không cần thì không nhắc tên |
| Cảnh thật mất hồn, xám xịt | Luật "màu xỉn, cấm phát sáng, cấm chữ" của phông vẽ áp nhầm lên cảnh thật | Cảnh thật giữ màu gốc và chữ ký nơi chốn; ánh sáng vẽ thành mảng phẳng có viền tay |
| Gạch bôi đen quá dày | Không nói cách tô vùng tối | "The dark areas are flat solid color, not heavy scribbled hatching" |
| Đổi style mất danh tính (áo phông thành vest) | Chỉ khóa đạo cụ | Khóa thêm tóc, quần áo, màu |
| Thứ tự ảnh đính ngược | Prompt gọi "first", "second" | Đính đúng thứ tự prompt gọi tên |
| Tay vừa cầm đồ vừa nắm tay vịn | Tờ gốc có đồ trên tay | Nói rõ đồ đó biến mất |
| Ra cướp biển, Dracula thay vì đồ học đường | Sót ngoặc vuông chưa điền | Dùng prompt hoàn chỉnh; vẫn lạ thì mở cuộc trò chuyện mới |
| Bịt mắt che mất biểu cảm | Trang phục che mắt | "Nothing covers its eyes" |
| Mèo đen khó đọc | Âm bản, không có mảng trung gian | Chuyển sang xám than |
| Nhân vật trôi dần qua các lượt | Sửa chồng nhiều lớp | Luôn sửa từ tờ gốc |
| Người không ra người khi đứng cạnh mèo | Đầu trứng không mũi, không tai, không lông mày; con mèo lại có đủ | Giữ nét tay, trả lại cằm, tai, mũi một nét và lông mày cho người |

## Việc còn dở

Ba mảng lớn đã có nền móng, nhưng còn năm thứ chưa động tới mà tập đầu sẽ cần: âm thanh, ảnh thật cắt dán, bảng tier, thumbnail, và đóng gói tất cả vào dây chuyền.

**Chưa động tới**

- [ ] Âm thanh cho mỗi cú cắt và cú đổi style: chạy lại bản B và C có tiếng nhấn để so.
- [ ] Cắt dán ảnh thật: món đem ra xếp hạng dùng ảnh thật, nhân vật vẽ đặt lên ảnh chụp thật (cửa lớp, hành lang). Chưa thử tấm nào.
- [ ] Bảng tier vẽ tay bằng code: nét run, chữ S, A, B viết tay, để "ngôi nhà" của kênh cũng trông như có người vẽ.
- [ ] Thumbnail: kênh mèo tím dùng chữ viết tay to cùng nhân vật cosplay; chưa bàn hướng cho kênh mình.
- [ ] Đóng gói vào dây chuyền: lưu các khối style vào thư mục phong cách riêng của kênh, và làm một bản Minh Ý cho kênh xếp hạng, vì luật khác Sinh Viên Kinh Tế (được có chữ, sinh liền người với cảnh, mặc định được dùng ảnh thật).

**Đang dở**

- [ ] Chạy prompt đội cờ đỏ, nhận điểm 2, và mèo ngủ gục ở giảng đường.
- [ ] Thử thêm vũ khí đổi style ngoài manga, ít nhất kinh dị, cổ động và pixel.
- [ ] Cổng trường Chuyên Tuyên Quang: liệt kê chữ ký nơi chốn rồi chạy khuôn chuyển cảnh thật; thử cả hai đường cho biển tên trường.
- [ ] Chạy tờ gốc bản người cho cậu gánh team và năm kiểu thành viên, xếp cạnh mèo xám ở cỡ thumbnail, rồi thay người trong ba tấm "Ai là triệu phú".
- [ ] Kho khoảng mười tư thế thường trực cho mèo, sinh một lần dùng mãi.
- [ ] Mèo và cậu gánh team chung một cảnh, ví dụ mèo làm MC "Ai là triệu phú" ngồi ghế đối diện.

**Câu hỏi mở**

- Tên con mèo.
- Chỏm tóc dựng của cậu gánh team bị yếu đi khi vào cảnh; có khóa lại không nếu cậu thành nhân vật thường trực?
- Màu tím ám kín da cậu ở cảnh "Ai là triệu phú": giữ vì buồn cười, hay giảm?
- Danh sách đầy đủ các kiểu thành viên cho đề đầu tiên.
