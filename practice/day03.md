# ✏️ Day 03: Review & Practice (Advanced Basic Config)

## ❓ Câu Hỏi Ôn Tập (Self-Quiz)

**Câu 1:** Bạn vô tình gõ nhầm chữ `conft` khi đang đứng ở mode `Router>`. Màn hình bỗng dưng bị đơ và hiển thị dòng chữ *Translating "conft"...*. Bạn cần làm gì để cứu nguy ngay lập tức?
* *Trả lời:* Bấm tổ hợp phím **`Ctrl + Shift + 6`** để ép thiết bị dừng việc dịch tên miền và trả lại quyền gõ lệnh ngay lập tức mà không cần đợi 2 phút.

**Câu 2:** Sau khi dùng lệnh `service password-encryption`, mật khẩu của `line console 0` có bị lộ khi chạy lệnh `show running-config` nữa không?
* *Trả lời:* Không. Lệnh này sẽ mã hóa toàn bộ mật khẩu dạng văn bản thuần túy thành các chuỗi số/ký tự băm (Type 7), giúp bảo mật an toàn trước hành vi nhìn trộm màn hình.

---

## 💻 Bài Tập Vận Dụng Lệnh CLI (Lab Scenario)

**Yêu cầu:** Hãy viết chuỗi lệnh cấu hình hoàn chỉnh cho một Router để:
1. Đặt thông báo hiển thị là `"CANH BAO: KHONG CO QUYEN TRUY CAP!"`.
2. Đặt mật khẩu mã hóa nâng cao cho Privileged Mode là `ccna123`.
3. Xóa bỏ mật khẩu Privileged Mode vừa đặt bằng lệnh ngắt.

### 📝 Chuỗi câu lệnh thực hiện hoàn chỉnh:
* Các lệnh gõ liên tục trên CLI:
    Router> enable
    Router# configure terminal
    Router(config)# banner motd "CANH BAO: KHONG CO QUYEN TRUY CAP!"
    Router(config)# enable secret ccna123
    Router(config)# no enable secret ccna123
    Router(config)# end
    Router#
