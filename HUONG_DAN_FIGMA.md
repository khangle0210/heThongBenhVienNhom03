# Hướng dẫn đưa giao diện vào Figma và nối mũi tên luồng

## 1. Trong gói này
- `IMPORT_1_khach-hang.html`  → 9 màn điện thoại (1.1–1.9), có sẵn mũi tên luồng vẽ trên bảng
- `IMPORT_2_nhan-vien.html`   → 6 màn máy tính (2.1–2.6)
- `IMPORT_3_kiosk.html`       → 6 màn kiosk dọc (K1–K6)
- `index.html` + thư mục `patient/ staff/ kiosk/` → 21 file lẻ, bấm thử được như web thật
- `luong-mui-ten.csv` → danh sách đầy đủ mũi tên (nút nào → màn nào)

## 2. Import vào Figma (miễn phí, mỗi lần 1 file)
1. Tạo file Figma Design mới. Plugins → Community → tìm **html.to.design** (by ‹div›RIOTS) → Run.
2. Tab **File** → kéo thả `IMPORT_1_khach-hang.html` (bản miễn phí chỉ nhận từng file một).
3. Ở mục Viewport, tick 1 kích thước rồi **bấm đúp để sửa** thành đúng chiều rộng bảng:
   - Khách hàng: **2230**  - Nhân viên: **5000**  - Kiosk: **5020**
4. Bật Use Autolayout, Add hyperlinks (tuỳ chọn) → Proceed. Lặp lại cho file 2 và 3.
5. Font: giao diện dùng **Inter** (có sẵn trong Figma). Nếu báo thiếu font: Update fonts.

## 3. Tách màn hình ra khung riêng (bắt buộc trước khi nối mũi tên)
Mũi tên prototype chỉ trỏ tới được khung cấp cao nhất.
1. Chọn khung lớn vừa import → **Ctrl/Cmd + Shift + G** (Ungroup) để các màn hình ra ngoài canvas.
2. Đổi tên từng khung theo nhãn (1.1, 1.2 … K1 …). Phần chữ nhãn và mũi tên đen/cam nằm cạnh chỉ là hình minh họa, giữ lại để đối chiếu.

## 4. Nối mũi tên prototype
1. Chọn tab **Prototype** (bên phải).
2. Chọn **nút** (không chọn cả khung) → kéo chấm tròn ở mép nút sang khung đích.
3. Bảng bên phải: Trigger **On click**, Action **Navigate to**, Animation: điện thoại dùng *Move in – Right*, máy tính/kiosk dùng *Instant*.
4. Nút "Cần hỗ trợ" lặp ở nhiều màn: chọn nhiều nút cùng lúc rồi kéo 1 lần sang 1.9 (hoặc K6).
5. Đặt **Flow starting point** (dấu ▶ cạnh tên khung) tại 1.1, 2.1, K1; bấm ▶ Present để chạy thử.

## 5. Bảng mũi tên
Xem `luong-mui-ten.csv` (44 dòng). Tóm tắt luồng chính:
- Khách hàng: 1.1 → 1.2 (Đã xem xong) → 1.3 (Xem đường đi) → 1.4 (Chọn lối đi dễ hơn, tùy chọn) → 1.5 (Bắt đầu đi) → 1.6 (Khi đến lượt) → 1.7 (Đã biết) → 1.8 (Tiếp theo); mọi màn → 1.9 (Cần hỗ trợ)
- Nhân viên: 2.1 → 2.2 → 2.3 → 2.4 → 2.5; 2.3 → 2.6 (Lỡ lượt)
- Kiosk: K1 → K2 (Quét QR) → K3 → K4 → K1 (Xong); K1 → K5 (Tôi không có mã) → K2; mọi màn → K6
- Liên kết giữa luồng: 2.1→1.2, 2.2→1.5, 2.3→1.5/1.6, 2.5→1.7, 1.9 & K6→2.6, 1.2→K1

Ghi chú: nút "Mô phỏng…" ở 1.5 và K1 chỉ để demo sự kiện hệ thống (gọi số, quét QR), có thể xoá hoặc thay bằng trigger After delay. Nút "Tôi đã đến nhà thuốc" ở 1.3 là đề xuất thêm để bỏ qua 1.4 (tùy chọn).
