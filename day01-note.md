# 📔 Day 01: Giới Thiệu Network Tổng Quan

## 📌 Các Thành Phần Cốt Lõi Trong Mạng (Network Components)
Một hệ thống mạng hạ tầng được cấu thành từ 3 thành phần chính:
1. **Thiết bị đầu cuối (End Devices):** Máy tính (PC), Laptop, Máy in, Server, Điện thoại... Đây là nơi sinh ra và nhận dữ liệu.
2. **Thiết bị trung gian (Intermediary Devices):**
   * **Switch (Bộ chuyển mạch):** Kết nối các thiết bị trong cùng một mạng nội bộ (LAN). Hoạt động chủ yếu ở Layer 2.
   * **Router (Bộ định tuyến):** Kết nối các mạng khác nhau lại với nhau và tìm đường đi tối ưu cho gói tin trên Internet. Hoạt động ở Layer 3.
   * **Firewall (Tường lửa):** Giám sát và lọc lưu lượng truy cập dựa trên các quy tắc bảo mật.
3. **Môi trường truyền dẫn (Network Media):** Cáp đồng (Twisted-Pair), Cáp quang (Fiber-Optic), hoặc Sóng vô tuyến (Wireless).

## 🌐 Các Kiến Trúc Mạng Phổ Biến
* **LAN (Local Area Network):** Mạng cục bộ trong phạm vi nhỏ như văn phòng, tòa nhà, trường học. Tốc độ cao, băng thông lớn nhưng khoảng cách giới hạn.
* **WAN (Wide Area Network):** Mạng diện rộng kết nối các vùng địa lý cách xa nhau (giữa các tỉnh thành hoặc quốc gia). Thường được cung cấp bởi các nhà mạng viễn thông (ISP).

## 🔀 Phương Thức Truyền Tin (Delivery Methods)
* **Unicast:** Truyền tin từ một thiết bị nguồn đến **duy nhất một** thiết bị đích ($1 \rightarrow 1$).
* **Multicast:** Truyền tin từ một nguồn đến **một nhóm** thiết bị đích cụ thể trong mạng ($1 \rightarrow \text{Group}$).
* **Broadcast:** Truyền tin từ một nguồn đến **tất cả** các thiết bị trong cùng một phân đoạn mạng ($1 \rightarrow \text{All}$).
