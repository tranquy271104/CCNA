# 📔 Day 09: Phương Pháp Mượn Bit Chia Subnet & Áp Dụng Chính Sách (Policy)

## 🛡️ 1. Tại Sao Phải Chia Subnet? — Bài Toán Thực Tế Doanh Nghiệp
Nếu một công ty có 200 nhân viên và tất cả gom chung vào 1 Subnet duy nhất sử dụng Prefix `/24` (Ví dụ: `192.168.1.0/24`), chúng ta sẽ **KHÔNG THỂ** áp đặt các chính sách bảo mật riêng biệt cho từng phòng ban.

### A. Tình huống yêu cầu từ doanh nghiệp:
* **HR (Nhân sự):** Được phép truy cập mạng xã hội (Youtube, Facebook, Zalo...).
* **Sale (Kinh doanh):** Được truy cập Facebook, Zalo nhưng **CẤM** truy cập Youtube.
* **IT (Kỹ thuật):** **CẤM TUYỆT ĐỐI** truy cập Facebook, Zalo, Youtube để tập trung làm việc.

### B. Giải pháp kỹ thuật bằng cách chia nhỏ Subnet:
Để triển khai hệ thống, kỹ sư mạng sẽ tạo ra các **Policy (Chính sách)** mạng:
* `Policy A`: Cho phép truy cập đầy đủ (Youtube, Facebook, Zalo).
* `Policy B`: Chặn toàn bộ các trang giải trí trên.

Sau đó, ta băm nhỏ mạng `/24` ban đầu thành các Subnet độc lập tương ứng với từng phòng ban để áp Policy chính xác dựa trên dải IP:
* Phòng **IT**: Cấp dải `192.168.1.0/24` $\rightarrow$ Áp dụng mạng này vào `Policy B`.
* Phòng **HR**: Cấp dải `192.168.2.0/24` $\rightarrow$ Áp dụng mạng này vào `Policy A`.

---

## 📐 2. Bản Chất Của Phương Pháp Mượn Bit Chia Subnet
* **Khái niệm:** Chia Subnet là hành động lấy một Subnet to (cung cấp nhiều địa chỉ IP nhưng lãng phí) băm nhỏ thành các Subnet con (vừa vặn với nhu cầu sử dụng thực tế).
* **Cơ chế kỹ thuật:** Ta tiến hành **mượn bit thuộc phần Host** chuyển sang cho phần Network quản lý (Làm tăng chỉ số Prefix lên, ví dụ từ `/24` lên `/25` hoặc `/26`).

### 🔍 Ví dụ chi tiết: Băm mạng `192.168.1.0/24` thành 2 mạng `/25`
* Mạng gốc `/24` có 24 bit Network, dải IP chạy liên tục từ `.0` đến `.255`.
* Khi nâng lên `/25`, ta đã mượn thêm **1 bit** đầu tiên của Octet thứ 4 làm bit Network.
* 1 bit mượn này tạo ra được $2^1 = 2$ Subnet con mới:

1. **Subnet con thứ nhất (Bit mượn bằng 0):**
   * Địa chỉ dạng nhị phân: `192.168.1.00000000/25` $\rightarrow$ **`192.168.1.0/25`**
   * Dải IP chạy từ: `.0` đến `.127` (Với `.0` là Network ID, `.127` là Broadcast IP).
2. **Subnet con thứ hai (Bit mượn bằng 1):**
   * Địa chỉ dạng nhị phân: `192.168.1.10000000/25` $\rightarrow$ **`192.168.1.128/25`**
   * Dải IP chạy từ: `.128` đến `.255` (Với `.128` là Network ID, `.255` là Broadcast IP).

---

## 📈 3. Quy Luật Dịch Chuyển Ranh Giới Mượn Bit
Tùy thuộc vào số lượng IP cần dùng, ranh giới mượn bit sẽ dịch chuyển tăng dần:
* `192.168.10.0/24` dịch chuyển mượn 2 bit $\rightarrow$ Thu được dải dạng **`/26`**
* `192.168.10.64/26` dịch chuyển mượn 2 bit $\rightarrow$ Thu được dải dạng **`/28`**
* `192.168.8.0/22` dịch chuyển mượn 3 bit $\rightarrow$ Thu được dải dạng **`/25`**
