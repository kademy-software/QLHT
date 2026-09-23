# QLHT - Hệ thống Quản lý Học tập Cá nhân

**Sinh viên thực hiện:** Lê Tuấn Kiệt - SE223216[cite: 1]
**Ngành:** An ninh mạng AI[cite: 1]
**Phiên bản Sao lưu:** 23/09/2026

## 📜 Tổng quan Dự án
QLHT là hệ thống quản lý học tập cá nhân được xây dựng bằng PHP và MySQL[cite: 1, 2], giúp sinh viên theo dõi tiến độ học tập, quản lý điểm số, lịch học, đơn từ FAP[cite: 1], và lộ trình tự học các chứng chỉ bảo mật bên ngoài một cách đồng bộ.

Bản sao lưu ngày 23/09/2026 ghi nhận toàn bộ các đợt nâng cấp cấu trúc cơ sở dữ liệu và giao diện mới nhất để phục vụ việc theo dõi song song chương trình chính khóa và các lộ trình thực chiến (đặc biệt là TryHackMe).

---

## 🚀 Các nâng cấp trong bản 23/09/2026

### 1. Cập nhật Cấu trúc Cơ sở dữ liệu (MySQL)
- **Quản lý Deadline:** Tích hợp bảng `deadlines` hỗ trợ quản lý bài tập, đồ án và các việc cần làm có thời hạn.
- **Theo dõi Tự học:** Thêm bảng `self_study_modules` để lưu trữ và theo dõi tiến độ học tập độc lập ngoài chương trình đại học.
- **Trạng thái Miễn môn:** Cập nhật kiểu dữ liệu cột `status` trong bảng `subjects` hỗ trợ thêm trạng thái `exempted` (Miễn môn).

### 2. Dữ liệu Học tập (Đã khởi tạo)
- **Chương trình Chính khóa:** Đã nhập toàn bộ lộ trình 54 môn học chuyên ngành từ kỳ -5 (Tiếng Anh chuẩn bị) đến kỳ 9. Tự động phân bổ trạng thái: Miễn môn, Đã hoàn thành (Passed), Đang học và Chưa bắt đầu.
- **Lộ trình TryHackMe:** Cập nhật lịch trình tự học thực chiến (từ Module 2 đến Module 14) với các mốc thời gian hoàn thành cụ thể cho từng ngày, bắt đầu từ 23/09/2026.

### 3. Giao diện & Tính năng mới (PHP/CSS/JS)
- **Trang Môn học (`subjects.php`):** 
  - Bổ sung bộ lọc trạng thái thời gian thực (Tất cả, Đang học, Passed, Miễn môn, Chưa bắt đầu) bằng JavaScript giúp tìm kiếm học phần nhanh chóng không cần tải lại trang.
  - Cập nhật hệ thống màu sắc nhận diện (`badge-purple`) cho các học phần được miễn.
- **Trang Dashboard (`index.php`):** 
  - Tích hợp widget **"Tự học tuần này"**, tự động trích xuất các bài TryHackMe cần hoàn thành từ Thứ 2 đến Chủ Nhật.
  - Hệ thống cảnh báo màu đỏ đối với các task trễ hạn và tự động gạch ngang nội dung các task đã chuyển sang trạng thái "Hoàn thành".
  - Hiển thị tỷ lệ và số lượng môn học đã "Passed" gộp chung với các môn "Miễn".

---

## ⚙️ Hướng dẫn cài đặt

1. **Cơ sở dữ liệu:**
   - Tạo database mới tên là `qlht` (Charset: `utf8mb4_unicode_ci`)[cite: 1].
   - Nhập (Import) tệp `database.sql` vào MySQL[cite: 1].
2. **Cấu hình Kết nối:**
   - Đảm bảo cấu hình file `config/auth.php` khớp với thông tin đăng nhập MySQL (User, Password, Database Name) trên server/localhost của bạn[cite: 2].
3. **Đăng nhập mặc định:**
   - **Mã số sinh viên:** `SE223216`[cite: 1]
   - **Mật khẩu:** `123456`[cite: 1]

---
*Phát triển và bảo trì cho lộ trình học tập cá nhân ngành An ninh mạng AI.*
