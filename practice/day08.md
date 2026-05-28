# ✏️ Day 08: Review & Practice (Subnetting & Homework Solutions)

## 📝 Giải Bài Tập Nhận Diện Mạng Con (Trên Lớp)

**Bài toán 1:** Trong các địa chỉ IP sau, địa chỉ nào thuộc cùng Subnet với nhau?
* `A: 192.168.1.5/28`
* `B: 192.168.1.10/28`
* `C: 192.168.1.16/28`
* 👉 **Đáp án:** **A** và **B** thuộc cùng một Subnet. 
* **Giải thích:** Prefix `/28` có bước nhảy trong Octet thứ 4 là $2^{(32-28)} = 2^4 = 16$. Dải mạng đầu tiên chạy từ `.0` đến `.15`. Do đó `.5` và `.10` nằm chung dải, còn `.16` đã nhảy sang Subnet tiếp theo.

---

## 💾 Giải Bài Tập Về Nhà (BTVN - Detailed Solutions)

### 📌 Bài 1: Phân tích Subnet `192.168.1.128/28`
* **Số bit phần Host:** $H = 32 - 28 = 4$ bit.
* **Số lượng IP Host gán được:** $2^4 - 2 = 14$ IP.
* **Network ID:** **`192.168.1.128`**
* **Broadcast IP:** **`192.168.1.143`** (Vì bước nhảy là 16: $128 + 16 - 1 = 143$).
* **Dải IP Host hợp lệ:** Chạy từ **`192.168.1.129`** đến **`192.168.1.142`**.

### 📌 Bài 2: Phân tích Subnet `172.16.0.0/12`
* **Số bit phần Host:** $H = 32 - 12 = 20$ bit.
* **Tổng số IP trong mạng:** $2^{20} = 1.048.576$ địa chỉ IP.
* **Network ID:** **`172.16.0.0`**
* **Broadcast IP:** **`172.31.255.255`** (Vì Prefix `/12` nằm ở Octet 2, bước nhảy là $2^{(16-12)} = 2^4 = 16$. Mạng bắt đầu từ 16 sẽ kết thúc ở $16 + 16 - 1 = 31$).
* **Dải IP Host hợp lệ:** Chạy từ **`172.16.0.1`** đến **`172.31.255.254`**.

### 📌 Bài 3: Xác định Prefix phù hợp cho số lượng Host yêu cầu
Sử dụng điều kiện thiết kế hệ thống $2^H - 2 \ge \text{Số Host}$, ta có bảng quy hoạch ranh giới:

| Phòng | Số Host cần cấp | Số bit Host ($H$) tối ưu | Công thức tính toán | Prefix phù hợp (`32 - H`) |
| :---: | :---: | :---: | :--- | :---: |
| **A** | 8 | **4 bit** | $2^4 - 2 = 14 \ge 8$ | **`/28`** |
| **B** | 100 | **7 bit** | $2^7 - 2 = 126 \ge 100$ | **`/25`** |
| **C** | 31 | **6 bit** | $2^6 - 2 = 62 \ge 31$ | **`/26`** |
| **D** | 255 | **9 bit** | $2^9 - 2 = 510 \ge 255$ | **`/23`** |
