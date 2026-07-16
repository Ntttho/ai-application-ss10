# Bài 2: Tối Ưu Hóa Prompt Đặc Tả Yêu Cầu Chức Năng

## Prompt tối ưu

``` text
Vai trò:
Act as a Senior Business Analyst và System Analyst.

Mục tiêu:
Viết tài liệu Functional Requirements cho module Authentication của dự án Shop AI.

Ngữ cảnh:
Dự án sử dụng Spring Boot, JWT để xác thực và RBAC để phân quyền. Phân tích toàn bộ luồng đăng nhập và mô tả đầy đủ yêu cầu chức năng.

Ràng buộc:
- Mô tả điều kiện đầu vào, đầu ra và luồng xử lý.
- Bao gồm tiền điều kiện, hậu điều kiện, luồng chính và ngoại lệ.
- Bắt buộc mô tả chi tiết:
  1. Người dùng nhập sai mật khẩu quá 5 lần.
  2. JWT hết hạn trong khi phiên làm việc đang diễn ra.
  3. Tài khoản ở trạng thái Inactive nhưng vẫn cố đăng nhập.
- Nêu phản hồi hệ thống và mã lỗi nếu có.
- Viết theo góc nhìn tài liệu SRS, không mô tả code.

Định dạng:
Trình bày bằng Markdown với các mục:
1. Overview
2. Actors
3. Preconditions
4. Functional Requirements
5. Main Flow
6. Exception Flows
7. Postconditions
```

## Functional Requirements

``` text
# Functional Requirements - Authentication

## Overview
Module Authentication xác thực người dùng bằng JWT và kiểm soát quyền truy cập theo RBAC.

## Actors
- Người dùng
- Hệ thống Authentication

## Preconditions
- Người dùng có tài khoản.
- Hệ thống hoạt động bình thường.

## Functional Requirements

FR-01: Cho phép nhập tên đăng nhập và mật khẩu.

FR-02: Kiểm tra thông tin đăng nhập.
- Nếu hợp lệ, tạo JWT và trả về cho người dùng.
- Áp dụng quyền theo RBAC.

FR-03: Đăng nhập thành công.
- Trả về Access Token.
- Cho phép truy cập theo quyền.

FR-04: Sai mật khẩu quá 5 lần.
- Ghi nhận số lần thất bại.
- Khóa đăng nhập tạm thời hoặc khóa tài khoản theo chính sách.
- Trả về thông báo phù hợp.

FR-05: JWT hết hạn.
- Từ chối yêu cầu sử dụng token hết hạn.
- Yêu cầu người dùng đăng nhập hoặc làm mới token nếu hệ thống hỗ trợ.

FR-06: Tài khoản Inactive.
- Từ chối đăng nhập.
- Không cấp JWT.
- Thông báo tài khoản đã bị khóa hoặc chưa được kích hoạt.

## Main Flow
1. Người dùng nhập thông tin.
2. Hệ thống xác thực.
3. Kiểm tra trạng thái tài khoản.
4. Sinh JWT.
5. Gán quyền RBAC.
6. Trả kết quả thành công.

## Exception Flows
- Sai mật khẩu quá 5 lần.
- JWT hết hạn.
- Tài khoản Inactive.
- Sai tên đăng nhập hoặc mật khẩu.
- Lỗi hệ thống.

## Postconditions
- Thành công: JWT được cấp.
- Thất bại: Không tạo JWT và ghi nhận sự kiện bảo mật.
```
