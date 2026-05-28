# 📔 Day 10: Kỹ Thuật Chia Mạng Con Chi Tiết — VLSM (Variable Length Subnet Mask)

## 🎯 1. Bản Chất Và Quy Trình Tri Khai VLSM
* **Khái niệm:** VLSM là kỹ thuật cho phép chia một không gian địa chỉ mạng lớn thành các mạng con có kích thước mặt nạ (Prefix) khác nhau, nhằm tối ưu hóa không gian địa chỉ, tránh lãng phí IP.
* **Quy trình triển khai tiêu chuẩn (3 Bước):**
  * **Bước 1:** Sắp xếp danh sách các phòng ban dựa theo số lượng Host yêu cầu theo thứ tự **giảm dần** (từ lớn nhất đến nhỏ nhất).
  * **Bước 2:** Xác định giá trị Prefix phù hợp nhất cho từng phòng ban bằng công thức $2^H - 2 \ge \text{Host}$.
  * **Bước 3:** Tiến hành phân tách, mượn bit và chia Subnet lần lượt từ trên xuống dưới theo danh sách đã sắp xếp.

---

## 📝 2. Phân Tích Tiến Trình Giải Bài Toán Mẫu Trên Lớp

### 📌 Bài toán 1: Cho mạng gốc `192.168.1.0/24`. Chia cho 4 phòng ban: A (50 hosts), C (20 hosts), D (15 hosts), B (8 hosts).

#### Bước 1 & 2: Sắp xếp và xác định Prefix
* Phòng A: 50 hosts $\rightarrow$ Cần Prefix `/26` (Cung cấp tối đa 62 IP Host)
* Phòng C: 20 hosts $\rightarrow$ Cần Prefix `/27` (Cung cấp tối đa 30 IP Host)
* Phòng D: 15 hosts $\rightarrow$ Cần Prefix `/27` (Cung cấp tối đa 30 IP Host)
* Phòng B: 8 hosts  $\rightarrow$ Cần Prefix `/28` (Cung cấp tối đa 14 IP Host)

#### Bước 3: Tiến trình chia chi tiết bằng cách mượn bit nhị phân
* **Phần 1: Băm mạng `/24` gốc bằng cách mượn 2 bit $\rightarrow$ Tạo ra 4 mạng `/26`:**
  * `192.168.1.00 000000/26` $\rightarrow$ **`192.168.1.0/26`** $\rightarrow$ **Cấp cho Phòng A**
  * `192.168.1.01 000000/26` $\rightarrow$ `192.168.1.64/26` $\rightarrow$ Dùng để chia tiếp cho phòng C, D
  * `192.168.1.10 000000/26` $\rightarrow$ `192.168.1.128/26` $\rightarrow$ Dùng để chia tiếp cho phòng B
  * `192.168.1.11 000000/26` $\rightarrow$ `192.168.1.192/26` $\rightarrow$ **[Dải IP Dư thừa]**

* **Phần 2: Lấy dải `192.168.1.64/26` mượn thêm 1 bit $\rightarrow$ Tạo ra 2 mạng `/27`:**
  * `192.168.1.010 00000/27` $\rightarrow$ **`192.168.1.64/27`** $\rightarrow$ **Cấp cho Phòng C**
  * `192.168.1.011 00000/27` $\rightarrow$ **`192.168.1.96/27`** $\rightarrow$ **Cấp cho Phòng D**

* **Phần 3: Lấy dải `192.168.1.128/26` hạ xuống để chia cho mạng `/28` (Bước nhảy 16):**
  * Các dải khả thi tạo ra: `.128/28`, `.144/28`, `.160/28`, `.176/28`.
  * **`192.168.1.128/28`** $\rightarrow$ **Cấp cho Phòng B**

---

### 📌 Bài toán 2: Cho mạng gốc `172.16.6.0/23`. Chia cho 4 phòng ban: A (130 hosts), C (31 hosts), B (20 hosts), D (5 hosts).

#### Tiến trình phân tích ranh giới và chia dải:
* Mạng gốc nhị phân tại Octet 3: `172.16.0000011 0.0/23`
* **Phần 1: Nâng lên Prefix `/24` (mượn 1 bit) $\rightarrow$ Tạo ra 2 mạng `/24`:**
  * `172.16.00000110.00000000/24` $\rightarrow$ **`172.16.6.0/24`** $\rightarrow$ **Cấp cho Phòng A** (Cần 130 host)
  * `172.16.00000111.00000000/24` $\rightarrow$ `172.16.7.0/24` $\rightarrow$ Dùng để chia tiếp cho các phòng còn lại.

* **Phần 2: Lấy dải `172.16.7.0/24` mượn 2 bit $\rightarrow$ Tạo ra 4 mạng `/26` (Bước nhảy 64):**
  * `172.16.7.00 000000/26` $\rightarrow$ **`172.16.7.0/26`** $\rightarrow$ **Cấp cho Phòng C** (Cần 31 host, nhận `/26` tối ưu)
  * `172.16.7.01 000000/26` $\rightarrow$ `172.16.7.64/26` $\rightarrow$ Dùng để chia tiếp cho phòng B.
  * `172.16.7.10 000000/26` $\rightarrow$ `172.16.7.128/26` $\rightarrow$ **[Dải IP Dư thừa]**
  * `172.16.7.11 000000/26` $\rightarrow$ `172.16.7.192/26` $\rightarrow$ **[Dải IP Dư thừa]**

* **Phần 3: Lấy dải `172.16.7.64/26` mượn 1 bit $\rightarrow$ Tạo ra 2 mạng `/27` (Bước nhảy 32):**
  * `172.16.7.010 00000/27` $\rightarrow$ **`172.16.7.64/27`** $\rightarrow$ **Cấp cho Phòng B** (Cần 20 host)
  * `172.16.7.011 00000/27` $\rightarrow$ `172.16.7.96/27` $\rightarrow$ Dùng để chia tiếp cho phòng D.

* **Phần 4: Lấy dải `172.16.7.96/27` hạ phân hoạch xuống Prefix `/29` để cấp cho phòng D:**
  * **`172.16.7.96/29`** $\rightarrow$ **Cấp cho Phòng D** (Cần 5 host)
