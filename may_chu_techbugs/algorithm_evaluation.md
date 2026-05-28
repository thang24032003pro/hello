ĐẦU VÀO: Danh_sách gồm N người dùng (Đã sắp xếp A-Z), Tên_cần_tìm
ĐẦU RA: Vị trí của người dùng hoặc thông báo thất bại

KHỞI TẠO:
    Đầu = 1
    Cuối = N

VÒNG LẶP: KHI (Đầu <= Cuối) THÌ:
    Giữa = Phần_nguyên_xuống((Đầu + Cuối) / 2)
    
    NẾU Danh_sách[Giữa] == Tên_cần_tìm THÌ
        IN RA "Đăng nhập thành công tại vị trí " + Giữa
        DỪNG THUẬT TOÁN
        
    NGƯỢC LẠI NẾU Danh_sách[Giữa] > Tên_cần_tìm THÌ
        Cuối = Giữa - 1 // Thu hẹp phạm vi về nửa trước
        
    NGƯỢC LẠI
        Đầu = Giữa + 1  // Thu hẹp phạm vi về nửa sau
    KẾT THÚC NẾU
KẾT THÚC VÒNG LẶP

IN RA "Đăng nhập thất bại: Tài khoản không tồn tại"

Bảng 1: Dò tay theo Mã giả cũ (Linear Search)Vòng lặpChỉ số iGiá trị Danh_sách[i]So sánh với "Hoa"Kết quả11"An""An" == "Hoa"Sai, tiếp tục22"Bảo""Bảo" == "Hoa"Sai, tiếp tục33"Cường""Cường" == "Hoa"Sai, tiếp tục44"Dung""Dung" == "Hoa"Sai, tiếp tục55"Hoa""Hoa" == "Hoa"Đúng, Dừng (Thành công)

Bảng 2: Dò tay theo Mã giả mới (Binary Search)Vòng lặpBiến ĐầuBiến CuốiBiến GiữaGiá trị Danh_sách[Giữa]Logic So sánh & Hành động cập nhậtKhởi tạo17Chưa cóChưa cóKiểm tra điều kiện vòng lặp $1 \le 7$ (Thỏa mãn)1174"Dung""Dung" < "Hoa" $\rightarrow$ Mục tiêu nằm ở nửa sau.Cập nhật: Đầu = Giữa + 1 = 52576"Lan""Lan" > "Hoa" $\rightarrow$ Mục tiêu nằm ở nửa trước.Cập nhật: Cuối = Giữa - 1 = 53555"Hoa""Hoa" == "Hoa" $\rightarrow$ Tìm thấy mục tiêu! Dừng.

PHẦN BỔ SUNG: KHUNG BẢO VỆ GIẢI THUẬT TRƯỚC TECH LEADDưới đây là các câu trả lời ngắn gọn, đanh thép giúp bạn vượt qua vòng chất vấn của Tech Lead:Câu hỏi 1 (Worst-case của 1 triệu phần tử): Với thuật toán mới, trong kịch bản tệ nhất, hệ thống chỉ mất tối đa khoảng 20 phép thử. Phép toán chứng minh là $\log_2(1.000.000) \approx 19.93$. Thay vì duyệt tuyến tính, đồ thị hiệu năng đã chuyển từ đường thẳng vọt lên đỉnh thành một đường cong thoải cực kỳ ổn định $O(\log n)$.Câu hỏi 2 (Điều kiện tiên quyết): Dữ liệu bắt buộc phải được sắp xếp trước. Nếu dữ liệu lộn xộn, logic chia đôi sẽ tự động loại bỏ sai các phân vùng chứa kết quả, dẫn đến hiện tượng Sót dữ liệu (Báo tài khoản không tồn tại trong khi tài khoản đó thực sự có trong hệ thống).Câu hỏi 3 (Dấu bằng trong điều kiện Đầu <= Cuối): Dấu = là bắt buộc. Khi phạm vi tìm kiếm bị thu hẹp lại chỉ còn duy nhất 1 phần tử cuối cùng (lúc này Đầu == Cuối == Giữa), nếu không có dấu =, vòng lặp sẽ thoát ra sớm và bỏ sót phần tử chốt chặn này, dẫn đến thuật toán chạy sai khi mục tiêu nằm ở biên thu hẹp.