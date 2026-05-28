# ✏️ Day 04: Review & Practice (Memory & Interface Lab)

## ❓ Câu Hỏi Ôn Tập (Self-Quiz)

**Câu 1:** Một kỹ sư mạng cấu hình xong Hostname, Mật khẩu và IP cho Router, thiết bị đang hoạt động rất tốt. Tuy nhiên, sau khi văn phòng bị mất điện và có lại, Router lại quay về trạng thái rỗng ban đầu (`Router>`). Kỹ sư đã quên bước nào?
* *Trả lời:* Kỹ sư mạng đã quên chạy lệnh `copy running-config startup-config` hoặc lệnh `write` để lưu cấu hình từ bộ nhớ tạm thời (RAM) vào bộ nhớ dài hạn (NVRAM).

**Câu 2:** Tại sao khi vừa cắm dây mạng từ máy tính vào cổng Router, đèn tín hiệu trên cổng Router vẫn báo màu đỏ (hoặc trạng thái Down), trong khi trên thiết bị Switch thì cắm vào là tự sáng đèn?
* *Trả lời:* Vì theo cơ chế bảo mật mặc định của Cisco, tất cả các cổng Interface của Router luôn ở trạng thái đóng (Down). Muốn cổng hoạt động, kỹ sư bắt buộc phải vào cấu hình cổng đó và gõ lệnh kích hoạt là `no shutdown`. Còn đối với Switch, các cổng mặc định luôn ở trạng thái mở (Up).

---

## 💻 Bài Tập Vận Dụng Cấu Hình Cổng (Interface Lab Scenario)

**Yêu cầu kịch bản:** Bạn cần cấu hình cổng FastEthernet `fa0/1` của một Router mới để làm cổng Gateway cho mạng nội bộ. Hãy viết chuỗi câu lệnh CLI thực hiện liên tục để đáp ứng các tiêu chí:
1. Vào chế độ cấu hình cổng `fa0/1`.
2. Bật cổng hoạt động.
3. Gán địa chỉ IP cho cổng là `192.168.1.1` với Subnet Mask là `255.255.255.0`.
4. Thoát ra và lưu cấu hình vĩnh viễn bằng lệnh ngắn gọn nhất.

### 📝 Chuỗi câu lệnh thực hiện hoàn chỉnh trên CLI:
* Tiến trình gõ lệnh cấu hình:
    Router> enable
    Router# configure terminal
    Router(config)# interface fa0/1
    Router(config-if)# no shutdown
    Router(config-if)# ip address 192.168.1.1 255.255.255.0
    Router(config-if)# end
    Router# write
