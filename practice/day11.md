# ✏️ Day 11: Review & Practice (IP Classes & ARP Mechanics)

## ❓ Câu Hỏi Ôn Tập (Self-Quiz)

**Câu 1:** Một thiết bị trong văn phòng của bạn được cấp IP là `192.168.10.15`. Địa chỉ này thuộc Lớp nào? Nó là IP Public hay Private? Máy tính này có thể trực tiếp gửi gói tin ra Google (`8.8.8.8`) mà không cần qua thiết bị NAT được không?
* *Trả lời:* * Địa chỉ `192.168.10.15` có Octet đầu là 192 $\rightarrow$ Thuộc **Lớp C**.
  * Nằm trong dải `192.168.0.0/16` $\rightarrow$ Đây là địa chỉ **IP Private**.
  * Máy tính này **KHÔNG THỂ** trực tiếp gửi gói tin ra Internet đến Google vì các Router trên Internet sẽ lập tức hủy (drop) các gói tin có IP nguồn là Private. Gói tin bắt buộc phải đi qua Router/Firewall tích hợp tính năng NAT để đổi sang IP Public trước khi ra ngoài.

**Câu 2:** Khi máy tính gửi gói tin `ARP Request` để tìm địa chỉ MAC, tại sao gói tin đó phải sử dụng phương thức truyền thông Broadcast (`FF-FF-FF-FF-FF-FF`) ở tầng Data Link?
* *Trả lời:* Vì tại thời điểm đó, máy tính nguồn hoàn toàn **chưa biết** địa chỉ MAC của thiết bị đích ở đâu để gửi đích danh (Unicast). Do đó, nó phải gửi Broadcast để tất cả các thiết bị trong phân đoạn mạng LAN cùng nhận và kiểm tra, thiết bị nào trùng IP đích yêu cầu thì mới đứng ra phản hồi.

---

## 📊 Bài Tập Thực Hành: Phân Tích Dải IP (IP Classification)

Hãy điền thông tin phân loại cho danh sách các IP dưới đây:

| Địa chỉ IP | Thuộc Lớp (Class) | Loại IP (Public / Private / Đặc biệt) | Default Subnet Mask |
| :--- | :---: | :---: | :---: |
| `10.50.1.1` | **A** | Private | `/8` |
| `172.35.4.2` | **B** | Public (Vì vượt quá dải private .31) | `/16` |
| `127.0.0.1` | **A** | Đặc biệt (Loopback) | `/8` |
| `192.168.5.100` | **C** | Private | `/24` |
| `224.0.0.5` | **D** | Đặc biệt (Multicast cho OSPF) | Không có |
