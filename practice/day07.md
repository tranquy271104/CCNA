# ✏️ Day 07: Review & Practice (Subnet & IP Structure)

## ❓ Câu Hỏi Ôn Tập (Self-Quiz)

**Câu 1:** Một địa chỉ IPv4 bao gồm bao nhiêu bit nhị phân và được chia làm mấy Octet? Giá trị thập phân tối đa của một Octet là bao nhiêu và tại sao có con số đó?
* *Trả lời:* Địa chỉ IPv4 gồm **32 bit nhị phân**, chia làm **4 Octet** (mỗi octet 8 bit). Giá trị thập phân tối đa của một octet là **255**, đạt được khi toàn bộ 8 bit nhị phân của octet đó đều được bật lên bằng 1 (`11111111`).

**Câu 2:** Định nghĩa thế nào là `Network ID` và `Broadcast IP` của một mạng con (Subnet)? Kỹ sư mạng có được phép gán 2 địa chỉ này cho PC hoặc cổng Router không?
* *Trả lời:* * `Network ID` là địa chỉ đầu tiên (nhỏ nhất) của Subnet, dùng để định danh cho cả phân đoạn mạng đó.
  * `Broadcast IP` là địa chỉ cuối cùng (lớn nhất) của Subnet, dùng khi muốn gửi gói tin đến tất cả thiết bị trong mạng.
  * **Quy tắc:** Kỹ sư mạng **TUYỆT ĐỐI KHÔNG** được phép gán Network ID và Broadcast IP cho bất kỳ thiết bị end-device nào trên hệ thống hạ tầng.

---

## 💻 Bài Tập Vận Dụng & Phân Tích (IP Analysis Challenge)

Dựa trên ví dụ so sánh cấu trúc phần Network cố định và phần Host thay đổi linh hoạt trong bài học, hãy phân tích bài toán sau:

### Đề bài:
Cho một Subnet có địa chỉ dạng: `192.168.1.0/24`. 
1. Xác định số lượng bit thuộc phần Host.
2. Viết địa chỉ Network ID và địa chỉ Broadcast IP của Subnet này.
3. Tìm dải địa chỉ IP Host hợp lệ có thể gán được cho máy tính doanh nghiệp.

### 📝 Đáp án và tiến trình phân tích chi tiết:
* Tiến trình giải bài toán:
    1. Số bit thuộc phần Host = 32 bit (Tổng số bit IP) - 24 bit (Prefix Network) = 8 bit.
    2. Địa chỉ Network ID (IP đầu tiên khi 8 bit Host bằng 0): 192.168.1.0
    3. Địa chỉ Broadcast IP (IP cuối cùng khi 8 bit Host bằng 1): 192.168.1.255
    4. Dải địa chỉ IP Host hợp lệ gán cho thiết bị là các IP nằm ở giữa: Chạy từ 192.168.1.1 đến 192.168.1.254
