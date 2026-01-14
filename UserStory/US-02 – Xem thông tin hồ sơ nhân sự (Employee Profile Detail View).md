Thông tin chung chức năng
User Story ID: US-02

Tên tính năng: Xem thông tin chi tiết hồ sơ nhân sự

Module: HRM – Hồ sơ nhân viên

Version: v1.0

Link thiết kế (Figma): TBD

Phụ thuộc:

US-01 – Tạo mới hồ sơ nhân viên (có dữ liệu hồ sơ để xem)

US-08 – Phân quyền theo Job Level (xác định ai được xem hồ sơ)

1. Mục tiêu tính năng (Feature Objective)
1.1. Vấn đề cần giải quyết
Sau khi nhân sự được tạo vào hệ thống, cần màn hình/luồng để xem chi tiết toàn bộ thông tin hồ sơ nhân viên theo đúng quyền truy cập.

Người dùng cần xem:

Thông tin định danh (mã NV, họ tên…)

Thông tin công việc (job title/job level, ngày vào…)

Các thông tin liên hệ / tổ chức / quản lý trực tiếp (nếu có)

Thông tin cá nhân, tài liệu chi tiết về bản thân nhân sự.

Hệ thống cần đảm bảo phân quyền: ai không có quyền thì không xem được.

1.2. Mục tiêu
Cung cấp trang “Chi tiết hồ sơ nhân viên” để tra cứu nhanh, đầy đủ, nhất quán dữ liệu.

Enforce quyền truy cập ở UI + API theo cơ chế quyền của HRM (US-08).

2. Phạm vi tính năng (Scope)
In-scope (v1.0)
Xem chi tiết hồ sơ nhân viên theo Employee ID / Mã nhân viên.

Hiển thị thông tin theo các nhóm dữ liệu đã được lưu trong hồ sơ (từ US-01 và các thông tin mở rộng nếu hệ thống có).

Kiểm tra quyền truy cập (permission) trước khi trả dữ liệu.

Audit log truy cập (tối thiểu: ai xem, xem hồ sơ nào, thời điểm) nếu bạn yêu cầu.

Out-of-scope (v1.0)
Chỉnh sửa hồ sơ (để ở US-03 nếu có).

Export/Print hồ sơ.

Field-level permission (ẩn theo từng trường nhạy cảm) – nếu cần sẽ tách user story.

3. Đối tượng sử dụng (Target Users)
Theo thông tin bạn đã chốt trước đó: ban đầu là HR Admin, và HR Admin có thể trao quyền cho người khác theo đặc thù vị trí.

Actor

Mô tả

HR Admin

Xem toàn bộ chi tiết hồ sơ nhân viên

User được phân quyền (tuỳ chọn)

Các user khác được phép xem theo permission HRM (US-08)

4. Workflow tổng quan
4.1 Luồng xem chi tiết từ danh sách
User vào HRM → Danh sách nhân sự

Chọn 1 nhân sự → nhấn “Xem chi tiết”

Hệ thống kiểm tra quyền VIEW_EMPLOYEE_PROFILE (tên permission code sẽ theo catalog của bạn)

Nếu hợp lệ → hiển thị trang chi tiết hồ sơ

Nếu không hợp lệ → chặn truy cập (UI + API)

5. User Story
As a HR Admin (và/hoặc user được phân quyền)
I want xem thông tin chi tiết hồ sơ nhân sự
So that tôi tra cứu được đầy đủ thông tin nhân sự để phục vụ nghiệp vụ HRM.

6. Acceptance Criteria (Given/When/Then)
AC-01 – Xem chi tiết thành công khi có quyền
Given user có permission xem hồ sơ nhân sự

When user mở trang chi tiết của nhân sự A

Then hệ thống hiển thị đầy đủ thông tin chi tiết hồ sơ của A

AC-02 – Bị chặn khi không có quyền
Given user không có permission xem hồ sơ nhân sự

When user mở trang chi tiết hồ sơ

Then hệ thống chặn truy cập và API trả 403 Forbidden

AC-03 – Không tìm thấy hồ sơ
Given user có quyền xem

When mở hồ sơ với ID/Mã nhân viên không tồn tại

Then hệ thống hiển thị “Không tìm thấy hồ sơ” (404)

AC-04 – Thông tin hiển thị đúng theo dữ liệu lưu
Given hồ sơ nhân sự đã được tạo với các trường dữ liệu X

When mở trang chi tiết

Then hiển thị đúng giá trị các trường theo dữ liệu đã lưu

AC-05 – Audit log (nếu bật)
Given hệ thống bật audit log truy cập hồ sơ

When user xem hồ sơ nhân sự

Then ghi log “ai xem – xem ai – lúc nào”

7. Functional Requirements
7.1 Danh sách yêu cầu chức năng (FR list)
ID

Yêu cầu

Mô tả ngắn

Priority

FR-01

Open Profile Detail

Mở trang chi tiết hồ sơ theo ID/Mã NV

High

FR-02

Permission Check

Kiểm tra quyền xem hồ sơ (UI + API)

High

FR-03

Profile Data Rendering

Hiển thị dữ liệu hồ sơ theo nhóm thông tin

High

FR-04

Not Found Handling

Xử lý 404 khi hồ sơ không tồn tại

High

FR-05

Audit Log (optional)

Ghi nhận lịch sử truy cập

Medium

7.2 Chi tiết hiển thị dữ liệu (theo nhóm)
Mình bám theo những nhóm field đã đề xuất ở US-01. Khi hệ thống có thêm field, trang chi tiết sẽ hiển thị tương ứng.

Nhóm A – Thông tin định danh

Mã nhân viên (unique)

Họ và tên

Nhóm B – Thông tin công việc

Job Title (từ US-07)

Job Level (suy ra từ Job Title)

Ngày vào công ty

Trạng thái làm việc

Nhóm C – Thông tin liên hệ

Email

Số điện thoại

Nhóm D – Tổ chức & quản lý

Đơn vị/Phòng ban (Org Unit) (nếu đã có dữ liệu)

Quản lý trực tiếp (Line Manager) (nếu đã có dữ liệu)

Nhóm E – Thông tin phân quyền (hiển thị cho HR Admin)

Quyền mặc định theo Job Level (từ US-08)

Override theo user (nếu có)

Nhóm F - Các thông tin chi tiết khác 

8. Non-functional Requirements (NFR)
Security: Bắt buộc enforce quyền ở API (không tin UI).

Performance: Thời gian mở trang chi tiết không bị chậm đáng kể khi dữ liệu tăng.

Auditability: Có thể bật audit log truy cập hồ sơ (tuỳ chọn theo policy).

9. Business Rules
BR-01: Chỉ user có permission xem hồ sơ nhân sự mới truy cập được.

BR-02: Quyền xem hồ sơ áp dụng theo cơ chế US-08 (Job Level + override).

BR-03: Nếu hồ sơ không tồn tại → trả 404 (không lộ thông tin).

10. Validation & Error Handling
Trường hợp

Hành vi hệ thống

Không có quyền xem

403 Forbidden

Hồ sơ không tồn tại

404 Not Found + thông báo rõ

Lỗi hệ thống

500 + log

11. Define Of Done
DoD
Mở được trang chi tiết hồ sơ theo ID/Mã NV.

Hiển thị đúng dữ liệu hồ sơ theo các nhóm thông tin.

Permission check hoạt động đúng (UI + API).

Xử lý 404 đúng.

(Nếu áp dụng) audit log truy cập hoạt động.

