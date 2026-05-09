Người thực hiện: System Analyst (Học viên)
Mục tiêu:Sử dụng AI làm đối tác tư duy (Brainstorm) và rà soát lỗi logic.

Prompt 1: Liệt kê các trường hợp (Edge cases)
Câu hỏi: "Dựa vào quy tắc tính phí của FastShip gồm 3 tham số: Khoảng cách (d), Cân nặng (w), Hạng thành viên (VIP/Thường). Hãy giúp tôi liệt kê tất cả các tổ hợp trường hợp (combinations) có thể xảy ra để đảm bảo tôi không bỏ sót nhánh nào khi vẽ Flowchart."
Mục đích:Đảm bảo bao phủ toàn bộ các nhánh điều kiện (dưới 5km, 5-20km, trên 20km; cân nặng 3 mức; hạng TV 2 mức).

Prompt 2: Phản biện logic Fail-fast
Câu hỏi:"Trong giải thuật này, tôi nên đặt khối kiểm tra 'Khoảng cách > 20km' ở đầu lưu đồ hay cuối lưu đồ để tối ưu hóa? Giải thích lý do về mặt hiệu năng hệ thống."
Kết quả: AI tư vấn đặt ở đầu (Fail-fast) để tránh tính toán phụ thu/giảm giá vô ích nếu đơn hàng không thể giao.

Prompt 3: Kiểm tra lỗi logic tiềm ẩn
Câu hỏi:"Đây là mã giả của tôi: [Dán mã giả]. Có trường hợp nào luồng điều kiện này bị rơi vào ngõ cụt hoặc tính toán sai cho khách hàng VIP không?"
Kết quả: Rà soát lại điều kiện miễn phí 0đ cho VIP để không bị ghi đè bởi lệnh giảm 20%.