THUẬT TOÁN: Tinh_Phi_FastShip
BẮT ĐẦU
    NHẬP d (Khoảng cách), w (Cân nặng), la_VIP (Đúng/Sai)

    // Bước 1: Kiểm tra điều kiện chặn (Fail-fast)
    NẾU d > 20 THÌ
        XUẤT "Không nhận giao"
        KẾT THÚC
    KẾT THÚC NẾU

    // Bước 2: Xác định phí cơ bản (Phi_CB)
    NẾU d < 5 THÌ
        Phi_CB = 15000
    NGƯỢC LẠI
        Phi_CB = 30000
    KẾT THÚC NẾU

    // Bước 3: Xác định phụ thu cân nặng (Phu_thu)
    NẾU w < 2 THÌ
        Phu_thu = 0
    NGƯỢC LẠI THÌ
        NẾU w <= 10 THÌ
            Phu_thu = 10000
        NGƯỢC LẠI
            Phu_thu = 50000
        KẾT THÚC NẾU
    KẾT THÚC NẾU

    // Bước 4: Tính tổng tạm tính
    Tong_tam = Phi_CB + Phu_thu

    // Bước 5: Xét đặc quyền VIP
    NẾU la_VIP == Đúng THÌ
        NẾU d < 5 VÀ w < 2 THÌ
            Tong_cuoi = 0  
        NGƯỢC LẠI
            Tong_cuoi = Tong_tam * 0.8  
        KẾT THÚC NẾU
    NGƯỢC LẠI
        Tong_cuoi = Tong_tam
    KẾT THÚC NẾU

    XUẤT Tong_cuoi
KẾT THÚC