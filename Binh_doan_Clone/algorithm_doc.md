THUẬT TOÁN: Quét_Bot_Theo_Lô_An_Toàn
BẮT ĐẦU
    NHẬP totalBots
    KHAI BÁO batchSize = 100

    VÒNG LẶP KHI (totalBots > 0)
            Kiểm tra lô cuối nếu còn ít hơn 100
        NẾU totalBots < batchSize THÌ
            so_luong_thuc_xoa = totalBots
        NGƯỢC LẠI
            so_luong_thuc_xoa = batchSize
        KẾT THÚC NẾU

        THỰC HIỆN: Xóa(so_luong_thuc_xoa) tài khoản bot
        CẬP NHẬT: totalBots = totalBots - so_luong_thuc_xoa
        IN MÀN HÌNH: "Đã xóa " + so_luong_thuc_xoa + " bot. Còn lại: " + totalBots
    KẾT THÚC VÒNG LẶP

    IN MÀN HÌNH: "Hoàn tất! Hệ thống đã sạch Bot."
KẾT THÚC