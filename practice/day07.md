# 📔 Day 07: Cấu Trúc Địa Chỉ IPv4 & Các Thuật Ngữ Subnet Core

## 📐 1. Quy Luật Số Bit Và Số Trường Hợp (Binary Combinations)
Mối liên hệ giữa số lượng bit nhị phân và số trường hợp (TH) khả thi được tính theo công thức lũy thừa cơ số 2 ($2^x$):
* **2 bit nhị phân:** Có $2^2 = 4$ trường hợp khả thi (`00`, `01`, `10`, `11`) $\rightarrow$ Tương ứng giá trị thập phân từ `0` đến `3`.
* **3 bit nhị phân:** Có $2^3 = 8$ trường hợp khả thi (`000`, `001`, `010`, `011`, `100`, `101`, `110`, `111`) $\rightarrow$ Tương ứng giá trị thập phân từ `0` đến `7`.
* **4 bit nhị phân:** Có $2^4 = 16$ trường hợp khả thi từ `0000` đến `1111` $\rightarrow$ Tương ứng giá trị thập phân từ `0` đến `15`.
> 📌 **Tổng quát:** Nếu có **$x$ bit nhị phân**, chúng ta sẽ tạo ra được tất cả **$2^x$ trường hợp** giá trị khác nhau.

---

## 🌐 2. Cấu Trúc Địa Chỉ IPv4 (IPv4 Address Structure)
Địa chỉ IP là một định danh thuộc Layer 3 (Network Layer) dùng để định tuyến gói tin trên hệ thống, hiện tại gồm 2 phiên bản là IPv4 và IPv6.

### A. Cấu trúc thiết kế của IPv4
* Được cấu tạo hoàn toàn bởi **32 bit Nhị phân**.
* Chia làm 4 phần bằng nhau $\rightarrow$ Mỗi phần sở hữu 8 bit Nhị phân, được gọi là một **Octet**.
* Các cụm Octet này được ngăn cách với nhau bởi dấu chấm (`.`).
* **Hiển thị:** Để con người dễ đọc, IPv4 được trình diễn ở dạng thập phân. Giá trị thập phân của 1 octet luôn chạy trong khoảng từ **0 đến 255**.
* **Tổng số địa chỉ:** IPv4 có tổng cộng $2^{32} = 4.294.967.296$ địa chỉ trên toàn thế giới.

---

## 🏗️ 3. Các Thuật Ngữ Cốt Lõi Về Subnet (Subnet Terminology)

### A. Subnet (Mạng con)
Là một nhóm các địa chỉ IP có **chung phần Network**.
* *Ví dụ:* `192.168.1.0/24`

### B. Các thành phần cấu tạo nên Subnet
Một Subnet được định danh bằng cấu trúc: `Network ID / Prefix`

* **Prefix:** Là số bit thuộc về phần Network dùng để xác định ranh giới cố định.
  * *Ví dụ:* `/24` nghĩa là có 24 bit thuộc phần Network, còn lại $32 - 24 = 8$ bit thuộc phần Host.
* **Phần Network (Network Portion):** Là phần địa chỉ cố định, giống nhau hoàn toàn giữa các địa chỉ IP nằm trong cùng một Subnet.
  * *Ví dụ thực tế:* Giống như dòng họ, họ **Trần** (/1) thì tất cả mọi người trong nhóm đều phải mang họ Trần cố định (1 chữ cố định). Nếu là họ + đệm **Trần Văn** (/2) thì có 2 chữ cố định giống nhau.
* **Phần Host (Host Portion):** Là phần địa chỉ thay đổi tùy ý nhằm mục đích định danh riêng cho từng thiết bị cụ thể trong Subnet đó.
* **Network ID (Địa chỉ mạng):** Là địa chỉ **đầu tiên** (địa chỉ bé nhất) của một Subnet. Phần Host của địa chỉ này có toàn bộ các bit bằng `0`.
* **Broadcast IP (Địa chỉ quảng bá):** Là địa chỉ **cuối cùng** (địa chỉ lớn nhất) của một Subnet. Phần Host của địa chỉ này có toàn bộ các bit bằng `1`.
* **IP Host:** Các địa chỉ IP nằm ở giữa Network ID và Broadcast IP, được dùng để gán trực tiếp cho thiết bị (PC, Router, Switch...).

---

## 🔍 4. Ví Dụ Phân Tích Cụ Thể Subnet `192.168.1.0/24`
Phân tích chi tiết ranh giới địa chỉ dựa trên Prefix `/24`:
* `Prefix = 24` $\rightarrow$ Có 24 bit Network (cố định cụm `192.168.1.`), và có $32 - 24 = 8$ bit Host (thay đổi linh hoạt).
* Số lượng địa chỉ IP nằm trong Subnet này là: $2^8 = 256$ địa chỉ (chạy liên tục từ `.0` đến `.255`).

* Chi tiết dải địa chỉ:
  * `192.168.1.00000000` $\rightarrow$ `192.168.1.0` $\rightarrow$ **Network ID** (IP bé nhất)
  * `192.168.1.00000001` $\rightarrow$ `192.168.1.1` $\rightarrow$ IP Host đầu tiên gán cho thiết bị
  * `192.168.1.00000010` $\rightarrow$ `192.168.1.2` $\rightarrow$ IP Host tiếp theo
  * ...
  * `192.168.1.11111111` $\rightarrow$ `192.168.1.255` $\rightarrow$ **Broadcast IP** (IP lớn nhất)
