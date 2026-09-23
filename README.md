# QLHT — Hệ thống Quản lý Học tập Cá nhân
Sinh viên: **Lê Tuấn Kiệt** — MSSV **SE223216** — Ngành **An ninh mạng AI**

Giao diện được thiết kế theo phong cách dashboard tối màu (dark theme), lấy cảm hứng
từ bố cục TryHackMe: topbar điều hướng, thẻ (card) bo góc, thanh tiến độ, badge trạng thái.

## Công nghệ
- PHP 8 (thuần, không framework) — PDO cho MySQL
- MySQL / MariaDB
- HTML5, CSS3 (vanilla), JavaScript (vanilla, Fetch API, Drag & Drop API)

## Tính năng
1. **Quản lý môn học** — thêm/sửa/xoá môn, đánh dấu học kỳ, trạng thái, giảng viên.
2. **Quản lý điểm** — thêm đầu điểm (Quiz/PE/FE...), nhập điểm, tự tính điểm tổng kết theo trọng số.
3. **Lịch học dạng lưới Slot 1–10** — kéo-thả môn học từ danh sách vào từng ô (Thứ 2–Thứ 7 × Slot 1–10),
   kéo để di chuyển giữa các ô, nhấp đúp để đặt phòng, bấm ✕ để gỡ khỏi lịch.
4. **Quản lý môn học Online** — danh sách môn Online kèm nền tảng (Teams/Zoom/Meet) và link vào lớp nhanh.
5. **Quản lý điểm danh** — ghi nhận có mặt/trễ/vắng theo từng buổi, thống kê tỉ lệ chuyên cần theo môn.
6. **Đơn gửi trên FAP** — tạo và theo dõi trạng thái các đơn (xin nghỉ, phúc khảo, bảo lưu...).

## Cài đặt (XAMPP / Laragon / PHP built-in server)

1. Import cơ sở dữ liệu:
   ```
   mysql -u root -p < database.sql
   ```
   (script đã tạo sẵn database `qlht`, 1 tài khoản mẫu và dữ liệu mẫu)

2. Mở `config/database.php` và chỉnh lại `DB_HOST`, `DB_USER`, `DB_PASS` cho đúng môi trường của bạn.

3. Chạy thử nhanh bằng PHP built-in server (từ thư mục gốc dự án):
   ```
   php -S localhost:8000
   ```
   Rồi mở trình duyệt tại `http://localhost:8000`

   Hoặc copy toàn bộ thư mục vào `htdocs` (XAMPP) / `www` (Laragon) và truy cập qua Apache.

4. Đăng nhập với tài khoản mẫu:
   - **MSSV:** `SE223216`
   - **Mật khẩu:** `123456`

   → Vào trang **Hồ sơ** để đổi mật khẩu khác sau khi đăng nhập lần đầu.

## Cấu trúc thư mục
```
qlht/
├── api/                # Cac endpoint JSON (subjects, grades, schedule, attendance, fap)
├── assets/css/         # style.css - theme dark/green
├── assets/js/          # JS tuong tac cho tung trang (fetch API, drag & drop)
├── config/             # Ket noi DB + xu ly dang nhap/phien
├── includes/           # header.php (topbar) / footer.php dung chung
├── database.sql        # Schema + du lieu mau
├── index.php            # Dashboard
├── subjects.php         # Quan ly mon hoc
├── grades.php            # Quan ly diem
├── schedule.php           # Lich hoc keo-tha slot 1-10
├── attendance.php         # Diem danh
├── online.php              # Mon hoc online
├── fap.php                  # Don FAP
├── profile.php               # Ho so / doi mat khau
├── login.php / logout.php
```

## Ghi chú bảo mật khi triển khai thật
- Đổi mật khẩu mẫu ngay sau khi cài đặt.
- Đặt `session.cookie_secure` và bật HTTPS nếu deploy lên server công khai.
- Thư mục `uploads/` dùng để lưu file đính kèm đơn FAP nếu bạn mở rộng tính năng upload file.
