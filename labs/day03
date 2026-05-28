# 🛠️ Lab Day 03: Thiết Lập Hệ Thống Bảo Mật Mật Khẩu Cho Thiết Bị

## 📍 1. Mục Tiêu Bài Lab (Lab Objectives)
* Thực hành cấu hình chuỗi mật khẩu bảo vệ thiết bị bao gồm: `Enable Secret` và `Console Password`.
* Kiểm tra tính năng mã hóa mật khẩu toàn cục bằng lệnh `service password-encryption`.
* Thực hành xử lý tình huống gõ sai câu lệnh bị treo màn hình CLI bằng phím tắt.

---

## 📝 2. Các Bước Thực Hiện Cấu Hình (Lab Steps)

### Bước 1: Cấu hình đặt tên và thông báo cảnh báo (Banner MOTD)
Bấm vào Router, di chuyển từ User Mode lên Config Mode và gõ chuỗi lệnh sau:
* Câu lệnh thực thi:
    Router> enable
    Router# configure terminal
    Router(config)# hostname R1-Secure
    R1-Secure(config)# banner motd "CAMH BAO: KHONG PHAI QUAN TRI VIEN CAM V REO! "

### Bước 2: Thiết lập mật khẩu mã hóa cho Privileged Mode
Đặt mật khẩu bảo mật cao để chặn người lạ can thiệp sâu vào hệ thống:
* Câu lệnh thực thi:
    R1-Secure(config)# enable secret tutt123

### Bước 3: Cấu hình mật khẩu khóa cổng Console vật lý
Cài đặt mật khẩu chặn truy cập trực tiếp ngay khi cắm dây cáp vào thiết bị:
* Câu lệnh thực thi:
    R1-Secure(config)# line console 0
    R1-Secure(config-line)# password tutt
    R1-Secure(config-line)# login
    R1-Secure(config-line)# exit

### Bước 4: Kích hoạt mã hóa toàn bộ mật khẩu rõ chữ
Chạy lệnh băm toàn bộ mật khẩu trên file cấu hình hiện hành để chống nhìn trộm:
* Câu lệnh thực thi:
    R1-Secure(config)# service password-encryption
    R1-Secure(config)# end

---

## 🧪 3. Kiểm Tra & Xử Lý Sự Cố (Verification & Troubleshooting)

### Tình huống 1: Kiểm tra file cấu hình (Show Run)
Tại mode `R1-Secure#`, gõ lệnh `show running-config`. Bạn kéo xuống kiểm tra xem phần mật khẩu cổng `line console 0` đã bị biến thành một chuỗi ký tự băm ngẫu nhiên hay chưa. Nếu đã bị băm (không còn chữ `tutt` rõ ràng) là cấu hình thành công.

### Tình huống 2: Test phím tắt cứu nguy khi CLI bị treo
1. Tại mode `R1-Secure#`, gõ lệnh `exit` để lùi ra ngoài `R1-Secure>`.
2. Tại đây, bạn cố tình gõ đại một cụm từ sai (Ví dụ: gõ chữ `tutt`).
3. Màn hình dòng lệnh ngay lập tức bị đơ và hiển thị thông báo *Translating "tutt"...*.
4. **Hành động:** Nhấn ngay tổ hợp phím **`Ctrl + Shift + 6`** trên bàn phím. Nếu dòng lệnh bị ép dừng dịch tên miền và trả lại quyền gõ ngay lập tức là bạn đã làm chủ phím tắt thành công.
