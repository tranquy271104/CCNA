# 📔 Day 01: Giới Thiệu Network Tổng Quan

## 🧩 1. Các Thành Phần Trong Hệ Thống Network

### A. Host (End Device - Thiết bị đầu cuối)
Là các thiết bị có khả năng tự tạo ra, nhận hoặc xử lý dữ liệu trong mạng.
* **Ví dụ phổ biến:** PC, Laptop, Máy Fax, Máy in...
* **Các loại Server chuyên dụng:**
  * **Mail Server:** Quản lý và trung chuyển hệ thống thư điện tử.
  * **Web Server:** Lưu trữ và phân phối nội dung trang web đến người dùng.
  * **File Server:** Lưu trữ và quản lý tệp tin dùng chung trong mạng cục bộ.

### B. Thiết Bị Trung Gian (Intermediary Devices)
Nhiệm vụ kết nối các thiết bị đầu cuối và điều phối dòng dữ liệu.
* **Switch:** Bộ chuyển mạch kết nối các thiết bị trong mạng LAN.
* **Router:** Bộ định tuyến kết nối các phân đoạn mạng khác nhau, tìm đường đi tối ưu.
* **Modem:** Chuyển đổi tín hiệu (analog/digital) để kết nối với nhà mạng ISP.
* **Firewall:** Tường lửa bảo mật, lọc lưu lượng truy cập độc hại.

### C. Phương Tiện Truyền Dẫn (Network Media)

* **Dây đồng / Dây mạng / Dây LAN:** Truyền tải thông tin thông qua **tín hiệu điện**.
  * `Cat 5`: Băng thông tối đa $100\text{ Mbps}$, khoảng cách truyền tải tối đa vài chục mét.
  * `Cat 5e`: Băng thông tối đa $1000\text{ Mbps}$ ($1\text{ Gbps}$), khoảng cách truyền tải tối đa $100\text{ m}$.
  * `Cat 6`: Băng thông tối đa $10000\text{ Mbps}$ ($10\text{ Gbps}$), khoảng cách tối đa $100\text{ m}$, ít suy hao hơn.
* **Dây quang:** Truyền tải thông tin thông qua tín hiệu **ánh sáng**. Ưu điểm: truyền tải khoảng cách xa, cực kỳ ít suy hao.
* **Sóng không dây:** Truyền dữ liệu qua không gian (Wifi, Bluetooth, Hồng ngoại).

> 💡 **Khái niệm cốt lõi — Băng thông (Bandwidth):** Là lượng dữ liệu được truyền đi thành công trong một đơn vị thời gian. Đơn vị đo thông dụng là **Mbps** (*Megabit per second*).

---

## 🗺️ 2. Sơ Đồ Mạng (Topology)
Sơ đồ mạng (bản vẽ kỹ thuật) được chia làm 2 loại tách biệt hoàn toàn:
* **Physical Topology (Bản vẽ vật lý):** Thể hiện cách thức kết nối vật lý thực tế và vị trí đặt các thiết bị phần cứng trong không gian.
* **Logical Topology (Bản vẽ logic):** Thể hiện cách dữ liệu di chuyển qua các thiết bị dựa trên giao thức, chức năng mạng và sơ đồ địa chỉ (IP address).

---

## 🏆 3. Tiêu Chuẩn Trong Thiết Kế Hệ Thống Mạng
Một hạ tầng mạng doanh nghiệp đạt chuẩn bắt buộc phải đáp ứng 4 tiêu chí:
1. **Khả năng xử lý lỗi / Dự phòng (Fault Tolerance):** Hệ thống vẫn hoạt động bình thường ngay cả khi có một thiết bị hoặc đường truyền bị sự cố.
2. **Khả năng mở rộng (Scalability):** Dễ dàng thêm thiết bị mới, người dùng mới vào hệ thống mà không làm gián đoạn hay phải thiết kế lại mạng từ đầu.
3. **Chất lượng dịch vụ (QoS - Quality of Service):** Ưu tiên băng thông cho các lưu lượng quan trọng cần thời gian thực (như Voice, Video) để tránh hiện tượng trễ/giật lag.
4. **Bảo mật (Security):** Bảo vệ dữ liệu khỏi các truy cập trái phép và đảm bảo tính toàn vẹn của hệ thống.
