**Mục tiêu:** Xử lý logic phí vận chuyển dựa trên Khoảng cách, Cân nặng và Hạng thành viên. Áp dụng tư duy Fail-fast (loại bỏ trường hợp lỗi sớm).

```text
START
    INPUT khoangCach, canNang, hangThanhVien
    
    Bước 1: Kiểm tra giới hạn vận chuyển (Fail-fast)
    IF khoangCach > 20 THEN
        OUTPUT "LỖI: Không nhận giao hàng trên 20km"
        EXIT
    ENDIF

    Bước 2: Tính phí cơ bản theo khoảng cách
    IF khoangCach < 5 THEN
        phiCoBan = 15000
    ELSE
        phiCoBan = 30000
    ENDIF

    Bước 3: Tính phụ thu theo cân nặng
    IF canNang < 2 THEN
        phuThu = 0
    ELSE IF canNang <= 10 THEN
        phuThu = 10000
    ELSE
        phuThu = 50000
    ENDIF

    Bước 4: Tính tổng phí tạm tính
    tongPhi = phiCoBan + phuThu

    Bước 5: Xét ưu đãi Hạng thành viên
    IF hangThanhVien == "VIP" THEN
        Kiểm tra đặc quyền miễn phí 100%
        IF khoangCach < 5 AND canNang < 2 THEN
            tongPhi = 0
        ELSE
            tongPhi = tongPhi * 0.8  // Giảm 20% tổng phí
        ENDIF
    ENDIF

    OUTPUT tongPhi
END