1. Mục tiêu tính năng (Feature Objective)
1.1. Vấn đề cần giải quyết
Người dùng đang gặp vấn đề gì?

Không có danh mục chức danh chuẩn hóa, mỗi phòng ban/người tự đặt tên chức danh theo cách riêng

Cùng một vị trí có thể có nhiều tên gọi khác nhau (ví dụ: Developer, Lập trình viên, Software Engineer)

Khó phân loại và thống kê nhân viên theo chức năng công việc hoặc cấp bậc

Không rõ cấu trúc Job Family (nhóm công việc) để xây dựng lộ trình phát triển

Vấn đề này xảy ra ở bước nào trong workflow?

Vấn đề xảy ra ngay khi tạo hồ sơ nhân viên mới hoặc cập nhật thông tin nhân sự. HR phải nhập thủ công tên chức danh, dẫn đến sai sót và không nhất quán. Điều này ảnh hưởng đến tất cả các báo cáo, phân tích nhân sự và quản lý năng lực.

1.2. Mục tiêu
Tính năng này giúp người dùng làm được điều gì?

HR Admin quản lý danh mục chức danh theo đúng quy tắc thiết kế HG Holding

Phân biệt rõ 3 khái niệm:

Job Level (L1-L5): Vị trí trong cấu trúc tổ chức

Seniority (Junior/Mid/Senior/Lead/Principal): Độ cao cấp theo kinh nghiệm

Role Type: Manager, Lead, Staff (có/không có role title)

Thiết lập chức danh theo format chuẩn: [Cấp độ] [Chức năng]

Giá trị mang lại cho business / vận hành:

Alignment với Organizational Design: Chức danh phản ánh đúng 100% quy tắc thiết kế HG Holding

Clarity: Mọi người hiểu rõ vị trí của mình trong cấu trúc (Level) và độ cao cấp (Seniority)

Scalability: Dễ dàng mở rộng khi thêm công ty con/phòng ban mới

Standardization: Tên chức danh nhất quán 100% theo format chuẩn

Outcome mong muốn:

100% chức danh tuân thủ format [Cấp độ] [Chức năng]

Phân biệt chính xác Level (L1-L5) và Seniority (Junior-Principal)

HR có thể báo cáo phân bổ nhân sự theo Job Level và Seniority

2. Phạm vi tính năng (Scope)
In-scope
✅ Quản lý Job Level (L1-L5) theo cấu trúc HG Holding

✅ Quản lý Seniority (Junior/Mid/Senior/Lead/Principal/Fellow)

✅ Quản lý Role Type (Manager/Lead/Staff)

✅ Tạo/Sửa/Xóa chức danh với thông tin:

Mã chức danh (unique)

Tên tiếng Việt (format: [Cấp độ] [Chức năng])

Tên tiếng Anh (format: [Level] [Function])

Job Level (L1-L5)

Job Function (RedOne, HGMedia, Technology/Finance/HR/Operations/Marketing...)

Mô tả

✅ Validate format tên chức danh theo chuẩn HG Holding

✅ Kích hoạt/Vô hiệu hóa chức danh (không xóa cứng)

✅ Hiển thị trong dropdown khi tạo nhân viên

✅ Thống kê theo Job Level

✅ Tìm kiếm và lọc theo các thuộc tính

Out-of-scope (để version sau)
❌ Liên kết với Competency Framework (v2.0)

❌ Chi tiết Career Path và Promotion criteria (v2.0)

❌ Import/Export (v2.0)

❌ Job Description chi tiết (v2.0)

❌ Salary Range gắn với chức danh (v2.0)

❌ Matrix Reporting setup (v2.0)

 

3. Đối tượng sử dụng (Target Users)
User Role

Mô tả

Quyền liên quan

HR Admin

Quản trị viên HR, chịu trách nhiệm thiết kế và duy trì cấu trúc chức danh

Tạo/Sửa/Xóa chức danh, Job Level, Seniority, Role Type

HR Staff

Nhân viên HR, tạo/cập nhật hồ sơ nhân viên

Xem và chọn chức danh từ dropdown

Manager/HoD

Trưởng phòng, đề xuất tuyển dụng và thăng tiến

Xem danh sách chức danh và Promotion Path

4. Data Model & Taxonomy
4.1. Job Level (Cấp độ theo cấu trúc tổ chức)
Theo Section 3.2.1 của tài liệu HG Holding:

Level

Job Title

Trách nhiệm

Quyết định

Ví dụ

L1

Chairman, Group CEO

Chiến lược tổng thể

Toàn Tập đoàn

Chairman

L2.1

C-Level

Điều hành chức năng

Toàn chức năng

Group CFO, Group CHRO, GMD

L2.2

Director, CEO công ty con

Quản lý phòng ban/company

Phòng ban/công ty

CEO HG Media

L3

Trưởng phòng (HoD)

Quản lý team, đội nhóm

Team, member

Trưởng Phòng Marketing

L4.1

Manager

Dẫn dắt nhóm lớn

Nhóm lớn

Quản lý Thiết Kế

L4.2

Lead

Dẫn dắt nhóm nhỏ

Nhóm nhỏ

Trưởng Nhóm Frontend

L5

Staff, Executive

Thực thi công việc

Cá nhân

Senior Developer, Junior Designer

4.2. Job Function (Chức năng công việc) Hiểu rõ để trong việc đặt tên chức danh
Theo Section 1.1.1 - Trục 2: Chức năng vs Sản phẩm:

Function (Chức năng):

Technology

Finance

HR (Human Resources)

Operations

Legal

Marketing

Sales

Product (Sản phẩm/Dịch vụ):

HG Media

RED ONE Media

Forest Music

(các công ty con khác)

4.3. Format Tên Chức danh
Theo Section 3.1.1 - Naming Convention:

Format chuẩn: [Cấp độ] [Chức năng]

Ví dụ từ tài liệu:

✅ Chairman

✅ Group CFO

✅ CEO HGMEDIA

✅ Trưởng Phòng Marketing

✅ Quản lý Thiết Kế

✅ Senior Developer

✅ Junior Designer

Quy tắc:

Không dùng tên người (❌ "Team của Anh Dũng")

Dùng tên chức năng, không dùng tên dự án tạm thời

Ngắn gọn, dễ nhớ (2-4 từ)

5. User Story
Core User Story
As a Nhân viên HR
I want quản lý danh mục chức danh theo đúng quy tắc thiết kế HG Holding với đầy đủ: Job Level (L1-L5), Seniority (Junior-Principal), Role Type (Manager/Lead/Staff), Job Category, Job Function và Promotion Path
So that đảm bảo tính nhất quán, phản ánh đúng cấu trúc tổ chức và hỗ trợ phát triển nghề nghiệp

6. Acceptance Criteria (AC)
AC1: Tạo mới chức danh L5 (Staff) - Case thông thường
Given tôi đang ở danh mục Chức danh
When tôi click "Thêm chức danh" → chọn Job Level = "L5 - Staff, Executive"
Then

Form hiển thị đầy đủ các trường:

✅ Mã chức danh (required)

✅ Tên TV (required)

✅ Tên EN ( optional )

✅ Job Level (pre-selected: L5)

✅ Job Function (required)

✅ Mô tả (optional)

When tôi nhập:

Mã: HGHolding-L5-001

Tên TV: Senior Developer

Tên EN: Senior Developer

Job Level: L5

Job Function: Technology

Then

✅ Chức danh được tạo thành công

✅ Hiển thị trong danh sách với format: "Senior Developer (L5 - Senior)"

✅ Trạng thái = Active

AC2: Role Type auto-set theo Job Level
Given tôi đang tạo chức danh
When tôi chọn Job Level:

L4.1 → Role Type auto-set = "Manager" (disabled, không cho đổi)

L4.2 → Role Type auto-set = "Lead" (disabled, không cho đổi)

L5 → Role Type auto-set = "Staff" (disabled, không cho đổi)

L1-L3 → Role Type = NULL (field hidden)

Then

✅ Role Type tự động khớp với Job Level

❌ User không thể thay đổi Role Type manually

AC3: Dropdown chức danh hiển thị đúng khi tạo nhân viên
Given có các chức danh:

"Senior Developer" (L5, Active)

"Lead Developer" (L5, Active)

"Flash Developer" (L5, Inactive)

"Trưởng Phòng Marketing" (L3, Active)

"CEO HG Media" (L2.2, Active)

When HR tạo hồ sơ nhân viên mới và mở dropdown "Chức danh"
Then

✅ Hiển thị chỉ chức danh Active

✅ Group by Job Function:



  [Technology]
    - Senior Developer (L5 - Senior - IC)
    - Lead Developer (L5 - Lead - IC)
  [Marketing]
    - Trưởng Phòng Marketing (L3 - HoD)
  [Leadership]
    - CEO HG Media (L2.2 - Director)
✅ Sort: Level cao → thấp, Seniority cao → thấp

❌ "Flash Developer" không hiển thị (Inactive)

AC4: Thống kê hiển thị đúng số lượng nhân viên
Given có:

15 nhân viên với chức danh "Senior Developer"

5 nhân viên với chức danh "Flash Developer" (Inactive)

When tôi xem danh sách chức danh
Then

✅ Cột "Số lượng nhân viên" hiển thị:

Senior Developer: 15 người

Flash Developer: 5 người (với note: Inactive)

✅ Click vào số lượng → Hiển thị danh sách nhân viên có chức danh đó

AC5: Không được xóa chức danh đang có nhân viên
Given chức danh "Senior Developer" đang có 15 nhân viên
When tôi click "Xóa" chức danh này
Then

❌ Không cho xóa

💡 Modal hiển thị: "Chức danh này có 15 nhân viên. Bạn muốn?"

[Vô hiệu hóa] → Chuyển sang Inactive (không hiển thị cho nhân viên mới)

[Xem danh sách] → Hiển thị 15 nhân viên đang dùng chức danh này

[Hủy]

When tôi click "Vô hiệu hóa"
Then

✅ Chức danh chuyển sang Inactive

✅ Không hiển thị trong dropdown khi tạo nhân viên mới

✅ Vẫn hiển thị cho 15 nhân viên hiện tại (data integrity)

AC6: Xóa chức danh không có nhân viên
Given chức danh "Test Developer" không có nhân viên nào
When tôi click "Xóa"
Then

💡 Confirm: "Xác nhận xóa chức danh 'Test Developer'? (Không có nhân viên)"

✅ Cho phép xóa (soft delete)

✅ Chức danh chuyển sang trạng thái Deleted (không hiển thị trong danh sách)

AC7: Báo cáo phân bổ theo Job Level
Given có:

350 nhân viên L5

20 nhân viên L4.2

30 nhân viên L4.1

15 nhân viên L3

5 nhân viên L2.2

5 nhân viên L2.1

1 nhân viên L1

When tôi xem báo cáo "Phân bổ theo Job Level"
Then

✅ Biểu đồ Pie Chart hiển thị:



  L5 (Staff):           350 (82.2%)
  L4.1 (Manager):        30 (7.0%)
  L4.2 (Lead):           20 (4.7%)
  L3 (HoD):              15 (3.5%)
  L2.2 (Director/CEO):    5 (1.2%)
  L2.1 (C-Level):         5 (1.2%)
  L1 (Chairman):          1 (0.2%)
✅ Click vào từng level → Drill-down chi tiết

AC8: Tìm kiếm chức danh
Given có chức danh:

"Senior Developer"

"Senior Designer"

"Lead Developer"

"Trưởng Phòng Marketing"

When tôi nhập "Senior" vào ô tìm kiếm
Then

✅ Hiển thị kết quả:

Senior Developer (L5 - Senior - IC)

Senior Designer (L5 - Senior - IC)

❌ Không hiển thị: Lead Developer, Trưởng Phòng Marketing

When tôi nhập "Trưởng"
Then

✅ Hiển thị cả:

Trưởng Phòng Marketing (L3 - HoD)

Trưởng Nhóm Frontend (L4.2 - Lead) (nếu có)

AC15: Lọc theo Job Level
Given tôi đang ở danh sách chức danh
When tôi chọn filter "Job Level = L5"
Then

✅ Hiển thị chỉ chức danh L5 (Staff)

✅ Count: "Hiển thị 150/200 chức danh"

When tôi chọn multi-select "Job Level = L3, L4.1"
Then

✅ Hiển thị chức danh L3 và L4.1

✅ Count: "Hiển thị 45/200 chức danh"

AC17: Audit log ghi lại mọi thay đổi
Given HR Admin tạo/sửa/xóa chức danh
When thao tác hoàn thành
Then

✅ Audit log ghi:

User: admin@hg.com

Action: CREATE / UPDATE / DELETE / INACTIVE

Timestamp: 2026-01-13 14:30:00

Before: (JSON của record cũ)

After: (JSON của record mới)

IP: 192.168.1.100

When Admin xem "Lịch sử thay đổi" của chức danh
Then

✅ Hiển thị timeline:



  2026-01-13 14:30 | admin@hg.com | UPDATE
    Changed: Seniority (Mid → Senior)
  2026-01-10 09:15 | hr@hg.com | CREATE
    Created: Senior Developer (L5-Senior-Staff-IC)
7. Functional Requirements
7.1. Danh sách yêu cầu chức năng
ID

Yêu cầu

Mô tả ngắn

Priority

ID

Yêu cầu

Mô tả ngắn

Priority

FR01

Quản lý Job Level

CRUD Job Level (L1-L5) theo cấu trúc HG Holding

High

FR02

Quản lý Job Function

CRUD Job Function (Technology/Finance/HR...)

High

FR03

CRUD Chức danh

Tạo/Sửa/Xóa chức danh với đầy đủ thuộc tính

High

FR04

Validate Logic

Validate sự tương thích giữa Level/Seniority/Role

High

FR05

Format Validation

Validate tên chức danh theo format chuẩn

High

FR6

Active/Inactive

Kích hoạt/Vô hiệu hóa (không xóa cứng)

High

FR8

Reporting & Analytics

Thống kê theo Level/Seniority/Role Type

Medium

FR9

Search & Filter

Tìm kiếm và lọc theo các thuộc tính

Medium

