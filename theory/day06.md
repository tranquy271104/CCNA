# 📔 Day 06: OSI Model (P2) & Hệ Thống Số Nhị Phân - Thập Phân

## 🚚 1. Layer 4 - Transport Layer (Tiếp Tục)
Tầng giao vận chịu trách nhiệm về cơ chế truyền tải gói tin cho các dịch vụ (Web, Mail, Video trực tuyến, Chat...). Tầng này phân chia thành 2 giao thức chính:

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
* **Ưu điểm cốt lõi:** Tốc độ truyền tải dữ liệu nhanh hơn giao thức TCP rất nhiều do giảm thiểu được các gói tin kiểm tra thủ tục.

---

## 🌐 2. Tổng Quan Các Tầng Còn Lại (Layer 3 $\rightarrow$ Layer 1)
* **Layer 3 - Network Layer:** * Định tuyến (Routing): Tìm đường đi và xác định đường đi tối ưu nhất để đưa gói tin tới đích.
  * Gán địa chỉ IP (Logical Addressing).
* **Layer 2 - Data Link Layer:** Truyền tải dữ liệu trong hệ thống mạng nội bộ (LAN). Kiểm tra lỗi gói tin trước khi đẩy xuống môi trường vật lý.
* **Layer 1 - Physical Layer:** Chịu trách nhiệm truyền dẫn dòng dữ liệu thô (bit) qua các môi trường vật lý (Dây cáp, sóng vô tuyến).

---

## 📦 3. Quá Trình Đóng Gói Dữ Liệu (Data Encapsulation)
* **Khái niệm:** Là quá trình đóng gói và gắn thêm các thông tin tiêu đề (Header) vào gói tin khi dịch chuyển tuần tự từ tầng trên xuống tầng dưới (**từ Layer 7 $\rightarrow$ Layer 2**).
* **Quá trình tại Source (Nguồn):** Thiết bị gửi sẽ trực tiếp thực hiện quá trình đóng gói Encapsulation này.
* **Vai trò của L2 (Frame Trailer):** Tại tầng Data Link, hệ thống sẽ chèn thêm một đoạn mã kiểm tra lỗi gọi là `Frame Trailer` ở đuôi gói tin để thực hiện check lỗi toàn bộ dữ liệu trước khi đẩy xuống Layer 1 phát đi.

---

## 🔢 4. Cách Chuyển Đổi Hệ Số Nhị Phân & Thập Phân (Binary & Decimal)
Trong hạ tầng mạng, máy tính và các thiết bị phần cứng chỉ hiểu được hệ số Nhị phân, trong khi con người sử dụng hệ Thập phân để quản lý địa chỉ IP.

### A. Mẹo sử dụng bảng 8 Bit (Dãy số quyền lực)
Kỹ sư mạng luôn sử dụng giá trị của 8 vị trí bit (tính từ trái qua phải) tương ứng với các lũy thừa của cơ số 2 để tính toán nhanh:

| Vị trí Bit | Bit 1 | Bit 2 | Bit 3 | Bit 4 | Bit 5 | Bit 6 | Bit 7 | Bit 8 |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Giá trị Thập phân** | **128** | **64** | **32** | **16** | **8** | **4** | **2** | **1** |

> 📌 **Nguyên tắc cốt lõi:**
> * Nếu vị trí bit đó bằng `1` $\rightarrow$ Bạn **CỘNG** giá trị thập phân của vị trí đó vào.
> * Nếu vị trí bit đó bằng `0` $\rightarrow$ Bỏ qua (không cộng).

### B. Quy trình đổi từ Nhị phân $\rightarrow$ Thập phân
* **Ví dụ:** Đổi chuỗi 8 bit `11000000` sang Thập phân.
  * Đặt chuỗi bit vào bảng:
    128  |  64  |  32  |  16  |  8  |  4  |  2  |  1
     1   |   1  |   0  |   0  |  0  |  0  |  0  |  0
  * Tính toán: Chỉ cộng các vị trí có bit 1 $\rightarrow$ $128 + 64 = 192$.
  * Kết quả: `11000000` (Nhị phân) = `192` (Thập phân).

### C. Quy trình đổi từ Thập phân $\rightarrow$ Nhị phân
* **Phương pháp:** Lấy số Thập phân trừ dần từ trái qua phải của bảng giá trị. Nếu trừ được thì đặt bit `1`, không trừ được thì đặt bit `0` và xét tiếp số bên phải.
* **Ví dụ:** Đổi số Thập phân `168` sang Nhị phân.
  * Xét vị trí 128: $168 \ge 128$ $\rightarrow$ Trừ được ($168 - 128 = 40$) $\rightarrow$ Đặt bit **1**.
  * Xét vị trí 64: $40 < 64$ $\rightarrow$ Không trừ được $\rightarrow$ Đặt bit **0**.
  * Xét vị trí 32: $40 \ge 32$ $\rightarrow$ Trừ được ($40 - 32 = 8$) $\rightarrow$ Đặt bit **1**.
  * Xét vị trí 16: $8 < 16$ $\rightarrow$ Không trừ được $\rightarrow$ Đặt bit **0**.
  * Xét vị trí 8: $8 \ge 8$ $\rightarrow$ Trừ vừa hết ($8 - 8 = 0$) $\rightarrow$ Đặt bit **1**.
  * Các vị trí còn lại (`4`, `2`, `1`) đặt toàn bộ là bit **0**.
  * Kết quả: `168` (Thập phân) = `10101000` (Nhị phân).
