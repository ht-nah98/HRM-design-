Thông tin chung chức năng
User Story ID: US-04

Tên tính năng: Upload và lưu trữ tài liệu nhân sự của nhân viên

Module: HRM – Hồ sơ nhân viên → Tài liệu đính kèm

Version: v1.0

Link thiết kế (Figma): TBD

Phụ thuộc:

US-02 – Xem chi tiết hồ sơ nhân sự (điểm vào trang hồ sơ để thao tác tài liệu)

US-08 – Phân quyền theo Job Level (ai được upload/xem/xóa tài liệu)

1. Mục tiêu tính năng (Feature Objective)
1.1. Vấn đề cần giải quyết
HR cần số hóa và lưu trữ các giấy tờ của nhân viên (CCCD, bằng cấp, chứng chỉ…) trong hệ thống để:

Không thất lạc bản giấy

Dễ tra cứu khi cần

Tập trung tại “hồ sơ nhân sự” thay vì lưu rải rác nhiều nơi

1.2. Mục tiêu
Cho phép HR upload, lưu trữ và quản lý các tài liệu gắn với từng hồ sơ nhân viên.

Đảm bảo tài liệu được phân loại rõ ràng và truy cập theo đúng quyền.

2. Phạm vi tính năng (Scope)
In-scope (v1.0)
Upload tài liệu vào hồ sơ nhân viên.

Lưu metadata tài liệu (loại tài liệu, tên file, ngày upload, người upload…).

Xem danh sách tài liệu đã upload theo từng nhân viên.

Tải xuống (download) tài liệu theo quyền.

Xóa tài liệu (nếu được phép) theo quyền.

Kiểm tra định dạng/kích thước file khi upload.

Out-of-scope (v1.0)
OCR trích xuất nội dung giấy tờ

Tự động kiểm tra tính hợp lệ giấy tờ

Chữ ký số / quy trình duyệt tài liệu

Versioning nâng cao (giữ nhiều phiên bản cùng một tài liệu) nếu chưa cần

3. Đối tượng sử dụng (Target Users)
Actor

Mô tả

Nhân viên HR (HR Staff/HR Admin)

Upload và quản lý tài liệu hồ sơ nhân viên

User được phân quyền

Có thể xem/tải theo permission được cấp

4. Workflow tổng quan
4.1 Upload tài liệu
HR mở Chi tiết hồ sơ nhân viên → Tab “Tài liệu”

Nhấn Upload

Chọn loại tài liệu (VD: CCCD/Bằng cấp/Chứng chỉ/Khác)

Chọn file → Upload

Hệ thống validate định dạng/kích thước

Upload thành công → tài liệu xuất hiện trong danh sách

4.2 Xem/Tải tài liệu
User mở tab “Tài liệu”

Xem danh sách tài liệu

Nhấn Download để tải về (nếu có quyền)

4.3 Xóa tài liệu
User có quyền nhấn “Xóa”

Hệ thống xác nhận

Xóa thành công và ghi audit log

5. User Story
As a Nhân viên HR
I want upload và lưu trữ các tài liệu của nhân viên (CCCD, bằng cấp, chứng chỉ) vào hệ thống
So that có hồ sơ số hóa hoàn chỉnh và dễ dàng tra cứu khi cần.

6. Acceptance Criteria (Given/When/Then)
AC-01 – Upload thành công
Given HR có quyền upload tài liệu

When HR chọn loại tài liệu + chọn file hợp lệ và nhấn Upload

Then hệ thống lưu file + metadata và hiển thị trong danh sách tài liệu của nhân viên

AC-02 – Chặn upload khi file không hợp lệ
Given HR đang upload

When file sai định dạng hoặc vượt dung lượng cho phép

Then hệ thống chặn upload và hiển thị lỗi rõ ràng

AC-03 – Xem danh sách tài liệu theo nhân viên
Given user có quyền xem tài liệu

When mở tab “Tài liệu” của nhân viên A

Then hệ thống hiển thị danh sách tài liệu đã upload của A

AC-04 – Download theo quyền
Given user có quyền download tài liệu

When nhấn Download một tài liệu

Then hệ thống cho tải file về

AC-05 – Xóa theo quyền + audit
Given user có quyền xóa tài liệu

When nhấn Xóa và xác nhận

Then tài liệu bị xóa và hệ thống ghi audit log

AC-06 – Không có quyền
Given user không có quyền upload/xem/download/xóa

When thực hiện hành động tương ứng

Then UI chặn và API trả 403

7. Functional Requirements
7.1 FR list
ID

Yêu cầu

Mô tả ngắn

Priority

FR-01

Document Tab

Tab tài liệu trong chi tiết hồ sơ

High

FR-02

Upload Document

Upload file + metadata

High

FR-03

Document Classification

Chọn loại tài liệu (CCCD/Bằng cấp/Chứng chỉ/Khác)

High

FR-04

List Documents

Danh sách tài liệu theo nhân viên

High

FR-05

Download Document

Tải tài liệu theo quyền

High

FR-06

Delete Document

Xóa tài liệu theo quyền

Medium

FR-07

File Validation

Validate định dạng/dung lượng

High

FR-08

Audit Log

Log upload/delete/download (tuỳ chính sách)

Medium

7.2 Chi tiết FR
FR-02: Upload Document
Input tối thiểu:

Employee ID / Mã nhân viên (gắn vào hồ sơ)

Document Type (CCCD/Bằng cấp/Chứng chỉ/Khác)

File (binary)

(Optional) Ghi chú

Kết quả:

Lưu file vào storage

Lưu metadata vào DB

Trả về document record (id, name, type, size, uploader, uploaded_at)

FR-07: File Validation
Định dạng cho phép (đề xuất v1.0): PDF, JPG, PNG

Dung lượng tối đa (đề xuất v1.0): TBD MB

Hệ thống chặn các file không hợp lệ và thông báo lỗi.

8. Non-functional Requirements (NFR)
Security: file chỉ truy cập được khi có quyền.

Storage: file được lưu trữ ổn định, có khả năng mở rộng.

Auditability: ghi nhận thao tác tài liệu (ít nhất upload/delete).

Performance: load danh sách tài liệu nhanh, download ổn định.

9. Business Rules
BR-01: Tài liệu phải gắn với đúng hồ sơ nhân viên (Employee ID/Mã NV).

BR-02: Phân quyền theo permission (US-08), không tin UI.

BR-03: Document Type bắt buộc khi upload.

BR-04: Không upload file vượt giới hạn dung lượng hoặc sai định dạng.

BR-05 (cần chốt): Chính sách xóa:

Xóa mềm (soft delete) hay xóa cứng (hard delete)?

10. Validation & Error Handling
Trường hợp

Hành vi hệ thống

Trường hợp

Hành vi hệ thống

Không có quyền

403 Forbidden

Hồ sơ nhân viên không tồn tại

404 Not Found

File sai định dạng

Chặn upload + thông báo

File quá dung lượng

Chặn upload + thông báo

Lỗi lưu storage

Báo lỗi + không tạo metadata (rollback)

Lỗi hệ thống

500 + log

11. Define Of Done
DoD
Upload được tài liệu vào hồ sơ nhân viên.

Có danh sách tài liệu theo từng nhân viên.

Download được theo quyền.

Xóa được theo quyền (theo policy).

Validate file hoạt động đúng.

Có audit log tối thiểu cho upload/delete.