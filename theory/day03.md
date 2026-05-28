# 📔 Day 03: OS & Basic Configuration (P2)

## ⌨️ 1. Mẹo & Phím Tắt Tiết Kiệm Thời Gian (CLI Efficiency)
* **Phím `Tab`:** Tự động hoàn thiện câu lệnh.
* **Phím dấu hỏi `?`:** Hiển thị các từ hoặc tham số có thể gõ tiếp theo.
* **Các phím mũi tên ($\uparrow$ / $\downarrow$):** Xem lại lịch sử các câu lệnh đã gõ trước đó.
* **Quy tắc viết tắt (Abbreviation):** Cisco IOS cho phép viết tắt câu lệnh (Ví dụ: thay vì gõ `configure terminal`, bạn chỉ cần gõ `conf t`).
> 💡 *Lời khuyên khi làm Lab:* Nên tận dụng phím `Tab` hoặc viết tắt để tối ưu hóa tốc độ gõ lệnh, tránh việc phải gõ đầy đủ từng chữ.

---

## 🔒 2. Cấu Hình Bảo Mật Mật Khẩu (Password Configuration)

### A. Bảo mật khi truy cập vào Privileged Mode (`#`)
Chúng ta có 2 câu lệnh để đặt password bảo vệ quyền truy cập cao cấp này:
1. `enable password <mật_khẩu>`: Đặt mật khẩu dạng văn bản thuần túy.
   * *Nhược điểm:* Khi dùng lệnh `show running-config` để xem file cấu hình hiện hành, mật khẩu sẽ hiển thị rõ mồn một (**clear-text**), rất dễ bị lộ.
2. `enable secret <mật_khẩu>`: Đặt mật khẩu có mã hóa nâng cao (MD5/SHA).
   * *Ưu điểm:* Khi `show running-config`, mật khẩu sẽ bị băm thành một chuỗi ký tự lạ, không thể đọc được.
> 📌 *Quy tắc ghi đè:* Nếu cấu hình cả 2 lệnh trên cùng một thiết bị, câu lệnh đặt lại password mới sẽ tự động viết đè và thay thế câu lệnh cũ.

### B. Bảo mật cổng vật lý (Console Password)
Bắt buộc người dùng phải nhập mật khẩu ngay khi vừa cắm dây cáp Console vào thiết bị:
```virl
Router(config)# line console 0
Router(config-line)# password tutt
Router(config-line)# login
