# 📔 Day 03: OS & Basic Configuration (P2)

## ⌨️ 1. Mẹo & Phím Tắt Tối Ưu Tốc Độ Gõ Lệnh (CLI Efficiency)
* **Phím `Tab`:** Tự động hoàn thiện câu lệnh khi gõ đúng các chữ cái đầu.
* **Phím dấu hỏi `?`:** Hiển thị danh sách các câu lệnh hoặc tham số có thể gõ tiếp theo.
* **Các phím mũi tên ($\uparrow$ / $\downarrow$):** Di chuyển ngược/xuôi để xem lại lịch sử các lệnh đã gõ trước đó.
* **Quy tắc viết tắt (Abbreviation):** Cisco IOS cho phép viết tắt lệnh nếu cụm từ đó là duy nhất (Ví dụ: thay vì gõ đầy đủ `configure terminal`, bạn chỉ cần viết tắt là `conf t`).
> 💡 *Lời khuyên khi làm Lab:* Nên tận dụng tối đa phím `Tab` hoặc viết tắt để cấu hình nhanh hơn, không bắt buộc phải viết đầy đủ cả câu lệnh.

---

## 🔒 2. Cấu Hình Bảo Mật Mật Khẩu (Password Configuration)

### A. Mật khẩu truy cập vào Privileged Mode (`#`)
Cisco IOS cung cấp 2 câu lệnh để bảo vệ quyền truy cập cao cấp này:
1. `enable password <mật_khẩu>`: Đặt mật khẩu ở dạng văn bản thuần túy.
   * *Nhược điểm:* Khi dùng lệnh `show running-config` để xem file cấu hình hiện hành, mật khẩu sẽ hiển thị rõ mồn một (**clear-text**), rất dễ bị nhìn trộm.
2. `enable secret <mật_khẩu>`: Đặt mật khẩu sử dụng thuật toán mã hóa nâng cao.
   * *Ưu điểm:* Khi xem file cấu hình, mật khẩu sẽ bị băm thành một chuỗi ký tự lạ, cực kỳ bảo mật.
> 📌 *Quy tắc ghi đè:* Để đổi mật khẩu `enable mode`, bạn chỉ cần gõ lại chính câu lệnh đó với mật khẩu mới. Câu lệnh mới sẽ tự động viết đè và thay thế câu lệnh cũ.

### B. Mật khẩu cổng vật lý (Console Password)
Bắt buộc người dùng phải nhập đúng mật khẩu ngay khi vừa cắm dây cáp Console vào thiết bị:
* Câu lệnh thực hiện trên CLI:
    Router(config)# line console 0
    Router(config-line)# password tutt
    Router(config-line)# login

### C. Mã hóa toàn bộ mật khẩu rõ chữ trên hệ thống
* **Lệnh:** `service password-encryption`
* **Chức năng:** Tự động mã hóa tất cả các mật khẩu đang hiển thị dạng rõ chữ (như password của line console, hoặc `enable password`) trong file cấu hình, ngăn chặn hoàn toàn việc nhìn trộm màn hình.

---

## ⚠️ 3. Xử Lý Sự Cố Treo CLI & Xóa Cấu Hình

### A. Tình trạng treo màn hình dòng lệnh (CLI Freeze)
* **Nguyên nhân:** Khi đứng ở `User Mode` hoặc `Privileged Mode`, nếu gõ sai hoặc gõ nhầm một từ không phải là lệnh, Router sẽ lầm tưởng đó là một tên miền (Domain Name) và cố gắng thực hiện quá trình dịch tên miền (Domain Lookup). Quá trình này khiến màn hình CLI bị đơ/treo.
* **Thời gian treo:** Sẽ tự động hết và trả lại dòng lệnh sau khoảng 1 đến 2 phút.
* **Mẹo thoát lập tức:** Bấm tổ hợp phím **`Ctrl + Shift + 6`** để ép thiết bị dừng việc lookup và thoát khỏi tình trạng treo ngay tại chỗ.

### B. Cách xóa câu lệnh đã cấu hình
* **Quy tắc:** Muốn hủy bỏ hoặc xóa bất kỳ câu lệnh nào đã gõ, chỉ cần đứng đúng Mode của lệnh đó và thêm từ khóa **`no`** ở phía trước câu lệnh muốn xóa.

---

## 📢 4. Cấu Hình Tin Nhắn Chào Mừng (Banner MOTD)
Hiển thị thông báo cảnh báo bảo mật hoặc lời chào khi có người kết nối vào thiết bị:
* **Cách 1 (Gõ trên một dòng):** `banner motd "ABC"`
* **Cách 2 (Xuống dòng nhập văn bản dài):** Gõ `banner motd "` -> Nhấn `Enter` để xuống dòng gõ nội dung tùy ý -> Gõ ký tự kết thúc `"` để hoàn thành.

---

## 🔑 5. Xử Lý Khi Quên Mật Khẩu Thiết Bị (Password Recovery)
Khi bị mất hoặc quên pass truy cập thiết bị, chúng ta có 2 phương án giải quyết:
* **Cài lại OS:** Thiết bị quay về trạng thái xuất xưởng nhưng sẽ **mất sạch cấu hình cũ**.
* **Recovery pass:** Giúp lấy lại quyền truy cập mà **không mất cấu hình**. Mỗi dòng thiết bị phần cứng và dòng OS sẽ có một quy trình thực hiện khác nhau.

> 🔍 **Lệnh xem toàn bộ cấu hình hiện hành trên RAM:** `show running-config` (chỉ chạy ở Privileged Mode).
