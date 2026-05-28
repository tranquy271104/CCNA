# 📔 Day 11: Phân Loại Địa Chỉ IPv4 & Tổng Quan Giao Thức ARP

## 🏷️ 1. Các Lớp Địa Chỉ IPv4 Định Danh (Classful IP Addressing)
Theo kiến trúc thiết kế ban đầu, địa chỉ IPv4 được chia thành các Class dựa vào giá trị của Octet đầu tiên:

* **Lớp A (Class A):** Chạy từ `1.0.0.0` $\rightarrow$ `126.255.255.255`. Default Subnet Mask là `/8`.
* **Lớp B (Class B):** Chạy từ `128.0.0.0` $\rightarrow$ `191.255.255.255`. Default Subnet Mask là `/16`.
* **Lớp C (Class C):** Chạy từ `192.0.0.0` $\rightarrow$ `223.255.255.255`. Default Subnet Mask là `/24`.
* **Lớp D (Class D):** Chạy từ `224.0.0.0` $\rightarrow$ `239.255.255.255`. Dùng cho mục đích **Multicast** (Truyền thông một nhóm).
* **Lớp E (Class E):** Chạy từ `240.0.0.0` $\rightarrow$ `255.255.255.255`. Dùng cho mục đích nghiên cứu, thử nghiệm (Experimental).

> ⚠️ **Dải đặc biệt bị bỏ qua:** Dải `127.0.0.0/8` (từ `127.0.0.1` $\rightarrow$ `127.255.255.254`) được gọi là **Loopback Address**. Địa chỉ này đại diện cho chính thiết bị nội bộ cục bộ, dùng để kiểm tra xem driver và card mạng (NIC) có đang hoạt động bình thường hay không (`ping 127.0.0.1`).

---

## 🔒 2. Phân Biệt IP Public Và IP Private
Để tiết kiệm không gian địa chỉ IPv4 đang cạn kiệt, tổ chức quốc tế đã chia IP thành 2 loại chính:

### A. IP Public (Địa chỉ dùng chung toàn cầu)
* Sử dụng để định danh thiết bị trực tiếp trên môi trường Internet quốc tế.
* Các địa chỉ này là duy nhất (không được trùng lặp) và phải thuê/mua từ các nhà mạng (ISP).

### B. IP Private (Địa chỉ dùng trong mạng nội bộ)
* Sử dụng tự do và miễn phí bên trong mạng LAN của các tổ chức, doanh nghiệp, gia đình.
* **Quy tắc cốt lõi:** IP Private **KHÔNG** được phép định tuyến và đi ra ngoài môi trường Internet. Muốn ra Internet, bắt buộc phải đi qua một thiết bị chạy tính năng **NAT (Network Address Translation)** để chuyển đổi thành IP Public.
* **Các dải IP Private chuẩn quốc tế (RFC 1918):**
  * Lớp A: `10.0.0.0` $\rightarrow$ `10.255.255.255` (`10.0.0.0/8`)
  * Lớp B: `172.16.0.0` $\rightarrow$ `172.31.255.255` (`172.16.0.0/12`)
  * Lớp C: `192.168.0.0` $\rightarrow$ `192.168.255.255` (`192.168.0.0/16`)

---

## 🔄 3. Giao Thức Phân Giải Địa Chỉ ARP (Address Resolution Protocol)
ARP là giao thức nền tảng giúp ánh xạ, chuyển đổi từ địa chỉ logic tầng mạng sang địa chỉ vật lý tầng liên kết dữ liệu (**Đổi từ IP $\rightarrow$ MAC**).

### A. Tại sao cần ARP?
Khi một máy tính nguồn biết IP đích nhưng chưa biết địa chỉ MAC đích của thiết bị trong cùng mạng LAN, nó không thể đóng gói Frame ở Layer 2 để gửi đi. Nó bắt buộc phải dùng ARP để tìm kiếm.

### B. Cơ chế hoạt động của gói tin ARP
Quá trình tìm kiếm diễn ra qua 2 bước:
1. **ARP Request (Yêu cầu):** Máy nguồn gửi một gói tin quảng bá (**Broadcast**) ở Layer 2 với địa chỉ MAC đích là `FF-FF-FF-FF-FF-FF`. Tất cả các máy trong mạng LAN đều nhận được, gói tin hỏi: *"Ai có địa chỉ IP này thì trả lời cho tôi biết MAC của bạn?"*.
2. **ARP Reply (Phản hồi):** Thiết bị sở hữu đúng địa chỉ IP được hỏi sẽ gửi trả lời trực tiếp (**Unicast**) về cho máy nguồn để cung cấp địa chỉ MAC của nó. Máy nguồn lưu thông tin này vào bộ nhớ tạm gọi là `ARP Cache`.
