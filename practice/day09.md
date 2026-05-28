# ✏️ Day 09: Review & Practice (Subnet Splitting Exercises)

## ❓ Câu Hỏi Ôn Tập (Self-Quiz)

**Câu 1:** Tại sao việc gom chung tất cả các phòng ban trong một doanh nghiệp vào duy nhất một Subnet `/24` lại bị coi là một thiết kế mạng tồi về mặt quản trị và bảo mật?
* *Trả lời:* Vì khi chung một Subnet, các thiết bị sẽ liên lạc trực tiếp với nhau ở Layer 2 mà không đi qua Router/Firewall. Điều này khiến người quản trị không thể thiết lập các chính sách (Policy) lọc lưu lượng, chặn Web hay phân quyền truy cập riêng biệt cho từng phòng ban (như cô lập phòng IT với phòng Sale).

**Câu 2:** Khi ta mượn thêm 2 bit từ phần Host để chia Subnet, ta sẽ tạo ra được bao nhiêu mạng con mới? Chỉ số Prefix sẽ thay đổi như thế nào nếu mạng gốc là `/24`?
* *Trả lời:* Mượn 2 bit sẽ tạo ra được $2^2 = 4$ Subnet mạng con mới. Chỉ số Prefix của mạng mới sẽ tăng thêm 2 đơn vị, chuyển từ `/24` thành `/26`.

---

## 💻 Bài Tập Vận Dụng Chia Nhỏ Mạng (Subnet Design Challenge)

### Đề bài yêu cầu:
Cho một không gian địa chỉ mạng ban đầu là `192.168.1.0/24`. Hãy tính toán chia mạng con để cấp phát tối ưu nhất cho 4 phòng ban có số lượng thiết bị Host như sau:
* **Phòng A:** 50 hosts
* **Phòng B:** 8 hosts
* **Phòng C:** 20 hosts
* **Phòng D:** 15 hosts

### 📝 Tiến trình phân tích và chia dải chi tiết:
Để tiết kiệm IP, ta tiến hành chia từ phòng có nhu cầu Host lớn nhất đến nhỏ nhất (Phương pháp VLSM):

1. **Chia cho Phòng A (50 hosts):**
   * Cần $2^H - 2 \ge 50 \rightarrow H = 6$ bit Host ($2^6 - 2 = 62$).
   * Prefix tương ứng: $32 - 6 = /26$.
   * **Cấp dải:** **`192.168.1.0/26`** (Dải IP chạy từ `.0` đến `.63`).

2. **Chia cho Phòng C (20 hosts):**
   * IP bắt đầu từ cụm trống tiếp theo là `.64`. Cần $2^H - 2 \ge 20 \rightarrow H = 5$ bit Host ($2^5 - 2 = 30$).
   * Prefix tương ứng: $32 - 5 = /27$.
   * **Cấp dải:** **`192.168.1.64/27`** (Dải IP chạy từ `.64` đến `.95`).

3. **Chia cho Phòng D (15 hosts):**
   * IP bắt đầu từ cụm trống tiếp theo là `.96`. Cần $2^H - 2 \ge 15 \rightarrow H = 5$ bit Host ($2^5 - 2 = 30$).
   * Prefix tương ứng: $32 - 5 = /27$.
   * **Cấp dải:** **`192.168.1.96/27`** (Dải IP chạy từ `.96` đến `.127`).

4. **Chia cho Phòng B (8 hosts):**
   * IP bắt đầu từ cụm trống tiếp theo là `.128`. Cần $2^H - 2 \ge 8 \rightarrow H = 4$ bit Host ($2^4 - 2 = 14$).
   * Prefix tương ứng: $32 - 4 = /28$.
   * **Cấp dải:** **`192.168.1.128/28`** (Dải IP chạy từ `.128` đến `.143`).
