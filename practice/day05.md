# ✏️ Day 05: Review & Practice (OSI Model Fundamentals)

## ❓ Câu Hỏi Ôn Tập (Self-Quiz)

**Câu 1:** Cuộc gọi video call (Zalo, Messenger) hoặc xem livestream bóng đá thường chấp nhận việc thỉnh thoảng bị vấp/mờ hình một chút nhưng không được phép bị chậm hay giật lag. Ứng dụng này đang sử dụng giao thức truyền tải nào ở Layer 4? Tại sao?
* *Trả lời:* Ứng dụng đang sử dụng giao thức **UDP**. Vì các dịch vụ thời gian thực (Realtime) cần tốc độ truyền tải cực nhanh. UDP không tốn thời gian thiết lập kết nối, không đánh số thứ tự hay truyền lại gói tin lỗi, giúp tối ưu hóa tốc độ cao nhất, dù phải đánh đổi bằng việc mất một vài gói tin (gây mờ/vấp hình nhẹ).

**Câu 2:** Quá trình đóng gói dữ liệu (Encapsulation) được diễn ra tại thiết bị nguồn (Source) hay thiết bị đích (Destination)? Vai trò của thành phần `Frame Trailer` ở Layer 2 là gì?
* *Trả lời:* Quá trình Encapsulation diễn ra tại thiết bị nguồn (**Source**). Thành phần `Frame Trailer` được thêm vào cuối gói tin ở Layer 2 có vai trò kiểm tra tính toàn vẹn và phát hiện lỗi của gói tin trước khi nó được chuyển xuống Layer 1 để đẩy ra môi trường truyền dẫn.

---

## 🧠 Thử Thách Tư Duy Thiết Kế Mạng (Scenario Analysis)

**Tình huống phân tích:** Hãy tưởng tượng nếu thế giới không có mô hình chuẩn chung OSI mà các hãng tự phát triển thiết bị theo quy chuẩn riêng. Khi công ty của bạn mua một chiếc Switch của hãng Cisco và một cụm máy in của hãng HP, điều gì sẽ xảy ra? Tầng nào trong mô hình OSI đảm bảo cho việc hai thiết bị này vẫn nói chuyện được với nhau?

👉 *Phân tích giải pháp:* * Nếu không có mô hình OSI, thiết bị của Cisco và HP sẽ sử dụng các tập lệnh và cấu trúc gói tin khác nhau, dẫn đến việc chúng hoàn toàn **không thể kết nối giao tiếp được với nhau** (mạng bị cô lập theo hãng).
* Nhờ có mô hình chuẩn chung **OSI**, các quy chuẩn về định dạng và truyền tải dữ liệu được thống nhất hóa toàn cầu, giúp linh kiện và thiết bị của tất cả các hãng công nghệ đa dạng có thể kết nối giao tiếp mượt mà.
