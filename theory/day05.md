# 📔 Day 05: Mô Hình OSI & Tổng Quan Các Tầng

## 🔀 1. Các Kiểu Truyền Thông (Data Delivery Methods)
* **Unicast (1 vs 1):** Truyền tải dữ liệu từ một nguồn đến duy nhất một đích.
* **Multicast (1 vs group):** Truyền tải dữ liệu từ một nguồn đến một nhóm thiết bị chỉ định (không phải tất cả).
* **Broadcast (1 vs all):** Truyền tải dữ liệu từ một nguồn đến toàn bộ các thiết bị trong cùng một phân đoạn mạng.
* **Các thuật ngữ:**
  * `Source` (Nguồn): Thiết bị khởi tạo dữ liệu.
  * `Destination` (Đích): Thiết bị nhận dữ liệu.

---

## 🌐 2. Tổng Quan Về Mô Hình OSI (Open Systems Interconnection)
* **Khái niệm:** Là mô hình chuẩn chung quy định về giao thức, chuẩn kích cỡ... trong hệ thống mạng.
* **Tác dụng:** * Giúp đa dạng hóa các hãng công nghệ (không bị độc quyền).
  * Giúp linh kiện, thiết bị của các hãng khác nhau có thể kết nối và giao tiếp mượt mà với nhau.

---

## 🏗️ 3. Mô Hình Phân Cấp 7 Lớp Của OSI (7-Layer Model)


### 🏢 Các Tầng Ứng Dụng (Upper Layers)
* **Layer 7 - Application (Tầng ứng dụng):** Cung cấp các ứng dụng hỗ trợ giao diện người dùng để tạo dữ liệu.
* **Layer 6 - Presentation (Tầng trình diễn):** Cung cấp định dạng (Format), mã hóa và chuẩn hóa dữ liệu.
* **Layer 5 - Session (Tầng phiên):** Thiết lập, duy trì và kết thúc các phiên kết nối giữa hai thiết bị.

### 🚚 Các Tầng Dịch Chuyển (Lower Layers)
* **Layer 4 - Transport (Tầng giao vận):** Cơ chế truyền tải gói tin (Dành cho Web, Mail, Video trực tuyến, Chat...). Bao gồm 2 giao thức chính:
  * **TCP (Transmission Control Protocol):**
    * Thiết lập kết nối trước khi truyền (Nếu thiết lập được thì mới truyền, không thiết lập được thì không truyền).
    * Đảm bảo tính toàn vẹn của dữ liệu.
    * Có cơ chế đánh số thứ tự (stt) gói tin.
    * Có cơ chế truyền tải lại gói tin nếu bị mất.
  * **UDP (User Datagram Protocol):**
    * Thường dùng cho dữ liệu thời gian thực (Video, Voice -> Realtime).
    * Không thiết lập kết nối trước khi truyền.
    * Không có cơ chế đánh số thứ tự (stt) gói tin.
    * Không có cơ chế truyền tải lại gói tin bị mất -> Không thể đảm bảo tính toàn vẹn dữ liệu.
    * **Ưu điểm:** Tốc độ truyền tải dữ liệu nhanh hơn TCP rất nhiều.
* **Layer 3 - Network (Tầng mạng):** * Thực hiện định tuyến (Routing): Tìm đường đi và xác định đường đi tối ưu tới đích.
  * Thực hiện gán địa chỉ IP (Logical Addressing).
* **Layer 2 - Data Link (Tầng liên kết dữ liệu):**
  * Truyền tải dữ liệu trong hệ thống mạng nội bộ (LAN).
  * Kiểm tra lỗi gói tin trước khi đẩy xuống môi trường truyền dẫn vật lý (bằng trường `Frame Trailer` ở đuôi).
* **Layer 1 - Physical (Tầng vật lý):** Chịu trách nhiệm truyền dẫn các bit dữ liệu thô qua môi trường vật lý (Dây cáp, sóng vô tuyến).

---

## 📦 4. Quá Trình Đóng Gói Dữ Liệu (Data Encapsulation)
* **Khái niệm:** Là quá trình đóng gói gói tin chuyển dịch tuần tự từ **Layer 7 xuống Layer 2**.
* **Đặc điểm tại Source (Nguồn):** Thiết bị gửi sẽ trực tiếp thực hiện quá trình đóng gói Encapsulation này. Tại Layer 2, một thành phần gọi là `Frame Trailer` sẽ được thêm vào cuối gói tin để kiểm tra xem dữ liệu có bị lỗi hay biến dạng trước khi chính thức đẩy xuống Layer 1 để truyền đi hay không.
