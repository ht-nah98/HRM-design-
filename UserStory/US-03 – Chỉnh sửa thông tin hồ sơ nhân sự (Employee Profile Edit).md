Thông tin chung chức năng
User Story ID: US-03

Tên tính năng: Chỉnh sửa thông tin hồ sơ nhân sự

Module: HRM – Hồ sơ nhân viên

Version: v1.0

Link thiết kế (Figma): TBD

Phụ thuộc:

US-01 – Tạo mới hồ sơ nhân viên (có hồ sơ để chỉnh sửa)

US-02 – Xem chi tiết hồ sơ (truy cập từ trang chi tiết)

US-07 – Quản lý Chức danh (job title/job level)

US-08 – Phân quyền theo Job Level (xác định ai được edit)

1. Mục tiêu tính năng (Feature Objective)
1.1. Vấn đề cần giải quyết
Hồ sơ nhân sự sau khi tạo có thể phát sinh thay đổi: thông tin cá nhân, liên hệ, công việc, tổ chức, quản lý trực tiếp, chức danh…

Cần cơ chế chỉnh sửa có kiểm soát quyền để đảm bảo dữ liệu HR chính xác và không bị sửa sai.

Thay đổi Job Title kéo theo thay đổi Job Level và có thể ảnh hưởng phân quyền mặc định theo Job Level.

1.2. Mục tiêu
Cho phép người có quyền chỉnh sửa cập nhật thông tin hồ sơ nhân sự nhanh, rõ ràng.

Lưu lịch sử thay đổi (audit) và enforce quyền ở UI + API.

Khi sửa Job Title: hệ thống cập nhật Job Level và xử lý liên quan phân quyền theo quy tắc.

2. Phạm vi tính năng (Scope)
In-scope (v1.0)
Chỉnh sửa thông tin hồ sơ nhân sự theo nhóm field.

Validate dữ liệu trước khi lưu.

Kiểm tra quyền chỉnh sửa (permission).

Audit log: ai sửa, sửa gì, lúc nào.

Trường hợp thay đổi Job Title → tự cập nhật Job Level.

Out-of-scope (v1.0)
Workflow phê duyệt nhiều cấp trước khi áp dụng thay đổi.

Field-level permission (ẩn/sửa theo từng field nhạy cảm) nếu chưa có rule.

Version compare (diff UI) nâng cao (nếu cần tách story).

3. Đối tượng sử dụng (Target Users)
Actor

Mô tả

HR Admin

Chỉnh sửa toàn bộ thông tin hồ sơ nhân sự

User được phân quyền (tuỳ chọn)

Có thể được cấp quyền edit theo đặc thù vị trí

4. Workflow tổng quan
4.1 Luồng chỉnh sửa từ trang chi tiết
User mở Chi tiết hồ sơ nhân sự

Nhấn Chỉnh sửa

Hệ thống kiểm tra permission EDIT_EMPLOYEE_PROFILE (tên code theo catalog của bạn)

User cập nhật thông tin → nhấn Lưu

Hệ thống validate → lưu → ghi audit log

Hiển thị thông báo thành công + dữ liệu cập nhật

4.2 Trường hợp sửa Job Title
User thay đổi Job Title

Hệ thống tự cập nhật Job Level theo Job Title

Áp quy tắc xử lý quyền theo Job Level (chi tiết ở Business Rules)

5. User Story
As a HR Admin (và/hoặc user được phân quyền)
I want chỉnh sửa thông tin hồ sơ nhân sự
So that dữ liệu nhân sự luôn đúng và cập nhật theo thực tế.

6. Acceptance Criteria (Given/When/Then)
AC-01 – Chỉnh sửa thành công khi có quyền
Given user có permission chỉnh sửa hồ sơ

When cập nhật thông tin hợp lệ và nhấn Lưu

Then hồ sơ được cập nhật và hiển thị dữ liệu mới

AC-02 – Bị chặn khi không có quyền
Given user không có permission chỉnh sửa hồ sơ

When nhấn “Chỉnh sửa” hoặc gọi API update

Then hệ thống chặn và API trả 403 Forbidden

AC-03 – Validate dữ liệu
Given user đang chỉnh sửa

When nhập thiếu trường bắt buộc hoặc nhập sai định dạng

Then hệ thống chặn lưu và hiển thị lỗi tại field

AC-04 – Không tìm thấy hồ sơ
Given user có quyền chỉnh sửa

When chỉnh sửa hồ sơ không tồn tại

Then trả 404 Not Found

AC-05 – Audit log thay đổi
Given user chỉnh sửa hồ sơ

When lưu thành công

Then hệ thống ghi log “ai sửa – sửa field nào – trước/sau – thời gian”

AC-06 – Thay đổi Job Title cập nhật Job Level
Given user thay đổi Job Title

When lưu

Then Job Level được cập nhật đúng theo Job Title

7. Functional Requirements
7.1 FR list
ID

Yêu cầu

Mô tả ngắn

Priority

FR-01

Edit Profile UI

Form chỉnh sửa hồ sơ

High

FR-02

Permission Check

Kiểm tra quyền edit (UI + API)

High

FR-03

Field Validation

Validate bắt buộc/định dạng

High

FR-04

Save Changes

Lưu cập nhật hồ sơ

High

FR-05

Job Title Update Handling

Sửa job title → cập nhật job level

High

FR-06

Audit Log

Lưu lịch sử thay đổi

High

7.2 Danh sách nhóm field cho phép chỉnh sửa (v1.0)
Mình bám theo bộ field đã dùng ở US-01/US-02. Nếu bạn muốn “khóa” field nào không cho sửa (ví dụ Mã NV), bạn chốt ở Business Rules.

Nhóm A – Thông tin định danh

Họ và tên (cho phép sửa)

Mã nhân viên (mặc định: không cho sửa – xem BR-01)

Nhóm B – Thông tin công việc

Job Title (cho phép sửa, ảnh hưởng job level)

Job Level (auto theo job title, không sửa tay)

Ngày vào công ty (cho phép sửa nếu cần)

Trạng thái làm việc (cho phép sửa)

Nhóm C – Thông tin liên hệ

Email

Số điện thoại

Nhóm D – Tổ chức & quản lý

Phòng ban/Đơn vị

Quản lý trực tiếp

8. Non-functional Requirements (NFR)
Security: API update bắt buộc check permission.

Audit: ghi rõ “trước/sau” để truy vết.

Reliability: lưu phải atomic (không cập nhật nửa chừng).

9. Business Rules
BR-01 (đề xuất cần chốt): Mã nhân viên là unique key ⇒ không cho phép chỉnh sửa sau khi tạo.

BR-02: Job Level không sửa tay, luôn suy ra từ Job Title.

BR-03 (cần chốt): Khi Job Title đổi dẫn đến Job Level đổi:

Quyền theo Job Level có tự động cập nhật theo Job Level mới không?

Nếu user có override quyền thì override giữ nguyên hay reset?

BR-04: Chỉ user có quyền mới được chỉnh sửa.

10. Validation & Error Handling
Trường hợp

Hành vi hệ thống

Không có quyền edit

403 Forbidden

Hồ sơ không tồn tại

404 Not Found

Dữ liệu không hợp lệ

Chặn lưu, báo lỗi tại field

Job Title không hợp lệ/inactive

Chặn lưu

Lỗi hệ thống

500 + log

11. Define Of Done
DoD
Có màn hình chỉnh sửa từ trang chi tiết.

Permission check hoạt động đúng.

Validate dữ liệu đúng.

Lưu thành công và hiển thị dữ liệu mới.

Audit log đầy đủ.

Sửa Job Title → Job Level auto đúng.