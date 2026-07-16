# Bài 3: Đọc Hiểu Code & Cập Nhật Đặc Tả Hệ Thống

## Prompt thiết kế

``` text
Vai trò:
Act as a Senior System Analyst.

Mục tiêu:
Phân tích đoạn mã CartService đã được Antigravity index, phát hiện lỗ hổng logic và xây dựng danh sách Business Rules theo chuẩn SRS.

Ngữ cảnh:
Module Cart của dự án Guai-api chịu trách nhiệm thêm sản phẩm vào giỏ hàng. Hãy phân tích luồng xử lý hiện tại và đối chiếu với các quy tắc nghiệp vụ thông thường của hệ thống thương mại điện tử.

Ràng buộc:
- Xác định các lỗ hổng logic trong phương thức addToCart().
- Đặc biệt kiểm tra trường hợp quantity <= 0.
- Kiểm tra trường hợp quantity vượt quá số lượng tồn kho (Inventory).
- Nếu phát hiện thiếu quy tắc nghiệp vụ, hãy đề xuất quy tắc cần bổ sung.
- Không chỉnh sửa mã nguồn, chỉ phân tích và sinh tài liệu.
- Viết theo chuẩn SRS.

Định dạng:
1. Logic Issues
2. Business Rules
3. Impact nếu không vá lỗi
4. Recommendation
```

## Business Rules

``` text
BR-01: Chỉ cho phép thêm sản phẩm tồn tại trong hệ thống.

BR-02: Quantity phải lớn hơn 0. Nếu quantity nhỏ hơn hoặc bằng 0, hệ thống từ chối yêu cầu và trả về thông báo lỗi.

BR-03: Tổng số lượng sản phẩm trong giỏ hàng sau khi cập nhật không được vượt quá số lượng tồn kho hiện có.

BR-04: Nếu số lượng tồn kho không đủ, hệ thống không cập nhật giỏ hàng và trả về thông báo phù hợp.

BR-05: Khi sản phẩm đã tồn tại trong giỏ hàng, hệ thống cộng thêm số lượng nhưng vẫn phải kiểm tra giới hạn tồn kho trước khi lưu.

BR-06: Khi sản phẩm chưa có trong giỏ hàng, hệ thống tạo mới CartItem sau khi hoàn thành tất cả bước kiểm tra dữ liệu.

BR-07: Không cho phép lưu dữ liệu có quantity âm hoặc bằng 0 nhằm đảm bảo tính toàn vẹn dữ liệu.

BR-08: Mọi yêu cầu thêm sản phẩm không hợp lệ phải được ghi nhận để phục vụ theo dõi và xử lý sự cố.

BR-09: Chỉ lưu dữ liệu vào CartRepository khi tất cả quy tắc nghiệp vụ đều được thỏa mãn.

BR-10: Hệ thống phải trả về thông báo rõ ràng cho từng trường hợp lỗi như sản phẩm không tồn tại, số lượng không hợp lệ hoặc vượt quá tồn kho.
```
