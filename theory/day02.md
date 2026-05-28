# 📔 Day 02: Hệ Điều Hành Mạng & Basic Configuration (P1)

## 🖥️ 1. Giao Diện Điều Khiển Thiết Bị (Management Interfaces)
Để cấu hình, thay đổi thông số hoặc quản trị thiết bị mạng, chúng ta có 2 loại giao diện chính:
* **GUI (Graphic User Interface - Giao diện đồ họa):** * Thân thiện, dễ sử dụng với người dùng phổ thông.
  * *Ví dụ:* Windows, iOS, Android, trang cấu hình Modem gia đình...
* **CLI (Command Line Interface - Giao diện dòng lệnh):**
  * Khó sử dụng hơn, đòi hỏi nhớ câu lệnh.
  * Là giao diện chuẩn bắt buộc đối với kỹ sư quản trị hạ tầng mạng chuyên nghiệp.

---

## 🔌 2. Phương Thức Truy cập Thiết Bị (Access Methods)

### A. Truy cập trực tiếp (Local Access) — Console
* **Cách thức:** Sử dụng dây cáp Console cắm trực tiếp từ máy tính quản trị vào cổng Console vật lý trên Router/Switch.
* **Ưu điểm:** Dễ dàng, kết nối trực tiếp không phụ thuộc vào cấu hình IP hay tình trạng mạng (dùng khi cứu hộ thiết bị hoặc cấu hình mới).
* **Nhược điểm:** Khoảng cách kết nối rất ngắn (bị giới hạn bởi độ dài dây cáp), thiếu tính linh hoạt.

### B. Truy cập từ xa (Remote Access) — Telnet & SSH
* **Ưu điểm:** Linh hoạt, không giới hạn khoảng cách địa lý, có thể ngồi từ xa quản trị thiết bị qua môi trường Internet.
* **Nhược điểm:** Cấu hình ban đầu khó khăn hơn, thiết bị phải có sẵn IP và thông mạng.
* **Bảo mật đường truyền:**
  * **Telnet:** **KHÔNG** mã hóa dữ liệu trên đường truyền $\rightarrow$ Rất nguy hiểm vì dễ bị bắt gói tin và lộ mật khẩu clear-text.
  * **SSH (Secure Shell):** **CÓ** mã hóa dữ liệu trên đường truyền $\rightarrow$ Bảo mật cao, là chuẩn thay thế hoàn toàn cho Telnet trong doanh nghiệp.

---

## 🎛️ 3. Các Chế Độ Hoản Trị Trong Cisco IOS (CLI Modes)


Hệ điều hành Cisco IOS phân tách quyền hạn và chức năng cấu hình theo cấu trúc phân cấp:

| CLI Mode | Ký Hiệu Dòng Lệnh | Đặc Điểm & Chức Năng | Lệnh Chuyển Mode |
| :--- | :--- | :--- | :--- |
| **User Mode** | `Router>` | Hiển thị một số thông số cơ bản. **Không thể** cấu hình hay thay đổi thông số thiết bị. | Mặc định khi khởi động |
| **Privileged Mode** | `Router#` | Chế độ đặc quyền. Xem được mọi thông số của thiết bị nhưng **không thể** cấu hình trực tiếp. | Gõ `enable` (từ User Mode) |
| **Config Mode** | `Router(config)#` | Chế độ cấu hình toàn cục. **Có thể** cấu hình và thay đổi mọi thông số của thiết bị. | Gõ `configure terminal` (từ Privileged Mode) |
| **Sub-config Mode** | `Router(config-if)#`<br>`Router(config-line)#` | Chế độ cấu hình chi tiết cho một phần nào đó của thiết bị (như Interface, Line Console,...). | Gõ lệnh chỉ định, ví dụ: `interface g0/0` |

### ⌨️ Các lệnh điều hướng và phím tắt (Commands & Shortcuts)
* `hostname <Tên>`: Lệnh đổi tên thiết bị (Ví dụ: `hostname TuTT`).
* `exit`: Lùi về chế độ (Mode) liền trước đó.
* `end`: Lùi thẳng từ bất kỳ đâu về lại chế độ đặc quyền `Privileged Mode` (`#`).
* Tổ hợp phím `Ctrl + C` hoặc `Ctrl + Z`: Đồng nghĩa với lệnh `end`, thoát nhanh về `Privileged Mode`.
