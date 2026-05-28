# ✏️ Day 01: Review & Practice (Network Fundamentals)

## ❓ Câu Hỏi Ôn Tập (Self-Quiz)

**Câu 1:** Phân biệt sự khác nhau giữa `Physical Topology` và `Logical Topology` bằng một ví dụ thực tế?
* *Trả lời:* * `Physical Topology` giống như việc bạn vẽ vị trí chiếc Switch đặt ở phòng server tầng 1, có dây cáp kéo lên chiếc PC ở bàn làm việc tầng 2.
  * `Logical Topology` không quan tâm dây cáp đi qua tường thế nào, nó chỉ thể hiện chiếc PC đó thuộc VLAN nào và đang mang địa chỉ IP là bao nhiêu để giao tiếp với Switch.

**Câu 2:** Một văn phòng có nhu cầu truyền tải dữ liệu nội bộ tốc độ cao lên tới $1\text{ Gbps}$ giữa các phòng ban cách nhau khoảng $50\text{ m}$. Bạn sẽ tư vấn sử dụng loại cáp mạng nào tối ưu nhất về chi phí và kỹ thuật?
* *Trả lời:* Sử dụng cáp mạng **Cat 5e** là tối ưu nhất. Vì Cat 5e hỗ trợ băng thông tối đa $1000\text{ Mbps}$ ($1\text{ Gbps}$) ở khoảng cách lên tới $100\text{ m}$, hoàn toàn đáp ứng được nhu cầu mà chi phí lại rẻ hơn cáp Cat 6.

---

## 🧠 Thử Thách Phân Tích Hệ Thống (Fault Tolerance Challenge)

**Tình huống:** Hãy nhìn vào tiêu chuẩn **"Khả năng xử lý lỗi, dự phòng (Fault Tolerance)"** đã học. Nếu một sơ đồ mạng chỉ có duy nhất 1 Router kết nối ra Internet độc đạo, mạng đó có đạt chuẩn Fault Tolerance không? Nếu Router đó bị cháy nguồn thì điều gì xảy ra?

👉 *Phân tích giải pháp:* Mạng này **không đạt chuẩn** dự phòng vì nó dính lỗi "Single Point of Failure" (điểm chết duy nhất). Nếu Router cháy, toàn bộ văn phòng mất Internet. Để đạt chuẩn thiết kế chuyên nghiệp, kỹ sư mạng sẽ cấu hình thêm một Router số 2 chạy dự phòng (Sử dụng các công nghệ như HSRP/VRRP mà bạn sẽ học ở Kì 3).
