# Bài 4: Xây Dựng Yêu Cầu Phi Chức Năng (NFR)

## Prompt

``` text
Vai trò:
Act as a Senior Solution Architect và System Analyst.

Mục tiêu:
Xây dựng phần Non-Functional Requirements (NFR) cho hệ thống Guai-api.

Ngữ cảnh:
Guai-api là hệ thống thương mại điện tử sử dụng Spring Boot, MySQL, JWT và RBAC. Hệ thống cần đáp ứng các đợt truy cập lớn và đảm bảo hiệu năng cũng như bảo mật.

Ràng buộc:
- Viết theo chuẩn SRS.
- Đưa ra các chỉ tiêu kỹ thuật có thể đo lường.
- Bắt buộc phân tích:
  1. Response Time của các API tra cứu sản phẩm.
  2. Chiến lược Indexing cho MySQL.
  3. Độ trễ và bảo mật của luồng cấp phát, xác thực JWT.
- Mỗi yêu cầu phải có tiêu chí đánh giá và mục đích.

Định dạng:
Xuất kết quả dưới dạng bảng Markdown gồm:
ID | Danh mục | Yêu cầu | Chỉ tiêu kỹ thuật | Tiêu chí đánh giá
```

## Bảng NFR

  -------------------------------------------------------------------------------
  ID       Danh mục    Yêu cầu        Chỉ tiêu kỹ thuật     Tiêu chí đánh giá
  -------- ----------- -------------- --------------------- ---------------------
  NFR-01   Response    API tra cứu    Thời gian phản hồi    Đo bằng công cụ kiểm
           Time        sản phẩm phải  trung bình ≤ 300 ms,  thử hiệu năng.
                       phản hồi nhanh tối đa ≤ 500 ms với   
                       trong điều     95% yêu cầu.          
                       kiện tải thông                       
                       thường.                              

  NFR-02   Response    Hệ thống vẫn   Hỗ trợ ít nhất 1000   Thực hiện kiểm thử
           Time        duy trì hiệu   yêu cầu đồng thời mà  tải.
                       năng khi số    không vượt ngưỡng     
                       lượng người    phản hồi quy định.    
                       dùng tăng.                           

  NFR-03   Database    MySQL phải sử  Thiết kế Index phù    Kiểm tra Execution
                       dụng Index cho hợp để giảm thời gian Plan.
                       các cột thường truy vấn và hạn chế   
                       xuyên tìm kiếm Full Table Scan.      
                       như                                  
                       product_id,                          
                       category_id,                         
                       name và price.                       

  NFR-04   Database    Truy vấn dữ    Thời gian truy vấn    Đo bằng công cụ giám
                       liệu phải được phổ biến ≤ 100 ms     sát cơ sở dữ liệu.
                       tối ưu.        trong điều kiện bình  
                                      thường.               

  NFR-05   Security    Quá trình cấp  Thời gian tạo Access  Đo thời gian xử lý
                       phát JWT phải  Token ≤ 100 ms.       phía máy chủ.
                       diễn ra nhanh                        
                       và an toàn.                          

  NFR-06   Security    JWT phải được  Token hết hạn hoặc    Kiểm thử các trường
                       xác thực ở mọi không hợp lệ phải bị  hợp hợp lệ và không
                       yêu cầu cần    từ chối ngay và trả   hợp lệ.
                       bảo vệ.        về mã lỗi phù hợp.    

  NFR-07   Security    Dữ liệu JWT    Sử dụng thuật toán ký Kiểm tra cấu hình bảo
                       phải được bảo  an toàn, thời gian    mật và kiểm thử tích
                       vệ.            hết hạn hợp lý và     hợp.
                                      truyền qua HTTPS.     
  -------------------------------------------------------------------------------
