Thông tin chung chức năng

User Story ID: US-01

Tên tính năng: Tạo mới hồ sơ nhân viên

Module: HRM – Hồ sơ nhân viên

Version: v1.0

Link thiết kế (Figma): TBD

Tiền đề liên quan:

US-07 – Quản lý Chức danh (để chọn Job Title và suy ra Job Level)

US-08 – Phân quyền theo Job Level (để gán quyền mặc định theo Job Level + ngoại lệ)

1. Mục tiêu tính năng (Feature Objective)

1.1. Vấn đề cần giải quyết

Cần một luồng thêm mới hồ sơ nhân viên vào hệ thống cho tất cả nhân sự “vào công ty”.

Người tạo/duyệt cao nhất là HR Admin (tạo xong là hợp lệ, không cần vòng duyệt khác).

Ngay khi tạo hồ sơ, cần gắn đúng chức danh để:

Suy ra Job Level

Gán phân quyền mặc định theo Job Level và (nếu cần) thêm ngoại lệ theo user.

1.2. Mục tiêu

HR Admin tạo mới hồ sơ nhân viên nhanh, chuẩn hóa thông tin đầu vào.

Hồ sơ được gắn đúng Job Title/Job Level và phân quyền ngay từ lúc tạo.

Outcome mong muốn:

100% hồ sơ mới có Mã nhân viên (unique) + Chức danh 

Quyền HRM của user sau tạo được áp dụng đúng theo Job Level (và ngoại lệ nếu có).

2. Phạm vi tính năng (Scope)

In-scope (v1.0)

Tạo mới hồ sơ nhân viên (1 nhân sự/lần).

Bắt buộc nhập Mã nhân viên (unique key).

Chọn Chức danh khi tạo → hệ thống suy ra Job Level.

Gán quyền mặc định theo Job Level (theo US-08).

Cho phép HR Admin cấu hình ngoại lệ quyền theo user ngay trong flow tạo (tuỳ chọn).

Out-of-scope (v1.0)

Import hồ sơ hàng loạt.

Quy trình phê duyệt nhiều cấp trước khi active.

Tạo credential/đăng nhập chi tiết (nếu có SSO/IT provisioning sẽ là user story khác).

3. Đối tượng sử dụng (Target Users)

Actor

Mô tả

HR Admin

Tạo mới hồ sơ, duyệt cuối, gán chức danh & quyền phù hợp; có thể trao quyền cho người khác sau này

4. Workflow tổng quan

4.1 Luồng tạo hồ sơ

HR Admin vào HRM → Hồ sơ nhân viên → Tạo mới

Nhập thông tin hồ sơ (theo các nhóm field bên dưới)

Chọn Chức danh

Hệ thống tự động:

Suy ra Job Level

Gán quyền mặc định theo Job Level (US-08)

(Tuỳ chọn) HR Admin cấu hình ngoại lệ quyền cho nhân viên này (Grant/Deny)

Nhấn Lưu → tạo hồ sơ thành công

5. User Story

As a HR Admin
I want tạo mới hồ sơ nhân viên và gắn chức danh ngay lúc tạo để hệ thống tự gán Job Level và phân quyền mặc định (kèm ngoại lệ nếu cần)
So that nhân viên được đưa vào hệ thống đầy đủ thông tin và quyền HRM đúng ngay từ đầu.

6. Acceptance Criteria (Given/When/Then)

AC-01 – Tạo hồ sơ thành công

Given HR Admin đang ở màn hình “Tạo mới hồ sơ nhân viên”

When nhập đủ các trường bắt buộc và nhấn Lưu

Then hồ sơ được tạo thành công và hiển thị trong danh sách hồ sơ

AC-02 – Mã nhân viên là unique key

Given đã tồn tại hồ sơ có Mã nhân viên HGHold001

When HR Admin tạo hồ sơ mới với Mã nhân viên HGHoldP001

Then hệ thống chặn lưu và hiển thị lỗi “Mã nhân viên đã tồn tại”

AC-03 – Chọn Job Title → tự suy ra Job Level

Given HR Admin chọn một Job Title hợp lệ

When Job Title được chọn

Then hệ thống tự hiển thị Job Level tương ứng (không cần nhập tay)

AC-04 – Gán quyền mặc định theo Job Level

Given hồ sơ được tạo với Job Level = X

When tạo thành công

Then user này được gán bộ quyền HRM mặc định theo Job Level X (theo US-08)

AC-05 – Ngoại lệ theo user (tuỳ chọn)

Given HR Admin thiết lập override cho user (Grant/Deny) trước khi lưu

When tạo hồ sơ thành công

Then quyền cuối cùng của user tuân theo ưu tiên: Deny > Grant > Job Level

7. Functional Requirements

7.1 Danh sách Field đề xuất (v1.0)

Bạn yêu cầu mình “tạo giúp fields”. Mình đề xuất bộ field tối thiểu theo chuẩn hệ thống HRM, và vẫn bám chặt các điều bạn đã chốt: Mã nhân viên unique, chọn chức danh khi tạo, gán quyền theo job level.

Nhóm A – Thông tin định danh (bắt buộc tối thiểu)

Mã nhân viên (Required, Unique)

Họ và tên (Required)

Nhóm B – Thông tin công việc (bắt buộc để gán org/job)

Job Title (Required – chọn từ danh mục US-07)

Job Level (Auto – suy ra từ Job Title, read-only)

Ngày vào công ty (Required)

Trạng thái làm việc (Default = Active; có thể mở rộng Draft/Inactive nếu bạn muốn)

Nhóm C – Thông tin liên hệ (khuyến nghị)

Email

Số điện thoại

Nhóm D – Tổ chức & quản lý (khuyến nghị, nếu dữ liệu đã sẵn có)

Đơn vị/Phòng ban (Org Unit)

Người quản lý trực tiếp (Line Manager)

Nhóm E – Phân quyền (áp dụng ngay khi tạo)

Bộ quyền mặc định theo Job Level (auto apply từ US-08)

Override theo user (tuỳ chọn): Grant/Deny

Nhóm F – Các thông tin khác cần xem xét….

7.2 Chi tiết Functional Requirements

FR-01 – CRUD hồ sơ nhân viên

HR Admin tạo mới hồ sơ với các field bắt buộc tối thiểu (A+B).

Lưu thành công tạo ra 1 bản ghi hồ sơ.

FR-02 – Validate Mã nhân viên unique

Mã nhân viên là khoá duy nhất.

Không cho phép lưu nếu trùng.

FR-03 – Chọn Job Title khi tạo

Job Title là danh mục chuẩn (US-07).

Job Level tự sinh theo Job Title, không nhập tay.

FR-04 – Auto apply phân quyền theo Job Level

Sau khi xác định Job Level, hệ thống gán quyền HRM theo US-08.

FR-05 – Thiết lập override quyền theo user (tuỳ chọn)

HR Admin có thể chọn Grant/Deny permission cho user trong quá trình tạo.

Quy tắc ưu tiên: Deny > Grant > Job Level.

FR-06 – Audit log

Ghi nhận: ai tạo hồ sơ, thời điểm, thay đổi gì (tạo mới + cấu hình quyền nếu có).

8. Non-functional Requirements (NFR)

Security: chỉ HR Admin (hoặc người được HR Admin trao quyền sau này) mới tạo hồ sơ.

Auditability: bắt buộc có audit log cho tạo mới và override quyền.

Reliability: không được tạo “nửa vời” (lưu hồ sơ nhưng không gán job level/quyền).

9. Business Rules

BR-01: Mã nhân viên là unique key toàn hệ thống.

BR-02: Job Level không nhập tay, phải suy ra từ Job Title.

BR-03: Quyền HRM mặc định lấy theo Job Level (US-08).

BR-04: Nếu có override quyền theo user: Deny > Grant > Job Level.

BR-05: Người tạo/duyệt cao nhất là HR Admin → tạo xong có hiệu lực ngay (không có bước approval khác).

10. Validation & Error Handling

Trường hợp

Hành vi hệ thống

Thiếu trường bắt buộc (Mã NV, Họ tên, Job Title, Ngày vào)

Chặn lưu, highlight field + thông báo rõ

Mã nhân viên bị trùng

Chặn lưu, báo “Mã nhân viên đã tồn tại”

Job Title không hợp lệ / bị inactive

Chặn lưu, yêu cầu chọn lại

Lỗi khi gán quyền theo Job Level

Chặn tạo (rollback), báo lỗi hệ thống

Không đủ quyền tạo hồ sơ

403 Forbidden

11. Define Of Done

DoD

HR Admin tạo được hồ sơ mới với bộ field tối thiểu.

Validate Mã nhân viên unique hoạt động đúng.

Chọn Job Title → Job Level auto đúng.

Quyền theo Job Level được gán sau khi tạo (và override nếu có).

Có audit log.

Chỉ số đo lường (gợi ý)

% hồ sơ mới có đầy đủ Mã NV + Job Title + Job Level đạt 100%

Giảm lỗi vận hành do thiếu job level/quyền sau onboarding