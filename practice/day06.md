# ✏️ Day 06: Review & Practice (OSI Model & Binary Conversion)

## ❓ Câu Hỏi Ôn Tập (Self-Quiz)

**Câu 1:** Dựa trên cơ chế hoạt động của Layer 4, tại sao khi bạn tải một tệp tin (Setup game, file Word) thì tệp tin đó bắt buộc phải dùng TCP, còn khi bạn xem livestream giải đấu game thì lại dùng UDP?
* *Trả lời:* * Khi tải tệp tin, dữ liệu bắt buộc phải toàn vẹn 100% (chỉ cần sai hoặc mất 1 bit là file lỗi không mở được), do đó bắt buộc phải dùng **TCP** để có cơ chế đánh số thứ tự và truyền lại nếu mất gói.
  * Khi xem livestream, sự chậm trễ (delay) là điều tối kỵ. Dữ liệu cần đẩy đi liên tục ở tốc độ cao nhất (Realtime). Do đó dùng **UDP** để tối ưu tốc độ, dù thỉnh thoảng có mất vài gói tin làm mờ hình một tích tắc cũng không ảnh hưởng đến trải nghiệm tổng thể.

**Câu 2:** Giá trị Thập phân lớn nhất và nhỏ nhất của một cụm Octet (8 bit) trong địa chỉ IP có thể đạt được là bao nhiêu? Tương ứng với chuỗi nhị phân nào?
* *Trả lời:*
  * Nhỏ nhất là **0**, tương ứng với chuỗi 8 bit 0 liên tiếp (`00000000`).
  * Lớn nhất là **255**, tương ứng với chuỗi 8 bit 1 liên tiếp (`11111111`) vì: $128 + 64 + 32 + 16 + 8 + 4 + 2 + 1 = 255$.

---

## 💻 Bài Tập Tự Luyện Tính Toán (Chuyển Đổi Hệ Số)

### Bài tập 1: Đổi từ Nhị phân sang Thập phân
1. Chuỗi bit: `10100000`
2. Chuỗi bit: `00001010`
* *Đáp án chi tiết:* 1. Chuỗi `10100000` $\rightarrow$ $128 + 32 =$ **160**
  2. Chuỗi `00001010` $\rightarrow$ $8 + 2 =$ **10**

### Bài tập 2: Đổi từ Thập phân sang Nhị phân
1. Số thập phân: `200`
2. Số thập phân: `50`
* *Đáp án chi tiết:*
  1. Số `200` $\rightarrow$ $200 = 128 + 64 + 8$ $\rightarrow$ Chuỗi nhị phân thu được là **`11001000`**
  2. Số `50` $\rightarrow$ $50 = 32 + 16 + 2$ $\rightarrow$ Chuỗi nhị phân thu được là **`00110010`**
