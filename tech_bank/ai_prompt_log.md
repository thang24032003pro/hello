Prompt 1: Tôi đang lập cấu trúc điều kiện cho tính năng giới hạn 3 lần nhập sai mã PIN trong ATM. Làm thế nào để thiết lập một biến đếm và khối rẽ nhánh hình thoi để khi chạm đến lần thứ 3 thì nuốt thẻ, còn dưới 3 lần thì quay lại màn hình nhập PIN mà không bị rơi vào vòng lặp vô hạn?

Prompt 2: Trong luồng rút tiền ATM, khi khách hàng nhập số tiền không phải bội số của 50.000 VNĐ, hệ thống phải hiển thị cảnh báo và cho họ nhập lại. Hãy tư duy logic giúp tôi vị trí đặt mũi tên quay lại (Loop-back arrow) sao cho người dùng có thể thoát ra được bằng nút Hủy chứ không bị kẹt vĩnh viễn ở đó.

Prompt 3: Đưa ra 3 kịch bản kiểm thử tĩnh cực đoan (Edge cases) liên quan đến sự xung đột giữa số dư khả dụng của khách hàng và lượng tiền mặt vật lý thực tế còn lại trong các hộp tiền của máy ATM.

Prompt 4: Phân tích rủi ro về mặt bảo mật và trải nghiệm người dùng nếu tôi đặt khối kiểm tra "Số dư tài khoản của khách hàng" lên TRƯỚC hoặc ra SAU khối kiểm tra "Lượng tiền mặt còn lại trong cột tiền ATM".