Mình là Long, chủ kênh Sinh Viên Kinh Tế. Phiên này mình muốn nghiên cứu tiếp phần dựng 3D (three.js bên trong HyperFrames) mà mình đã làm cùng Claude Code từ 21 đến 25/10.

Trước khi làm gì, đọc theo thứ tự:
1. `C:\hyperframestest\antigravity\LUAT-GOC.md`, rồi sổ tay `C:\hyperframestest\CLAUDE.md` như LUAT-GOC chỉ.
2. `C:\hyperframestest - antigravity\antigravity\BAN-GIAO-3D.md`: bàn giao toàn bộ phần 3D, gồm 6 dự án thử, công thức kỹ thuật đã chạy được trên máy, chỗ lệch DESIGN đang chờ mình quyết, các hướng còn mở.
3. `index.html` và `GHI-CHU.md` của `thu-3d-style` và `thu-3d-thienthach` trong workspace, để nắm lối viết mã trước khi viết gì mới.

Phạm vi và quyền trong phiên này:
- Workspace là `C:\hyperframestest - antigravity`. Chỉ ghi file trong thư mục này. Đọc sổ tay, DESIGN, skill ở `C:\hyperframestest` và `%USERPROFILE%\.claude\skills` thì được, nhưng không ghi vào đó, vì Claude Code đang làm song song ở `C:\hyperframestest`. Riêng phần 3D, điều này thay cho câu "không đụng ra ngoài C:\hyperframestest" trong LUAT-GOC.
- Giữ đủ luật cứng:
  - không xóa file nào; cần dọn thì liệt kê để mình tự xóa;
  - không cài gì khi chưa hỏi;
  - không gọi API tính tiền; `snapshot` luôn kèm `--describe false`;
  - `check`, `snapshot`, `render` kèm `HYPERFRAMES_BROWSER_PATH`;
  - gõ `npx.cmd`, dùng đúng bản hyperframes ghim trong `package.json`.
- Thử ý mới thì tạo dự án thử mới tên `thu-3d-<tên>` bằng cách chép một dự án thử có sẵn rồi sửa. Không sửa đè dự án cũ. Bản render đặt `_vN`, bản cũ giữ nguyên. Mỗi dự án có `GHI-CHU.md` ghi số liệu, nguồn, chỗ lệch DESIGN.
- Bản đồ có Biển Đông phải giữ Hoàng Sa, Trường Sa thuộc Việt Nam như BAN-GIAO-3D mục 3.5.
- Cây, người, khủng long, nhà cửa dựng bằng khối hình học chỉ là đồ tạm cho phép thử. Mỗi lần dùng thì ghi rõ trong GHI-CHU.

Đọc xong thì báo mình, khoảng 10 dòng:
- bạn hiểu trạng thái phần 3D thế nào;
- bản nào mình đã ưng;
- những chỗ đang lệch DESIGN chờ mình quyết.

Rồi đề xuất 2–3 hướng thử tiếp (lấy từ BAN-GIAO-3D mục 6 hoặc ý của bạn), mỗi hướng kèm lý do. Dừng chờ mình chọn, chưa dựng gì.
