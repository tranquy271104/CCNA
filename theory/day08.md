# 📔 Day 08: Kỹ Thuật Tính Toán Phân Hoạch Mạng Con (Subnetting)

## 🧮 1. Công Thức Cốt Lõi Tính Toán Địa Chỉ
Khi biết chỉ số Prefix của một Subnet, ta luôn tính được các thông số cốt lõi sau:
* **Số bit phần Network ($N$):** Bằng chính chỉ số Prefix.
* **Số bit phần Host ($H$):** $H = 32 - \text{Prefix}$
* **Tổng số địa chỉ IP trong Subnet:** $= 2^H$
* **Số lượng địa chỉ IP Host hợp lệ (gán được cho thiết bị):** $= 2^H - 2$
> ⚠️ *Lý do trừ 2:* Vì phải loại trừ đi 2 địa chỉ đặc biệt không thể gán cho thiết bị đầu cuối là **Network ID** (đầu tiên) và **Broadcast IP** (cuối cùng).

---

## 🔍 2. Phân Tích Ví Dụ Thực Tế Trên Lớp

### 📌 Ví dụ 1: Phân tích Subnet `192.168.2.0/23`
1. **Xác định số bit:** Prefix = 23 $\rightarrow$ Số bit Host $H = 32 - 23 = 9$ bit.
2. **Tổng số địa chỉ IP:** $2^9 = 512$ địa chỉ.
3. **Phân tích nhị phân tại Octet thứ 3 (Octet chứa ranh giới rẽ nhánh):**
   * Prefix `/23` nằm ở Octet thứ 3 (bit thứ 7 của octet này).
   * Network ID (8 bit Host bằng 0): `192.168.00000010.00000000` $\rightarrow$ **`192.168.2.0`**
   * Broadcast IP (8 bit Host bằng 1): `192.168.00000011.11111111` $\rightarrow$ **`192.168.3.255`**
4. **Dải IP Host hợp lệ:** Chạy từ **`192.168.2.1`** đến **`192.168.3.254`** (Tổng cộng 510 IP gán được cho máy tính).

### 📌 Ví dụ 2: Phân tích Subnet `192.168.4.0/22`
1. **Xác định số bit:** Prefix = 22 $\rightarrow$ Số bit Host $H = 32 - 22 = 10$ bit.
2. **Số địa chỉ IP Host hợp lệ:** $2^{10} - 2 = 1024 - 2 = 1022$ địa chỉ.
3. **Địa chỉ mạng con:** * **Network ID:** **`192.168.4.0`**
   * **Broadcast IP:** **`192.168.7.255`**
   * **Dải IP Host:** Chạy từ **`192.168.4.1`** đến **`192.168.7.254`**

---

## 🎯 3. Bài Toán Quy Hoạch Cấp Phát Subnet Doanh Nghiệp
* **Bài toán:** Công ty A có 15 người (tương ứng cần gán tối thiểu 15 địa chỉ IP Host). Hãy cấp cho công ty 1 Subnet phù hợp nhất?
* **Phương pháp giải:** * Tìm số bit Host ($H$) sao cho thỏa mãn điều kiện tối ưu: $2^H - 2 \ge 15$
  * Thử với $H = 4$ $\rightarrow$ $2^4 - 2 = 14$ (Thiếu, loại).
  * Thử với $H = 5$ $\rightarrow$ $2^5 - 2 = 30$ (Đủ và tối ưu chi phí).
  * Từ $H = 5$ bit Host $\rightarrow$ Chỉ số Prefix tương ứng $= 32 - 5 = 27$.
* **Kết luận:** Chọn Subnet có mẫu dạng **`/27`** là tối ưu nhất cho phòng ban 15 người.
