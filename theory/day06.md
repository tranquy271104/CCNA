# 📔 Day 06: Tổng Quan Các Giao Thức Mạng Tiêu Biểu (DHCP, DNS, HTTP/HTTPS)

## 🔌 1. Giao Thức Cấp Phát IP Tự Động - DHCP (Dynamic Host Configuration Protocol)
* **Khái niệm:** Là giao thức tự động cấu hình và cấp phát địa chỉ IP, Subnet Mask, Default Gateway và DNS Server cho các thiết bị trong mạng (PC, Laptop, Điện thoại...).
* **Lợi ích:** Tiết kiệm thời gian cấu hình thủ công cho quản trị viên, tránh việc cấu hình sai hoặc trùng lặp IP gây xung đột (IP Conflict).
* **Cơ chế hoạt động:** Hoạt động theo mô hình Client - Server và sử dụng giao thức **UDP** ở Layer 4 với 2 cổng:
  * Port `67`: Dành cho DHCP Server.
  * Port `68`: Dành cho DHCP Client.

### 🔄 Quy trình bắt tay 4 bước DHCP (DORA Process)
Khi một máy tính kết nối vào mạng, nó sẽ tìm kiếm Server và lấy IP qua 4 bước tuần tự:
1. **D - Discover (Phát hiện):** Client gửi gói tin Broadcast (đến tất cả thiết bị) để tìm xem trong mạng có DHCP Server nào không.
2. **O - Offer (Đề nghị):** DHCP Server nhận được gói tin, lựa chọn một địa chỉ IP còn trống trong kho và gửi gói tin Unicast (hoặc Broadcast tùy cấu hình) để đề nghị cấp IP này cho Client.
3. **R - Request (Yêu cầu):** Client nhận được lời mời, nó phản hồi lại bằng gói tin Broadcast để chính thức thông báo: "Tôi đồng ý lấy địa chỉ IP này từ Server".
4. **A - Acknowledge (Xác nhận):** Server gửi gói tin Unicast xác nhận, chính thức cho phép Client thuê địa chỉ IP đó và bắt đầu sử dụng.

---

## 📑 2. Giao Thức Phân Giải Tên Miền - DNS (Domain Name System)
* **Khái niệm:** Là hệ thống dịch thuật trong mạng Internet, chịu trách nhiệm chuyển đổi từ **Tên miền** (dễ nhớ cho con người) sang **Địa chỉ IP** (để máy tính hiểu và định tuyến).
  * *Ví dụ:* Khi bạn gõ tên miền `google.com`, DNS sẽ dịch thành địa chỉ IP `8.8.8.8` hoặc `172.217.24.14`.
* **Cơ chế hoạt động:** Sử dụng giao thức **UDP** trên Port **`53`**.

---

## 🌐 3. Giao Thức Duyệt Web - HTTP & HTTPS (Hypertext Transfer Protocol)
* **HTTP:**
  * Là giao thức truyền tải văn bản siêu văn bản thô để hiển thị trang web.
  * Hoạt động dựa trên giao thức **TCP** bảo đảm an toàn dữ liệu trên Port **`80`**.
  * **Nhược điểm:** Dữ liệu truyền đi không được mã hóa (Clear-text), rất dễ bị hacker chặn bắt và đọc trộm thông tin tài khoản.
* **HTTPS (HTTP Secure):**
  * Phiên bản nâng cấp bảo mật của HTTP, sử dụng thêm các chứng chỉ mã hóa dữ liệu (SSL/TLS).
  * Hoạt động dựa trên giao thức **TCP** trên Port **`443`**.
  * **Ưu điểm:** Toàn bộ dòng dữ liệu truyền đi giữa máy tính và máy chủ web đều được mã hóa, bảo mật tuyệt đối thông tin người dùng.
