# 📔 Day 06: Mô Hình OSI (P2) - Transport & Network Layer

## 🚚 1. Layer 4 - Transport Layer (Tiếp tục)
Tầng giao vận chịu trách nhiệm về cơ chế truyền tải gói tin cho các dịch vụ (Web, Mail, Video trực tuyến, Chat...). Tầng này phân chia thành 2 giao thức đối nghịch nhau:

### A. Giao thức TCP (Transmission Control Protocol)
* **Cơ chế:** Thiết lập kết nối trước khi truyền dữ liệu. Nếu thiết lập kết nối thành công thì mới tiến hành truyền dữ liệu, không thiết lập được thì không truyền.
* **Đặc điểm nổi bật:**
  * Đảm bảo tính toàn vẹn của dữ liệu tuyệt đối.
  * Có cơ chế đánh số thứ tự (stt) cho từng gói tin để bên nhận sắp xếp lại đúng vị trí.
  * Có cơ chế truyền tải lại gói tin nếu trong quá trình vận chuyển bị rơi rớt hoặc lỗi.

### B. Giao thức UDP (User Datagram Protocol)
* **Ứng dụng thực tế:** Thường dùng cho các lưu lượng truyền tải thời gian thực như **Video Call, Voice** (`Realtime`).
* **Đặc điểm:**
  * **KHÔNG** thiết lập kết nối trước khi truyền.
  * **KHÔNG** có cơ chế đánh số thứ tự (stt) cho gói tin.
  * **KHÔNG** có cơ chế truyền tải lại gói tin bị mất.
* **Hệ quả:** Không thể đảm bảo tính toàn vẹn của dữ liệu (gây ra hiện tượng thỉnh thoảng giật hình, vấp tiếng nhẹ).
* **Ưu điểm cốt lõi:** Tốc độ truyền tải dữ liệu nhanh hơn giao thức TCP rất nhiều do giảm thiểu được các gói tin kiểm tra thủ tục.

---

## 🌐 2. Layer 3 - Network Layer
Tầng mạng chịu trách nhiệm định hướng dòng dữ liệu đi qua các phân đoạn mạng khác nhau với 2 chức năng cốt lõi:
* **Định tuyến (Routing):** Thực hiện tìm đường đi và xác định đường đi tối ưu nhất để đưa gói tin tới đích.
* **Gán địa chỉ IP (Logical Addressing):** Cấp phát địa chỉ logic định danh cho thiết bị trong mạng.

---

## 🔗 3. Layer 2 - Data Link Layer
Tầng liên kết dữ liệu xử lý dòng dữ liệu trong phạm vi nội bộ:
* **Chức năng chính:** Truyền tải dữ liệu trong phạm vi hệ thống mạng nội bộ (LAN).
* **Kiểm tra lỗi gói tin:** Thực hiện kiểm tra gói tin trước khi chính thức đẩy xuống môi trường truyền dẫn vật lý.

---

## 🔌 4. Layer 1 - Physical Layer
* **Chức năng:** Chịu trách nhiệm truyền dẫn dòng dữ liệu thô qua các môi trường vật lý.

---

## 📦 5. Quá Trình Đóng Gói Dữ Liệu (Data Encapsulation)
* **Khái niệm:** Là quá trình đóng gói và gắn thêm các thông tin tiêu đề (Header) vào gói tin khi dịch chuyển tuần tự từ tầng trên xuống tầng dưới (**từ Layer 7 $\rightarrow$ Layer 2**).
* **Quá trình tại Source (Nguồn):** Thiết bị gửi sẽ trực tiếp thực hiện quá trình đóng gói Encapsulation này.
* **Vai trò của L2 (Frame Trailer):** Tại tầng Data Link, hệ thống sẽ chèn thêm một đoạn mã kiểm tra lỗi gọi là `Frame Trailer` ở đuôi gói tin để thực hiện check lỗi toàn bộ dữ liệu trước khi đẩy xuống Layer 1 phát đi.
