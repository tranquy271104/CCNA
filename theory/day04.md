# 🛠️ Lab Day 04: Cấu Hình Thiết Bị & Kích Hoạt Cổng Router

## 📍 1. Sơ Đồ Topo Mạng (Topology)
Bài Lab này sử dụng một mô hình mạng cơ bản gồm 1 Router kết nối trực tiếp đến 1 Máy tính (PC) thông qua cổng FastEthernet.

* **Thiết bị trong Lab:**
  * Router R1 (Cisco 2911 hoặc dòng tương đương).
  * PC-01 (Máy tính chạy Windows giả lập).
* **Sơ đồ phân hoạch IP:**
  * Cổng `fa0/0` trên Router R1: IP `192.168.1.10` / Subnet Mask: `255.255.255.0`
  * Máy tính PC-01: IP `192.168.1.50` / Subnet Mask: `255.255.255.0`

---

## 📝 2. Các Bước Thực Hiện Cấu Hình (Lab Steps)

### Bước 1: Khởi động CLI và di chuyển vào chế độ cấu hình cổng
Bấm vào Router R1, chuyển sang tab **CLI** và gõ chuỗi lệnh sau để di chuyển vào cấu hình chi tiết cho cổng `fa0/0`:
* Câu lệnh thực thi:
    Router> enable
    Router# configure terminal
    Router(config)# interface fa0/0

### Bước 2: Kích hoạt cổng vật lý
Mặc định cổng Router sẽ báo đèn đỏ (Down). Bạn gõ lệnh sau để kích hoạt cổng (đèn sẽ chuyển sang màu xanh):
* Câu lệnh thực thi:
    Router(config-if)# no shutdown

### Bước 3: Gán địa chỉ IP cho cổng Router
Cấp địa chỉ IP cho cổng đóng vai trò làm Gateway quản lý đường truyền:
* Câu lệnh thực thi:
    Router(config-if)# ip address 192.168.1.10 255.255.255.0

### Bước 4: Lưu cấu hình vĩnh viễn vào NVRAM
Thoát ra chế độ đặc quyền và thực hiện ghi lại cấu hình tránh mất điện:
* Câu lệnh thực thi:
    Router(config-if)# end
    Router# write

---

## 🧪 3. Kiểm Tra Kết Quả (Verification)
1. Trên Router R1, đứng ở mode `Router#` gõ lệnh `show ip interface brief` để kiểm tra xem cổng `fa0/0` đã báo trạng thái `Status: Up / Protocol: Up` hay chưa.
2. Trên máy tính PC-01, cấu hình IP tĩnh là `192.168.1.50` (Subnet Mask: `255.255.255.0`).
3. Mở màn hình dòng lệnh (Command Prompt) của PC-01, gõ lệnh `ping 192.168.1.10` để kiểm tra kết nối thông suốt đến cổng Router.
