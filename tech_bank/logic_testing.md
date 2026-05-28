
## 1. Case 1: Happy Path (Mọi luồng đều hoàn hảo)

* **Dữ liệu đầu vào:** PIN đúng lần đầu, `soDuTaiKhoan` = 10.000.000 VNĐ, `tienMatATM` = 50.000.000 VNĐ, Người dùng nhập `soTienRut` = 2.000.000 VNĐ, Chọn không in biên lai.

| Bước | Khối chức năng kiểm tra | Giá trị biến ghi nhận | Điều kiện / Kết quả rẽ nhánh | Hành động tiếp theo của hệ thống |
| :--- | :--- | :--- | :--- | :--- |
| **1** | Khởi tạo | `soLanNhapSai` = 0 | Khởi tạo thành công | Chuyển đến màn hình nhập PIN |
| **2** | `<Kiểm tra PIN>` | PIN khớp | **ĐÚNG (TRUE)** | Chuyển đến màn hình nhập số tiền |
| **3** | `<Người dùng bấm Hủy?>` | Khách không bấm Hủy | **NO** | Chuyển đến khối kiểm tra bội số |
| **4** | `<soTienRut % 50.000 == 0?>`| 2.000.000 % 50.000 == 0 | **YES** | Chuyển đến khối kiểm tra tài chính |
| **5** | `<soTienRut <= soDu - 50.000>`| 2.000.000 <= 9.950.000 | **YES** | Chuyển đến khối kiểm tra tiền ATM |
| **6** | `<soTienRut <= tienMatATM>` | 2.000.000 <= 50.000.000 | **YES** | Tiến hành trừ tiền và nhả tiền |
| **7** | Cập nhật hệ thống | `soDu` = 8.000.000 VNĐ<br>`tienMatATM` = 48.000.000 VNĐ | Thành công | Nhả tiền $\rightarrow$ Hỏi biên lai $\rightarrow$ Nhả thẻ |
| **8** | **[END]** | Không có lỗi phát sinh | Hệ thống an toàn | Kết thúc luồng giao dịch |

---

## 2. Case 2: Loop Test (Nhập sai PIN, Nhập sai số tiền lẻ)

* **Dữ liệu đầu vào:** Nhập sai PIN 2 lần, lần 3 nhập đúng. `soDuTaiKhoan` = 500.000 VNĐ, `tienMatATM` = 20.000.000 VNĐ. Nhập số tiền rút lần đầu lẻ: 135.000 VNĐ. Nhập số tiền rút lần hai hợp lệ: 100.000 VNĐ.

| Bước | Vòng lặp / Khối kiểm tra | Giá trị biến ghi nhận | Kết quả rẽ nhánh | Trạng thái / Hành động hệ thống |
| :--- | :--- | :--- | :--- | :--- |
| **1** | Nhập PIN lần 1 | `soLanNhapSai` = 0 + 1 = 1 | `<Kiểm tra PIN>` $\rightarrow$ **SAI** | `<soLanNhapSai == 3?>` $\rightarrow$ **NO**. Quay lại màn hình PIN. |
| **2** | Nhập PIN lần 2 | `soLanNhapSai` = 1 + 1 = 2 | `<Kiểm tra PIN>` $\rightarrow$ **SAI** | `<soLanNhapSai == 3?>` $\rightarrow$ **NO**. Quay lại màn hình PIN. |
| **3** | Nhập PIN lần 3 | `soLanNhapSai` = 2 | `<Kiểm tra PIN>` $\rightarrow$ **ĐÚNG**| Vượt qua xác thực. Đến màn hình nhập số tiền. |
| **4** | Nhập tiền lần 1 | `soTienRut` = 135.000 | `<soTienRut % 50.000 == 0?>` $\rightarrow$ **NO** | **Báo lỗi số tiền lẻ.** Quay lại màn hình nhập tiền. |
| **5** | Nhập tiền lần 2 | `soTienRut` = 100.000 | `<soTienRut % 50.000 == 0?>` $\rightarrow$ **YES**| Chuyển xuống kiểm tra tài chính. |
| **6** | Kiểm tra tài chính | `soTienRut` = 100.000 | `100.000 <= (500.000 - 50.000)` $\rightarrow$ **YES** | Thỏa mãn số dư tối thiểu. Kiểm tra khay tiền. |
| **7** | Kiểm tra khay tiền | `tienMatATM` = 20.000.000 | `100.000 <= 20.000.000` $\rightarrow$ **YES** | Thực hiện trừ tiền, nhả tiền, trả thẻ. |
| **8** | **[END]** | `soDu` cuối = 400.000 VNĐ | Giao dịch hoàn tất | An toàn, thoát vòng lặp thành công. |

---

## 3. Case 3: Edge Case (Người dùng bấm nút "Hủy" đột ngột)

* **Dữ liệu đầu vào:** PIN đúng lần 1. Đến màn hình nhập số tiền, khách hàng quyết định thay đổi ý định và bấm nút "Hủy" (Cancel) trên bàn phím cứng.

| Bước | Khối chức năng kiểm tra | Giá trị biến ghi nhận | Điều kiện / Kết quả rẽ nhánh | Hành động tiếp theo của hệ thống |
| :--- | :--- | :--- | :--- | :--- |
| **1** | Xác thực | PIN đúng | `<Kiểm tra PIN>` $\rightarrow$ **ĐÚNG** | Chuyển sang màn hình nhập số tiền |
| **2** | Màn hình nhập tiền | Khách bấm nút "Hủy" | `<Người dùng bấm Hủy?>` $\rightarrow$ **YES** | Cắt luồng ngay lập tức, chuyển đến lệnh nhả thẻ |
| **3** | Trả thẻ | Tài khoản giữ nguyên | Không thực hiện lệnh trừ tiền | **[ATM nhả thẻ]** ngay lập tức |
| **4** | **[END]** | An toàn dữ liệu | Không treo hệ thống | Kết thúc luồng giao dịch |