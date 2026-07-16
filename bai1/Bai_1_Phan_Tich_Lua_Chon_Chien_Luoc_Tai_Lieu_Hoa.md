# Bài 1: Phân Tích & Lựa Chọn Chiến Lược Tài Liệu Hóa

## Đáp án

**Chọn: Phương án B**

## Lý do lựa chọn

-   Antigravity có khả năng index toàn bộ workspace của dự án nên AI có
    thể hiểu mối liên hệ giữa Controller, Service, Repository và
    Security Filter.
-   Prompt yêu cầu AI đóng vai System Analyst và sinh trực tiếp tài liệu
    SRS theo đúng cấu trúc nên phù hợp với mục tiêu tài liệu hóa nghiệp
    vụ.
-   AI có thể lần theo toàn bộ luồng xử lý từ endpoint
    `/api/v1/checkout` đến các tầng xử lý bên dưới, giúp giảm việc tổng
    hợp thủ công.
-   Context của toàn bộ dự án được giữ tốt hơn so với việc chỉ đọc từng
    đoạn mã riêng lẻ.
-   Phù hợp với nội dung Session 10 vì tận dụng khả năng phân tích mã
    nguồn ở quy mô lớn và sinh tài liệu từ toàn bộ codebase.

## Lý do loại trừ phương án A

-   Chỉ phân tích từng file riêng lẻ nên AI không nhìn thấy toàn bộ
    luồng nghiệp vụ.
-   Người dùng phải tự ghép kết quả từ nhiều lần hỏi, dễ bỏ sót logic.
-   Dễ xảy ra thất thoát ngữ cảnh khi chuyển qua nhiều file.
-   Tốn nhiều thời gian và phụ thuộc vào khả năng tổng hợp của người
    thực hiện.

## Lý do loại trừ phương án C

-   Phải sao chép thủ công nhiều file nên mất thời gian.
-   Khó đảm bảo đã sao chép đầy đủ tất cả thành phần liên quan.
-   Giới hạn độ dài ngữ cảnh có thể khiến AI không tiếp nhận hết mã
    nguồn.
-   Quan hệ giữa các lớp và luồng gọi hàm có thể bị mất khi chỉ cung cấp
    các đoạn code rời rạc.
-   Nguy cơ context loss cao, dẫn đến tài liệu SRS thiếu hoặc sai nghiệp
    vụ.

## Kết luận

Phương án B là lựa chọn tối ưu nhất vì tận dụng được khả năng index toàn
bộ dự án của Antigravity, giúp AI phân tích đầy đủ luồng xử lý, hạn chế
thất thoát ngữ cảnh và tạo tài liệu SRS chính xác, đầy đủ hơn so với hai
phương án còn lại.
