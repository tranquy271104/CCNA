# ✏️ Day 02: Review & Practice (CLI Basic Operations)

## ❓ Câu Hỏi Ôn Tập (Self-Quiz)

**Câu 1:** Một kỹ sư mạng đang đứng ở mode `Router(config-if)#` và muốn quay nhanh về thẳng mode `Router#` để chạy lệnh lưu cấu hình. Kỹ sư đó nên gõ lệnh nào hoặc dùng tổ hợp phím nào nhanh nhất?
* *Trả lời:* Kỹ sư có thể gõ lệnh `end` hoặc bấm nhanh tổ hợp phím `Ctrl + C` / `Ctrl + Z`.

**Câu 2:** Tại sao các doanh nghiệp hiện nay lại nghiêm cấm sử dụng giao thức Telnet để cấu hình thiết bị từ xa? Thay vào đó họ bắt buộc phải dùng giao thức nào?
* *Trả lời:* Vì Telnet gửi toàn bộ gói tin (bao gồm cả Username/Password) dưới dạng văn bản thuần túy, không hề mã hóa. Kẻ xấu có thể dùng Wireshark để nghe lén dòng dữ liệu và lấy cắp tài khoản thiết bị. Do đó, doanh nghiệp bắt buộc phải thay thế bằng **SSH** để mã hóa toàn bộ đường truyền.

---

## 💻 Bài Tập Về Nhà (BTVN - Lab Scenario)

### Đề bài yêu cầu:
1. Thực hiện đặt tên thiết bị mạng (Router/Switch) lần lượt cho các thành viên trong nhóm: `HoangVD`, `TuTT`, `ThangND`.
2. Chụp lại kết quả chứng minh thiết bị đã được đổi tên khi đang đứng ở chế độ **User Mode** (`Router>`).

### 📝 Các bước triển khai bằng câu lệnh CLI:

#### Bước 1: Tiến hành đổi tên thiết bị thành `HoangVD`
```virl
Router> enable
Router# configure terminal
Router(config)# hostname HoangVD
HoangVD(config)# end
HoangVD# exit
HoangVD>
