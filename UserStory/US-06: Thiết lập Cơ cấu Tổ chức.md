1. Mục tiêu tính năng (Feature Objective)
1.1. Vấn đề cần giải quyết
Người dùng đang gặp vấn đề gì?

HR Admin không có công cụ để thiết lập và quản lý, trực quan hóa cơ cấu tổ chức theo chuẩn HG Holding (Tập đoàn → Khối, Công ty → Phòng ban → Nhân sự)

Việc phân quyền, đồng bộ hệ thống nội bộ không thể thực hiện vì thiếu cơ cấu tổ chức rõ ràng làm cơ sở cốt lõi

Khó khăn trong việc xác định trách nhiệm, phối hợp công việc liên phòng ban, mơ hồ về vị trí trong bối cảnh tổng thể .

Vấn đề này xảy ra ở bước nào trong workflow?

Vấn đề xảy ra ngay từ bước đầu tiên trong quy trình quản lý nhân sự - khi cần xác định vị trí và vai trò của từng nhân viên trong tổ chức. Đây là bước nền tảng, ảnh hưởng đến tất cả các quy trình tiếp theo như phân quyền, chấm công, tính lương, và báo cáo và đồng bộ hóa hệ thống nội bộ tập đoàn.

1.2. Mục tiêu
Tính năng này giúp người dùng làm được điều gì?

HR Admin, Quản Lý Cấp Cao có xem và quản lý toàn bộ cơ cấu tổ chức 5 cấp theo chuẩn HG Holding

Xem sơ đồ tổ chức dạng tree view và org chart trực quan

Tạo, sửa, xóa các đơn vị tổ chức (Tập đoàn, Công ty, Khối, Phòng ban) một cách linh hoạt

Gán nhân viên vào từng đơn vị và thiết lập đồng bộ hệ thống tool nội bộ dễ dàng.

Giá trị mang lại cho business / vận hành:

Cơ sở dữ liệu tập trung: 100% cơ cấu tổ chức được lưu trữ trong hệ thống,

Tăng độ chính xác: Giảm 90% sai sót về cấu trúc tổ chức do dữ liệu không đồng bộ

Hỗ trợ phân quyền: Cung cấp nền tảng để xây dựng hệ thống phân quyền theo cấp bậc và phòng ban

Tăng khả năng mở rộng: Dễ dàng thêm/bớt các đơn vị khi công ty phát triển mà không làm đổ vỡ hệ thống

Minh bạch thông tin: Mọi nhân viên hiểu rõ vị trí, vai trò và đường báo cáo của mình

Outcome mong muốn:

Sau 2 tuần triển khai, 100% cơ cấu tổ chức được nhập vào hệ thống, trực quan rõ ràng, minh bạch

Hệ thống được đồng bộ 80%, các tool sẽ sử dụng sơ đồ tổ chức mới để phân quyền, cập nhật ở các tool nội bộ

2. Phạm vi tính năng (Scope)
In-scope
Tạo/Sửa/Xóa các cấp tổ chức: Tập đoàn, Công ty, Khối, Phòng ban

Gán nhân viên vào từng đơn vị tổ chức

Thiết lập reporting line (người quản lý trực tiếp) cho từng nhân viên

Xem sơ đồ tổ chức dạng Org Chart (sơ đồ trực quan)

Hiển thị thông tin tổng quan: số lượng nhân viên trong từng đơn vị

Out-of-scope (để version sau)
Lịch sử thay đổi cơ cấu tổ chức (audit log v2.0)

Workflow phê duyệt thay đổi cơ cấu (v2.0)

Drag & drop để sắp xếp cấu trúc (v2.0)

3. Đối tượng sử dụng (Target Users)
User Role

Mô tả

Quyền liên quan

HR Admin, Chủ Tịch

Quản trị viên HR, chịu trách nhiệm quản lý toàn bộ hệ thống nhân sự

Full quyền: Tạo/Sửa/Xóa toàn bộ cơ cấu tổ chức

Manager/HoD

Trưởng phòng, Giám đốc các cấp

Chỉ xem cơ cấu phòng ban/khối mình quản lý

Staff (Nhân viên)

Tất cả nhân viên trong công ty

Không được xem ???

Core User Story
As a HR Admin

I want thiết lập và xem sơ đồ tổ chức của công ty theo cấu trúc 5 cấp (Tập đoàn →  Khối, Công ty → Phòng ban → Nhân sự)

So that phản ánh đúng cấu trúc quản lý thực tế, phục vụ cho việc phân quyền và trực quan hóa hệ thống cơ cấu tổ chức

6. Acceptance Criteria (AC)
AC1: Tạo mới đơn vị tổ chức

Given HR Admin đang ở màn hình quản lý cơ cấu tổ chức

When tôi chọn một đơn vị cha và click "Thêm đơn vị con", nhập thông tin (Tên, Loại: Công ty/Khối/Phòng ban), và click "Lưu" (không thêm được nhân viên ở đây)

Then đơn vị mới được tạo và hiển thị trong sơ đồ tổ chức, hệ thống hiển thị thông báo thành công

AC2: Validate tên đơn vị không trùng

Given đã tồn tại phòng ban "Phòng Marketing" dưới "Khối Kinh doanh"

When tôi cố tạo thêm một phòng ban khác cũng tên "Phòng Marketing" dưới cùng "Khối Kinh doanh"

Then hệ thống hiển thị lỗi "Tên đơn vị đã tồn tại trong cùng cấp cha" và không cho phép lưu

AC3: Xem sơ đồ tổ chức dạng Org Chart

Given cơ cấu tổ chức đã được thiết lập

When tôi chọn tab "Org Chart"

Then hệ thống hiển thị sơ đồ tổ chức dạng hình khối, thể hiện rõ mối quan hệ cấp trên-cấp dưới

AC4: Hiện thị số lượng nhân viên trong phòng ban → các đơn vị

Given đã tồn tại phòng ban Phòng IT và nhân viên 

When tôi muốn xem số lượng nhân sự theo từng phòng, ban, khối, công ty

Then nắm rõ thông tin tổng thể về số lượng nhân sự theo từng cấp

AC5: Xóa đơn vị có nhân viên

Given "Phòng IT" đang có 5 nhân viên

When tôi click "Xóa" phòng ban này

Then hệ thống hiển thị cảnh báo "Phòng ban có 5 nhân viên. Vui lòng chuyển nhân viên trước khi xóa" và không cho phép xóa

AC6: Tìm kiếm đơn vị 

Given đang ở màn hình sơ đồ tổ chức

When tôi nhập từ khóa vào ô tìm kiếm (ví dụ: "Marketing")

Then hệ thống highlight và cuộn đến các đơn vị/ có tên chứa từ khóa

AC7: Lịch sử thay đổi

Given đang ở màn hình sơ đồ tổ chức

When tôi thay đổi, thêm, sửa, xóa nhân sự phòng ban, ..

Then hệ thống sẽ log lại các thông tin để tôi đối chiếu và kiểm soát thông tin

7. Functional Requirements
7.1. Danh sách yêu cầu chức năng
ID

Yêu cầu

Priority

FR01

Quản lý CRUD (Tạo/Đọc/Sửa/Xóa) đơn vị tổ chức

High

FR02

Logs lịch sử thay đổi

High

FR03

Hiển thị sơ đồ tổ chức dạng Org Chart

High

FR04

Tìm kiếm đơn vị 

Medium

FR05

Validation và xử lý lỗi

Medium

7.2. Chi tiết từng Functional Requirement
FR01: Quản lý CRUD đơn vị tổ chức

Mô tả:

HR Admin có thể tạo mới, xem, cập nhật và xóa các đơn vị tổ chức theo cấu trúc 5 cấp: Tập đoàn → Khối, Công ty → Phòng ban → Nhân sự

Điều kiện tiền đề:

User đã đăng nhập với role HR Admin

Đã có ít nhất 1 Tập đoàn trong hệ thống (seed data)

Luồng xử lý chính:

HR Admin truy cập màn hình "Quản lý Cơ cấu Tổ chức"

Chọn đơn vị cha (ví dụ: Khối Kinh doanh) → Click "Thêm đơn vị con"

Nhập thông tin: Tên đơn vị, Loại (Công ty/Khối/Phòng ban), Mô tả (tùy chọn)

Hệ thống validate: tên không trùng trong cùng cấp cha, tên không rỗng

Click "Lưu" → Đơn vị được tạo và hiển thị trong sơ đồ

Trường hợp ngoại lệ:

Nếu tên đơn vị trùng → Hiển thị lỗi "Tên đơn vị đã tồn tại trong cùng cấp cha"

Nếu cố xóa đơn vị có nhân viên → Hiển thị lỗi "Vui lòng chuyển nhân viên trước khi xóa"

Nếu cố xóa đơn vị có đơn vị con → Hiển thị lỗi "Vui lòng xóa các đơn vị con trước"

Kết quả mong đợi:

Đơn vị tổ chức được tạo/cập nhật/xóa thành công, sơ đồ tổ chức được cập nhật real-time

FR02: Logs lịch sử thay đổi sơ đồ tổ chức

Mô tả:

HR Admin xem và tìm kiếm lại lịch sử thay đổi vị trí đã xay ra trong sơ đồ tổ chức

Luồng xử lý chính:

Thay đổi vị trí nhân sự, thêm phòng ban, thêm nhân sự

Hệ thống hiển thị thông tin chi tiết của sự thay đổi, cập nhật realtime

Kết quả mong đợi:

HR admin có thể theo dõi chính xác, minh bạch thông tin 24/24 về bất kì sự thay đổi nào trong sơ đồ bộ máy tổ chức

FR03-FR05:

8. Non-Functional Requirements
Performance:

Thời gian load sơ đồ tổ chức < 2 s với 400 nhân viên

Thời gian tìm kiếm < 1 s

Hỗ trợ mở rộng lên 1000+ nhân viên mà không giảm hiệu suất

Security / Permission:

Chỉ HR Admin có quyền tạo/sửa/xóa cơ cấu

Manager chỉ xem được cơ cấu phòng ban mình quản lý

Audit log / History:

Ghi log mọi thay đổi: Ai, Làm gì, Khi nào 

 

9. Business Rules
BR01: Tập đoàn là đơn vị to nhất. Lõi trung tâm

BR02: Tên đơn vị không được trùng trong cùng cấp cha

BR03: Không được xóa đơn vị đang có nhân viên hoặc đơn vị con

BR04: Mỗi nhân viên chỉ thuộc 1 phòng ban chính 

BR05: Người quản lý trực tiếp (line manager) phải thuộc cùng phòng ban hoặc cấp trên trực tiếp

BR06: Cấu trúc phải tuân thủ 5 cấp theo thứ tự: Tập đoàn → Khối, Công ty  → Phòng ban → Nhân sự

10. Validation & Error Handling
Trường hợp

Hành vi hệ thống

Tên đơn vị để trống

Hiển thị lỗi: "Tên đơn vị không được để trống"

Tên đơn vị trùng

Hiển thị lỗi: "Tên đơn vị đã tồn tại"

Xóa đơn vị có nhân viên

Chặn xóa, hiển thị: "Vui lòng chuyển nhân viên trước"

Không đủ quyền

Hiển thị: "Bạn không có quyền thực hiện thao tác này"

Lỗi hệ thống

Hiển thị: "Có lỗi xảy ra, vui lòng thử lại"

 

11. Definition of Done
Chỉ số đo lường thành công:

User Adoption: 100% HR Admin sử dụng hệ thống 

Data Completeness: 100% cơ cấu tổ chức được nhập đầy đủ vào hệ thống

Performance: Thời gian tra cứu, nắm rõ sơ đồ tổ chức có sự thay đổi giảm từ 10 phút xuống < 30 giây (giảm 95%)

Accuracy: Giảm 90% lỗi do dữ liệu không đồng bộ

Technical Completion Criteria:

Tất cả Acceptance Criteria (AC1-AC7) được pass

Unit test coverage >= 80%

Integration test hoàn thành cho các luồng chính

UAT (User Acceptance Testing) được HR Admin sign-off

Tài liệu hướng dẫn sử dụng hoàn thành

Performance test pass với 400 nhân viên