1. Mục tiêu tính năng (Feature Objective)
1.1. Vấn đề cần giải quyết
Hiện tại cần một cơ chế phân quyền không định nghĩa theo Role tự do, mà định nghĩa theo cấu trúc Job Level (theo chuẩn job title/job level của tổ chức).

Cần nhìn được theo từng Job Level (ví dụ C-level):

Có những user nào thuộc Job Level đó

Job Level đó được thực thi tính năng nào (theo danh mục feature/action)

Có thể thêm ngoại lệ theo user (cấp thêm hoặc chặn riêng)

Vấn đề này xảy ra tại bước: Quản trị hệ thống HRM (thiết lập quyền) và Runtime (khi user thao tác vào các tính năng HRM).

1.2. Mục tiêu
Thiết lập cơ chế phân quyền theo Job Level làm “mặc định hệ thống”.

Hỗ trợ ngoại lệ theo user để đáp ứng trường hợp “cùng job level nhưng quyền khác nhau ở một vài tính năng”.

Outcome mong muốn (1–2 dòng):

Admin cấu hình quyền theo Job Level + override theo user; hệ thống enforce đúng ở UI/API.

2. Phạm vi tính năng (Scope)
In-scope (v1.0)
Danh mục Job Level (lấy theo chuẩn từ hệ thống Job Title/Job Level)

Mapping User → Job Level và màn hình xem danh sách user theo Job Level

Danh mục quyền (Permission Catalog) theo Feature/Action (tối thiểu hỗ trợ “xem tính năng nào được phép”)

Gán Permission theo Job Level (JobLevelPermission)

Ngoại lệ theo User (User override: Grant/Deny)

Enforcement: kiểm tra quyền tại UI & API

Out-of-scope (để v2.0+ nếu cần)
Field-level permission (chặn theo từng trường dữ liệu)

Approval workflow nhiều cấp

ABAC phức tạp theo nhiều thuộc tính

3. Đối tượng sử dụng (Target Users)
User Role

Mô tả

Quyền liên quan

System Admin / HR Admin

Thiết lập quyền theo Job Level, cấu hình ngoại lệ theo user

Manage Permission

HR Leader/HR Staff/Other Users

Sử dụng các tính năng HRM theo quyền được cấp

View/Use Feature

4. Workflow tổng quan
4.1 Thiết lập quyền theo Job Level
Admin vào màn hình Phân quyền theo Job Level

Chọn Job Level (VD: “C-level”)

Hệ thống hiển thị:

Danh sách user thuộc job level

Danh sách permission hiện đang áp dụng cho job level

Admin tick chọn / bỏ chọn permission → Lưu

4.2 Thiết lập ngoại lệ theo User (Override)
Trong Job Level đã chọn, admin chọn 1 user

Gán override:

Grant thêm permission

Deny permission (chặn riêng)

Lưu override

4.3 Runtime kiểm tra quyền
Khi user thao tác vào 1 feature HRM:

Hệ thống lấy quyền theo Job Level

Áp override theo user

Quyết định allow/deny và phản hồi UI/API

5. User Story
Core User Story
As a System Admin / HR Admin
I want cấu hình phân quyền HRM theo Job Level, xem user thuộc job level đó và gán ngoại lệ theo từng user
So that hệ thống kiểm soát đúng ai được thực thi tính năng nào theo job level và vẫn linh hoạt cho các trường hợp ngoại lệ.

6. Acceptance Criteria (AC) – Given/When/Then
AC-01: Xem danh sách Job Level
Given Admin truy cập màn hình Phân quyền theo Job Level

When hệ thống tải dữ liệu

Then hiển thị danh sách Job Level theo chuẩn hệ thống Job Title/Job Level

AC-02: Xem danh sách user theo Job Level
Given Admin chọn một Job Level

When mở tab “User trong Job Level”

Then hiển thị đầy đủ user thuộc Job Level đó

AC-03: Xem quyền (permission) đang áp dụng cho Job Level
Given Admin chọn một Job Level

When mở tab “Quyền theo Job Level”

Then hiển thị danh sách permission (feature/action) đang được gán cho Job Level đó

AC-04: Cập nhật quyền theo Job Level
Given Admin đang ở Job Level X

When admin tick thêm/bỏ permission và nhấn Lưu

Then hệ thống lưu cấu hình JobLevelPermission và cập nhật đúng khi reload

AC-05: Thiết lập override theo user (grant/deny)
Given Admin chọn user A thuộc Job Level X

When admin thêm override Grant/Deny và nhấn Lưu

Then hệ thống lưu override và hiển thị lại đúng trạng thái

AC-06: Ưu tiên Deny
Given user A có permission P từ Job Level nhưng có override Deny P

When user A thao tác feature tương ứng

Then hệ thống chặn (deny thắng)

AC-07: Enforce tại API
Given user không có quyền hợp lệ sau khi tính Job Level + override

When gọi API của feature đó

Then trả 403 Forbidden (không phụ thuộc UI)

AC-08: Audit log
Given admin thay đổi permission theo Job Level hoặc override user

When lưu thay đổi

Then hệ thống ghi nhận lịch sử: ai thay đổi, thay đổi gì, thời gian

7. Functional Requirements
7.1 Danh sách yêu cầu chức năng (FR list)
ID

Yêu cầu

Mô tả ngắn

Priority

FR-01

Job Level Catalog

Hiển thị danh mục Job Level theo chuẩn hệ thống

High

FR-02

User ↔ Job Level

Xem được danh sách user thuộc Job Level

High

FR-03

Permission Catalog

Danh mục quyền theo Feature/Action

High

FR-04

JobLevelPermission

Gán quyền cho Job Level

High

FR-05

User Override

Gán Grant/Deny theo user

High

FR-06

Permission Evaluate

Tính quyền cuối cùng theo thứ tự ưu tiên

High

FR-07

Enforcement (UI/API)

UI ẩn/disable + API trả 403 khi thiếu quyền

High

FR-08

Audit Log

Lưu lịch sử thay đổi cấu hình

Medium

7.2 Chi tiết từng Functional Requirement
FR-01: Job Level Catalog
Mô tả: Hệ thống hiển thị danh mục Job Level đang áp dụng (theo chuẩn Job Level trong hệ thống quản lý chức danh).

Điều kiện tiền đề: Có dữ liệu Job Level.

Luồng xử lý chính:
a) Admin mở màn hình phân quyền
b) Hệ thống load danh sách Job Level
c) Hiển thị dropdown/list Job Level

Trường hợp ngoại lệ: Không có Job Level → hiển thị trạng thái rỗng + hướng dẫn.

Kết quả mong đợi: Danh sách Job Level hiển thị đúng, dùng để chọn cấu hình.

FR-02: Xem danh sách user theo Job Level
Mô tả: Khi chọn Job Level, hệ thống hiển thị danh sách user thuộc Job Level đó.

Điều kiện tiền đề: User có gắn job title → suy ra job level (hoặc có bảng mapping).

Luồng xử lý chính:
a) Admin chọn Job Level X
b) Hệ thống query danh sách user thuộc X
c) Hiển thị danh sách user

Ngoại lệ: User chưa có job title/job level → đưa vào nhóm “Chưa xác định” (hoặc không hiển thị) tuỳ rule bạn đang dùng.

Kết quả mong đợi: Admin nhìn được “Cùng job level gồm những ai”.

FR-03: Permission Catalog (Feature/Action)
Mô tả: Hệ thống có danh mục permission theo cấu trúc:

FeatureCode (mã tính năng HRM)

Action (tập action dùng cho phân quyền)

Điều kiện tiền đề: Danh mục feature HRM đã được định danh (code).

Luồng xử lý chính:
a) Admin mở tab Quyền
b) Hệ thống load danh sách permission
c) Hiển thị theo nhóm feature + action

Kết quả mong đợi: Có danh mục chuẩn để gán cho job level / user.

FR-04: Gán Permission theo Job Level (JobLevelPermission)
Mô tả: Admin cấu hình permission mặc định cho từng Job Level.

Luồng xử lý chính:
a) Admin chọn Job Level X
b) Tick chọn permission
c) Lưu → hệ thống cập nhật JobLevelPermission

Ngoại lệ: Không cho phép lưu nếu danh mục permission rỗng mà hệ thống yêu cầu tối thiểu (nếu có rule).

Kết quả mong đợi: Job Level có “bộ quyền mặc định” rõ ràng.

FR-05: User Override (Grant/Deny)
Mô tả: Admin gán ngoại lệ cho user thuộc Job Level.

Luồng xử lý chính:
a) Admin chọn user A
b) Chọn override Grant/Deny permission
c) Lưu

Kết quả mong đợi: User có thể khác quyền so với Job Level mặc định.

FR-06: Permission Evaluate (tính quyền cuối)
Mô tả: Khi kiểm tra quyền, hệ thống tính theo thứ tự:

Permission theo Job Level

Override theo user

Deny ưu tiên cao nhất

Kết quả mong đợi: Quyền cuối cùng xác định nhất quán.

FR-07: Enforcement UI/API
Mô tả:

UI: ẩn/disable các action không có quyền

API: bắt buộc check permission; thiếu quyền trả 403

Kết quả mong đợi: Không thể bypass bằng gọi API trực tiếp.

FR-08: Audit Log
Mô tả: Ghi lịch sử thay đổi khi:

đổi permission theo job level

đổi override theo user

Kết quả mong đợi: Truy vết được thay đổi.

8. Non-Functional Requirements (nếu có)
Performance: Permission evaluate không được gây chậm đáng kể (có thể cache theo user/session nếu cần)

Security/Permission: API luôn enforce; không tin UI

Audit log/History: bắt buộc lưu thay đổi cấu hình phân quyền

9. Business Rules
BR-01: Quyền mặc định của user đến từ Job Level

BR-02: Deny (User) > Grant (User) > Job Level Permission

BR-03: Permission phải quản lý theo Feature/Action (không gộp mơ hồ)

BR-04: Không xóa cứng cấu hình đang dùng; ưu tiên Active/Inactive (nếu áp dụng cơ chế trạng thái)

10. Validation & Error Handling
Trường hợp

Hành vi hệ thống

Trường hợp

Hành vi hệ thống

Dữ liệu thiếu (không có Job Level/Permission)

Hiển thị trạng thái rỗng + thông báo cấu hình thiếu

Không đủ quyền thao tác màn hình quản trị

Chặn truy cập + 403

Lưu cấu hình lỗi

Hiển thị lỗi rõ ràng, không lưu một phần

Lỗi hệ thống

Trả 500 + log chi tiết

11. Define Of Done
DoD
Admin xem được danh sách Job Level

Admin xem được user theo Job Level

Admin gán permission cho Job Level và hệ thống áp dụng được

Admin gán override theo user (grant/deny) và thứ tự ưu tiên hoạt động đúng

API trả 403 khi thiếu quyền; UI ẩn/disable đúng

Có audit log cho thay đổi cấu hình

Chỉ số đo lường thành công (gợi ý theo template)
Giảm lỗi phân quyền vận hành (số ticket “sai quyền” giảm)

Thời gian thiết lập quyền giảm (so với làm thủ công theo từng user)

% tính năng HRM được enforce quyền tại API đạt 100%