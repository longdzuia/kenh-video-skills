# Kênh video: skill, hướng dẫn, kinh nghiệm

Repo chia sẻ **bộ não** dựng video bằng HyperFrames: skill cho Claude Code, sổ tay phong cách và các bài học rút ra khi làm.

**Quy tắc của repo:** chỉ chứa skill, hướng dẫn và kinh nghiệm mới. Không đưa video, ảnh, âm thanh hay file output lên đây (đã chặn trong `.gitignore`). Không đưa khóa API (`.env`).

## Có gì trong này

| Thư mục | Nội dung |
|---|---|
| `skills/minh-y` | Chuẩn bị nguyên liệu: phân việc từng dòng, gom sân khấu, viết prompt ảnh nhân vật/đồ vật/nền. |
| `skills/nhip-hf` | Chia mạch và tách dòng kịch bản tiếng Việt cho dây chuyền 100% HyperFrames. |
| `guides/hyperframestest` | Luật gốc, hướng dẫn công cụ, nhật ký thay đổi của dự án HyperFrames. |
| `guides/kenh-xep-hang` | Sổ tay style, khuôn prompt ảnh, ghi chú của kênh xếp hạng. |

## Cách dùng

**Cách 1: cài như plugin (nên dùng, cập nhật dễ)**
```
/plugin marketplace add longdzuia/kenh-video-skills
/plugin install kenh-video-skills@kenh-video
```
Khi có bản mới: `/plugin marketplace update kenh-video`.

**Cách 2: chép tay**
Clone repo, chép thư mục trong `skills/` vào `~/.claude/skills/` (dùng mọi project) hoặc `<project>/.claude/skills/` (chỉ project đó).

## Đóng góp

Tạo nhánh, sửa, mở Pull Request. Ghi rõ đã học được gì và vì sao đổi. Trước khi commit, kiểm tra không có khóa API, đường dẫn máy cá nhân, hay file output.

## Lưu ý

Một số hướng dẫn nhắc tới đường dẫn như `C:\hyperframestest`; đổi theo thư mục làm việc của bạn. Một số hướng dẫn nhắc tới công cụ cục bộ (`cong-cu`, `tools`) không nằm trong repo này.

