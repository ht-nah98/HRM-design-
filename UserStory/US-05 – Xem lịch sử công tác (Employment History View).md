Thông tin chung chức năng
User Story ID: US-05

Tên tính năng: Xem lịch sử công tác của nhân viên

Module: HRM – Hồ sơ nhân viên → Lịch sử công tác

Version: v1.0

Link thiết kế (Figma): TBD

Phụ thuộc:

US-02 – Xem chi tiết hồ sơ nhân sự (điểm vào trang hồ sơ để xem lịch sử)

US-03 – Chỉnh sửa hồ sơ (nếu lịch sử công tác có thể phát sinh thay đổi liên quan công việc)

1. Mục tiêu tính năng (Feature Objective)
1.1. Vấn đề cần giải quyết
Cần một nơi trong hồ sơ nhân viên để tra cứu lịch sử công tác (các giai đoạn làm việc, thay đổi chức danh/đơn vị/quản lý, trạng thái làm việc…).

Lịch sử công tác giúp HR/Stakeholder:

Nắm được quá trình làm việc của nhân viên theo thời gian

Dễ truy vết khi có tranh chấp/đối soát thông tin

Hỗ trợ báo cáo, đánh giá, và nghiệp vụ nhân sự

1.2. Mục tiêu
Hiển thị lịch sử công tác theo dòng thời gian, rõ ràng, dễ tra cứu.

Enforce quyền truy cập theo cơ chế phân quyền HRM (US-08).

2. Phạm vi tính năng (Scope)
In-scope (v1.0)
Tab/Mục “Lịch sử công tác” trong chi tiết hồ sơ nhân viên.

Hiển thị danh sách các bản ghi lịch sử (timeline hoặc table).

Cho phép filter/sort theo thời gian.

Xem chi tiết 1 bản ghi lịch sử (nếu cần).

Out-of-scope (v1.0)
Tạo/sửa/xóa lịch sử công tác thủ công (nếu bạn muốn chỉnh sửa được thì sẽ là user story riêng).

Workflow phê duyệt thay đổi công tác.

Export lịch sử.

3. Đối tượng sử dụng (Target Users)
Actor

Mô tả

HR Admin / HR Staff

Xem lịch sử công tác phục vụ nghiệp vụ

User được phân quyền

Có thể xem theo permission

4. Workflow tổng quan
4.1 Xem lịch sử công tác
User mở Chi tiết hồ sơ nhân viên

Chọn tab Lịch sử công tác

Hệ thống kiểm tra permission VIEW_EMPLOYMENT_HISTORY

Hiển thị lịch sử công tác theo thời gian (mới nhất trước hoặc timeline)

4.2 Filter/Sort
User chọn filter (khoảng thời gian / loại thay đổi)

Hệ thống trả danh sách tương ứng

5. User Story
As a HR Admin/HR Staff (hoặc user được phân quyền)
I want xem lịch sử công tác của nhân viên
So that tôi tra cứu được quá trình làm việc và các thay đổi công tác khi cần.

6. Acceptance Criteria (Given/When/Then)
AC-01 – Xem lịch sử khi có quyền
Given user có quyền xem lịch sử công tác

When mở tab “Lịch sử công tác” của nhân viên A

Then hệ thống hiển thị danh sách lịch sử công tác của A

AC-02 – Không có dữ liệu lịch sử
Given user có quyền xem

When nhân viên A chưa có bản ghi lịch sử công tác

Then hiển thị trạng thái rỗng “Chưa có lịch sử công tác”

AC-03 – Sort/Filter hoạt động đúng
Given có nhiều bản ghi lịch sử

When user filter theo thời gian hoặc sort

Then danh sách hiển thị đúng theo điều kiện đã chọn

AC-04 – Xem chi tiết bản ghi (nếu có)
Given user có quyền xem

When click vào một bản ghi lịch sử

Then hiển thị chi tiết thay đổi (trước/sau) của bản ghi đó

7. Functional Requirements
7.1 FR list
ID

Yêu cầu

Mô tả ngắn

Priority

FR-01

Employment History Tab

Tab lịch sử công tác trong hồ sơ

High

FR-03

History List View

Hiển thị danh sách lịch sử theo thời gian

High

FR-04

Filter/Sort

Lọc/sắp xếp theo thời gian/loại thay đổi

Medium

FR-05

History Detail

Xem chi tiết một bản ghi (tuỳ chọn)

Medium

FR-06

Audit/Source

Hiển thị “ai thay đổi/lý do” nếu có dữ liệu

Medium

7.2 Định nghĩa “bản ghi lịch sử công tác” (đề xuất v1.0)
Vì bạn chưa đưa cấu trúc lịch sử công tác cụ thể, mình định nghĩa tối thiểu theo đúng nghiệp vụ HRM phổ biến để bạn duyệt/loại bỏ.

Mỗi bản ghi lịch sử công tác gồm:

Từ ngày (effective_from) (Required)

Đến ngày (effective_to) (Optional; null nếu hiện tại)

Chức danh (Job Title) (Required)

Job Level (Auto theo Job Title)

Đơn vị/Phòng ban (Optional nếu dùng US-06)

Quản lý trực tiếp (Optional)

Loại sự kiện thay đổi (Event Type) (Required)
Ví dụ: Onboard / Thăng chức / Điều chuyển / Thay quản lý / Nghỉ việc …

Ghi chú/Lý do (Optional)

Người cập nhật (Optional nhưng nên có)

Thời điểm cập nhật (Required)

8. Non-functional Requirements (NFR)
Security: API enforce permission.

Performance: load lịch sử nhanh (paging nếu nhiều).

Traceability: ưu tiên có “người cập nhật + thời gian” cho từng bản ghi.

9. Business Rules
BR-01: User không có quyền → không xem được lịch sử.

BR-02: Lịch sử hiển thị theo thứ tự thời gian (mới nhất trước) hoặc timeline (tuỳ UI).

BR-03 (cần chốt): Lịch sử công tác được tạo từ đâu?

Tự sinh từ các thay đổi hồ sơ (job title/org/manager/status)

Hay có màn hình riêng để HR nhập lịch sử thủ công?

10. Validation & Error Handling
Trường hợp

Hành vi hệ thống

Không có quyền

403 Forbidden

Hồ sơ nhân viên không tồn tại

404 Not Found

Không có lịch sử

Trạng thái rỗng

Lỗi hệ thống

500 + log

11. Define Of Done
DoD
Có tab “Lịch sử công tác” trong chi tiết hồ sơ.

Xem được danh sách lịch sử theo nhân viên.

Permission check hoạt động đúng.

Filter/sort hoạt động (nếu in-scope).

Hiển thị rõ các thông tin chính của từng bản ghi.