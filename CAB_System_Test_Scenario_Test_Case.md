# CAB System – Test Scenario & Test Case

**Nguồn xây dựng:** SRS và bài Test Case mẫu trong repository `23671571_TrinhMyLoan_CABSYSTEM`.

**Quy ước:** Mỗi Business Process là một Test Scenario lớn. Mỗi Test Scenario có **20 Test Case** và bao phủ tối thiểu 5 nhóm: **Positive, Negative, Boundary, Empty, Invalid Format/Type**.

## 1. Danh sách Test Scenario

| ID | Test Scenario | Số Test Case |
|---|---|---:|
| BP-01 | User & Driver Management | 20 |
| BP-02 | Ride Booking Process | 20 |
| BP-03 | Driver Matching & Assignment Process | 20 |
| BP-04 | Trip Execution Process | 20 |
| BP-05 | Fare Calculation & Payment Process | 20 |
| BP-06 | Notification Process | 20 |
| BP-07 | Operation Management Process | 20 |

## 2. Chi tiết Test Case

## BP-01 – User & Driver Management

| Test Case ID | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|---|
| TC-BP-01-001 | Positive | Customer đăng ký tài khoản hợp lệ | Customer chưa có tài khoản | Nhập đầy đủ thông tin → Đăng ký | Tên, SĐT, email, password hợp lệ | Tạo tài khoản thành công | Medium |
| TC-BP-01-002 | Positive | Customer đăng nhập hợp lệ | Tài khoản Active | Nhập thông tin đúng → Login | Tài khoản hợp lệ | Đăng nhập và cấp phiên/token | Medium |
| TC-BP-01-003 | Positive | Driver đăng nhập hợp lệ | Driver Active | Nhập thông tin đúng → Login | Driver hợp lệ | Đăng nhập đúng vai trò Driver | Medium |
| TC-BP-01-004 | Positive | Người dùng xem hồ sơ | Đã đăng nhập | Mở hồ sơ | Token hợp lệ | Hiển thị đúng thông tin | Medium |
| TC-BP-01-005 | Positive | Người dùng cập nhật hồ sơ hợp lệ | Đã đăng nhập | Sửa thông tin → Lưu | Thông tin hợp lệ | Cập nhật thành công | Medium |
| TC-BP-01-006 | Positive | Operator tạo tài khoản Driver | Operator đã đăng nhập | Mở tạo Driver → nhập dữ liệu → Lưu | Driver mới hợp lệ | Tạo Driver thành công | Medium |
| TC-BP-01-007 | Positive | Driver cập nhật phương tiện | Driver đã đăng nhập | Sửa thông tin xe → Lưu | Biển số/model hợp lệ | Cập nhật phương tiện | Medium |
| TC-BP-01-008 | Positive | Driver chuyển trạng thái sẵn sàng | Driver đủ điều kiện | Chọn trạng thái AVAILABLE | AVAILABLE | Trạng thái được cập nhật | Medium |
| TC-BP-01-009 | Negative | Đăng ký email đã tồn tại | Email đã dùng | Đăng ký với email trùng | existing@example.com | Từ chối và báo trùng email | High |
| TC-BP-01-010 | Negative | Đăng nhập sai mật khẩu | Tài khoản tồn tại | Nhập sai password → Login | WrongPass | Không đăng nhập | High |
| TC-BP-01-011 | Negative | Tài khoản bị khóa đăng nhập | Status=LOCKED | Đăng nhập | Tài khoản LOCKED | Từ chối đăng nhập | High |
| TC-BP-01-012 | Negative | Customer truy cập chức năng Admin | Customer đã đăng nhập | Mở chức năng quản trị | Role=Customer | Từ chối quyền truy cập | High |
| TC-BP-01-013 | Boundary | Password đúng giới hạn tối thiểu | Rule password đã cấu hình | Đăng ký với password tại min | Giá trị tại min | Xử lý đúng rule | Medium |
| TC-BP-01-014 | Boundary | Driver vừa kết thúc chuyến chuyển AVAILABLE | Driver không còn trip active | Cập nhật trạng thái | AVAILABLE | Cho phép nhận chuyến mới | Medium |
| TC-BP-01-015 | Empty | Bỏ trống số điện thoại khi đăng ký | Mở form đăng ký | Để SĐT rỗng → Đăng ký | phone=empty | Báo trường bắt buộc | High |
| TC-BP-01-016 | Empty | Bỏ trống mật khẩu khi đăng nhập | Mở Login | Nhập tài khoản, bỏ password | password=empty | Không đăng nhập | High |
| TC-BP-01-017 | Invalid Format/Type | Email sai định dạng | Mở đăng ký | Nhập email sai → Đăng ký | user@@example | Báo email không hợp lệ | High |
| TC-BP-01-018 | Invalid Format/Type | SĐT chứa ký tự không hợp lệ | Mở đăng ký | Nhập SĐT sai | 09abc123 | Từ chối dữ liệu | High |
| TC-BP-01-019 | Invalid Format/Type | Trạng thái Driver ngoài danh mục | Driver đã đăng nhập | Cập nhật status | UNKNOWN | Từ chối trạng thái | High |
| TC-BP-01-020 | Invalid Format/Type | Token sai định dạng | Có token không hợp lệ | Gọi chức năng hồ sơ | Bearer abc | Từ chối xác thực | High |

## BP-02 – Ride Booking Process

| Test Case ID | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|---|
| TC-BP-02-001 | Positive | Tạo Booking với thông tin hợp lệ | Customer đã đăng nhập | Nhập điểm đón/đến → chọn loại xe → Đặt xe | Pickup, destination, vehicle type hợp lệ | Tạo Booking và mã định danh | Medium |
| TC-BP-02-002 | Positive | Chọn loại xe hợp lệ | Customer đang tạo Booking | Chọn loại xe | 4_SEATS | Lưu lựa chọn | Medium |
| TC-BP-02-003 | Positive | Xem trạng thái Booking | Booking đã tạo | Mở chi tiết Booking | booking_id hợp lệ | Hiển thị đúng trạng thái | Medium |
| TC-BP-02-004 | Positive | Hủy Booking khi được phép | Booking ở trạng thái cho phép hủy | Chọn Hủy → xác nhận | booking_id hợp lệ | Booking chuyển CANCELLED | Medium |
| TC-BP-02-005 | Positive | Xem lại thông tin trước xác nhận | Đã nhập đủ dữ liệu | Mở bước xác nhận | Dữ liệu hợp lệ | Hiển thị đúng thông tin | Medium |
| TC-BP-02-006 | Positive | Tạo Booking mới sau chuyến hoàn tất | Không còn chuyến active | Tạo Booking mới | Dữ liệu hợp lệ | Tạo thành công | Medium |
| TC-BP-02-007 | Negative | Tạo Booking khi có chuyến active | Customer có chuyến chưa xong | Tạo Booking mới | Dữ liệu hợp lệ | Từ chối tạo Booking | High |
| TC-BP-02-008 | Negative | Điểm đón và điểm đến trùng nhau | Customer đã đăng nhập | Nhập cùng vị trí → Đặt xe | Pickup=Destination | Từ chối hoặc yêu cầu sửa | High |
| TC-BP-02-009 | Negative | Loại xe không tồn tại | Customer đã đăng nhập | Tạo Booking | vehicleType=INVALID | Không tạo Booking | High |
| TC-BP-02-010 | Negative | Customer khác xem Booking | Booking thuộc Customer B | Customer A mở Booking B | booking_id B | Từ chối quyền | High |
| TC-BP-02-011 | Boundary | Booking với dữ liệu địa điểm tại giới hạn hợp lệ | Rule dữ liệu đã cấu hình | Nhập dữ liệu tại biên → Đặt xe | Giá trị biên | Xử lý đúng rule | Medium |
| TC-BP-02-012 | Boundary | Tạo Booking ngay sau khi chuyến cũ kết thúc | Chuyến cũ vừa Completed | Đặt chuyến mới | Dữ liệu hợp lệ | Cho phép tạo | Medium |
| TC-BP-02-013 | Boundary | Danh sách loại xe chỉ có 1 loại | Hệ thống có 1 loại xe | Mở danh sách | 1 vehicle type | Hiển thị đúng 1 lựa chọn | Medium |
| TC-BP-02-014 | Empty | Bỏ trống điểm đón | Mở đặt xe | Để pickup rỗng → Đặt xe | pickup=empty | Không tạo Booking | High |
| TC-BP-02-015 | Empty | Bỏ trống điểm đến | Mở đặt xe | Để destination rỗng → Đặt xe | destination=empty | Không tạo Booking | High |
| TC-BP-02-016 | Empty | Bỏ trống loại xe | Mở đặt xe | Không chọn loại xe → Đặt xe | vehicleType=empty | Không tạo Booking | High |
| TC-BP-02-017 | Invalid Format/Type | Tọa độ điểm đón sai kiểu | Customer đã đăng nhập | Gửi Booking | latitude=abc | Validation error | High |
| TC-BP-02-018 | Invalid Format/Type | vehicleType sai kiểu | Customer đã đăng nhập | Gửi Booking | vehicleType=[] | Validation error | High |
| TC-BP-02-019 | Invalid Format/Type | booking_id không tồn tại | Customer đã đăng nhập | Mở Booking | BOOK999 | Báo không tìm thấy | High |
| TC-BP-02-020 | Invalid Format/Type | Request Booking sai schema | Customer đã đăng nhập | Gửi request sai cấu trúc | body sai schema | API từ chối | High |

## BP-03 – Driver Matching & Assignment Process

| Test Case ID | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|---|
| TC-BP-03-001 | Positive | Tìm danh sách Driver sẵn sàng | Booking hợp lệ | Khởi chạy tìm Driver | Booking hợp lệ | Chỉ lấy Driver đủ điều kiện | Medium |
| TC-BP-03-002 | Positive | Ưu tiên Driver theo vị trí/tiêu chí | Có nhiều Driver phù hợp | Thực hiện matching | Nhiều Driver AVAILABLE | Chọn theo tiêu chí vận hành | Medium |
| TC-BP-03-003 | Positive | Gửi yêu cầu chuyến đến Driver | Có Driver phù hợp | Gửi offer | Driver hợp lệ | Driver nhận yêu cầu | Medium |
| TC-BP-03-004 | Positive | Driver Accept yêu cầu | Offer còn hiệu lực | Driver chọn Accept | ACCEPT | Phân công Driver | Medium |
| TC-BP-03-005 | Positive | Driver Reject yêu cầu | Offer còn hiệu lực | Driver chọn Reject | REJECT | Tiếp tục tìm Driver khác | Medium |
| TC-BP-03-006 | Positive | Driver không phản hồi | Offer hết thời gian | Chờ hết timeout | No response | Tiếp tục tìm Driver khác | Medium |
| TC-BP-03-007 | Positive | Thông báo Customer khi đã gán Driver | Driver đã Accept | Kiểm tra Booking | Assigned Driver | Customer thấy Driver được gán | Medium |
| TC-BP-03-008 | Negative | Không chọn Driver OFFLINE | Có Driver OFFLINE | Thực hiện matching | status=OFFLINE | Bỏ qua Driver | High |
| TC-BP-03-009 | Negative | Không chọn Driver BUSY | Driver có trip active | Thực hiện matching | status=BUSY | Bỏ qua Driver | High |
| TC-BP-03-010 | Negative | Không chọn Driver sai loại xe | Booking yêu cầu loại khác | Thực hiện matching | Vehicle mismatch | Không phân công | High |
| TC-BP-03-011 | Negative | Accept Booking đã bị hủy | Booking=CANCELLED | Driver Accept | ACCEPT | Từ chối phân công | High |
| TC-BP-03-012 | Negative | Driver khác phản hồi offer | Offer thuộc Driver A | Driver B phản hồi | offerId của A | Từ chối quyền | High |
| TC-BP-03-013 | Boundary | Chỉ có đúng 1 Driver phù hợp | Có 1 Driver hợp lệ | Matching | 1 Driver | Trả đúng Driver đó | Medium |
| TC-BP-03-014 | Boundary | Không có Driver phù hợp | 0 Driver hợp lệ | Matching | 0 Driver | Thông báo không tìm được Driver | Medium |
| TC-BP-03-015 | Empty | Booking ID rỗng khi matching | Customer đã tạo dữ liệu không đầy đủ | Gọi matching | bookingId=empty | Từ chối | High |
| TC-BP-03-016 | Empty | Driver ID rỗng khi phân công | Offer đang xử lý | Gửi assignment | driverId=empty | Không phân công | High |
| TC-BP-03-017 | Invalid Format/Type | Driver ID không tồn tại | Booking hợp lệ | Phân công Driver | DRV999 | Báo không tìm thấy | High |
| TC-BP-03-018 | Invalid Format/Type | Phản hồi ngoài Accept/Reject | Offer hợp lệ | Gửi response | MAYBE | Từ chối | High |
| TC-BP-03-019 | Invalid Format/Type | Vị trí Driver sai kiểu | Driver đang AVAILABLE | Cập nhật vị trí | lat=abc | Từ chối dữ liệu | High |
| TC-BP-03-020 | Invalid Format/Type | Offer ID sai định dạng | Driver đã đăng nhập | Phản hồi offer | @@@ | Từ chối/không tìm thấy | High |

## BP-04 – Trip Execution Process

| Test Case ID | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|---|
| TC-BP-04-001 | Positive | Tạo Trip sau khi Driver được phân công | Booking có Assigned Driver | Hệ thống tạo Trip | Booking hợp lệ | Trip được tạo và liên kết đúng | High |
| TC-BP-04-002 | Positive | Customer xem trạng thái Trip | Trip thuộc Customer | Mở Trip | trip_id hợp lệ | Hiển thị đúng trạng thái | Medium |
| TC-BP-04-003 | Positive | Driver cập nhật đã đến điểm đón | Trip đúng giai đoạn | Cập nhật trạng thái | ARRIVED | Chuyển trạng thái hợp lệ | Medium |
| TC-BP-04-004 | Positive | Driver cập nhật đã đón khách | Driver đã đến | Cập nhật trạng thái | PICKED_UP | Chuyển trạng thái hợp lệ | Medium |
| TC-BP-04-005 | Positive | Driver bắt đầu chuyến | Đã đón khách | Cập nhật trạng thái | IN_PROGRESS | Trip bắt đầu | Medium |
| TC-BP-04-006 | Positive | Driver hoàn thành chuyến | Trip đang thực hiện | Cập nhật trạng thái | COMPLETED | Trip hoàn thành | High |
| TC-BP-04-007 | Positive | Lưu thời gian sự kiện Trip | Trip thay đổi trạng thái | Cập nhật trạng thái | timestamp | Lưu thời gian tương ứng | Medium |
| TC-BP-04-008 | Positive | Lưu lịch sử Trip hoàn tất | Trip COMPLETED | Mở lịch sử | trip_id | Trip xuất hiện trong lịch sử | Medium |
| TC-BP-04-009 | Negative | Nhảy trạng thái không hợp lệ | Trip mới bắt đầu | Chuyển thẳng COMPLETED | COMPLETED | Từ chối chuyển trạng thái | High |
| TC-BP-04-010 | Negative | Driver khác cập nhật Trip | Trip thuộc Driver A | Driver B cập nhật | trip_id A | Từ chối quyền | High |
| TC-BP-04-011 | Negative | Customer cập nhật trạng thái Driver | Customer đã đăng nhập | Gọi cập nhật Trip | IN_PROGRESS | Từ chối quyền | High |
| TC-BP-04-012 | Negative | Cập nhật Trip đã COMPLETED | Trip đã hoàn tất | Đổi trạng thái | IN_PROGRESS | Không cho quay lại | High |
| TC-BP-04-013 | Boundary | Trip vừa được tạo | Driver vừa được gán | Xem Trip | Trạng thái đầu | Hiển thị trạng thái khởi tạo đúng | Medium |
| TC-BP-04-014 | Boundary | Chuyển bước cuối sang COMPLETED | Trip ở trạng thái trước COMPLETED | Cập nhật | COMPLETED | Chấp nhận đúng lifecycle | Medium |
| TC-BP-04-015 | Empty | status rỗng | Driver sở hữu Trip | Cập nhật status | empty | Từ chối | High |
| TC-BP-04-016 | Empty | trip_id rỗng | Driver đã đăng nhập | Gọi cập nhật | tripId=empty | Không xử lý | High |
| TC-BP-04-017 | Invalid Format/Type | status ngoài lifecycle | Trip hợp lệ | Cập nhật | RUNNING_UNKNOWN | Từ chối | High |
| TC-BP-04-018 | Invalid Format/Type | status là số | Trip hợp lệ | Cập nhật | status=1 | Validation error | High |
| TC-BP-04-019 | Invalid Format/Type | trip_id không tồn tại | Đã đăng nhập | Xem/cập nhật Trip | TRIP999 | Báo không tìm thấy | High |
| TC-BP-04-020 | Invalid Format/Type | timestamp sai định dạng | Trip hợp lệ | Gửi sự kiện | time=abc | Từ chối dữ liệu | High |

## BP-05 – Fare Calculation & Payment Process

| Test Case ID | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|---|
| TC-BP-05-001 | Positive | Tính cước sau khi Trip hoàn thành | Trip COMPLETED | Thực hiện tính cước | Trip hợp lệ | Tính và lưu fare | High |
| TC-BP-05-002 | Positive | Hiển thị cước cho Customer | Fare đã tính | Mở chi tiết | trip_id | Hiển thị đúng cước | Medium |
| TC-BP-05-003 | Positive | Chọn thanh toán CASH | Trip có fare | Chọn CASH | CASH | Chấp nhận phương thức | High |
| TC-BP-05-004 | Positive | Thanh toán tiền mặt thành công | Trip COMPLETED | Xác nhận thanh toán | CASH | Payment thành công | High |
| TC-BP-05-005 | Positive | Chọn thanh toán điện tử | Trip có fare | Chọn electronic | ELECTRONIC | Gửi yêu cầu thanh toán | High |
| TC-BP-05-006 | Positive | Nhận kết quả thanh toán điện tử thành công | Provider trả success | Nhận callback/kết quả | SUCCESS | Cập nhật Paid | High |
| TC-BP-05-007 | Positive | Thử lại thanh toán sau thất bại | Payment trước Failed | Chọn thử lại | ELECTRONIC | Cho phép retry | High |
| TC-BP-05-008 | Negative | Thanh toán khi Trip chưa hoàn thành | Trip IN_PROGRESS | Thanh toán | CASH | Từ chối | High |
| TC-BP-05-009 | Negative | Customer khác thanh toán Trip | Trip thuộc người khác | Gửi payment | trip_id khác | Từ chối quyền | High |
| TC-BP-05-010 | Negative | Payment Provider trả thất bại | Đã gửi payment | Nhận kết quả | FAILED | Cập nhật Failed | High |
| TC-BP-05-011 | Negative | Phương thức không hỗ trợ | Trip hợp lệ | Thanh toán | CRYPTO | Từ chối | High |
| TC-BP-05-012 | Negative | Tính cước khi thiếu dữ liệu Trip | Trip thiếu dữ liệu cần thiết | Tính fare | Dữ liệu thiếu | Không tính sai cước | High |
| TC-BP-05-013 | Boundary | Tính cước ngay sau COMPLETED | Trip vừa hoàn tất | Tính fare | COMPLETED | Tính đúng thời điểm | Medium |
| TC-BP-05-014 | Boundary | Retry payment sau một lần Failed | Có payment Failed | Retry | Lần thử 2 | Xử lý nhất quán | Medium |
| TC-BP-05-015 | Empty | payment method rỗng | Trip COMPLETED | Thanh toán | method=empty | Từ chối | High |
| TC-BP-05-016 | Empty | trip_id rỗng | Customer đã đăng nhập | Thanh toán | tripId=empty | Không xử lý | High |
| TC-BP-05-017 | Invalid Format/Type | payment method sai kiểu | Trip COMPLETED | Gửi payment | method=1 | Validation error | High |
| TC-BP-05-018 | Invalid Format/Type | trip_id không tồn tại | Customer đã đăng nhập | Thanh toán | TRIP999 | Báo không tìm thấy | High |
| TC-BP-05-019 | Invalid Format/Type | Kết quả Provider sai format | Đang chờ kết quả | Nhận callback | status={} | Không cập nhật sai trạng thái | High |
| TC-BP-05-020 | Invalid Format/Type | Dữ liệu cước sai kiểu | Trip COMPLETED | Tính/lưu fare | distance=abc | Từ chối dữ liệu | High |

## BP-06 – Notification Process

| Test Case ID | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|---|
| TC-BP-06-001 | Positive | Thông báo khi Booking được tạo | Booking vừa tạo | Kiểm tra notification | BOOKING_CREATED | Gửi thông báo phù hợp | Medium |
| TC-BP-06-002 | Positive | Thông báo Driver khi có yêu cầu chuyến | Có offer mới | Kiểm tra Driver | TRIP_OFFER | Driver nhận thông báo | Medium |
| TC-BP-06-003 | Positive | Thông báo Customer khi Driver Accept | Driver vừa Accept | Kiểm tra Customer | DRIVER_ASSIGNED | Customer nhận thông báo | Medium |
| TC-BP-06-004 | Positive | Thông báo khi trạng thái Trip thay đổi | Trip đổi trạng thái | Kiểm tra notification | TRIP_STATUS_CHANGED | Gửi đúng sự kiện | Medium |
| TC-BP-06-005 | Positive | Thông báo kết quả thanh toán | Payment có kết quả | Kiểm tra notification | PAYMENT_RESULT | Customer nhận kết quả | High |
| TC-BP-06-006 | Positive | Thông báo khi không tìm được Driver | Matching thất bại | Kiểm tra Customer | NO_DRIVER | Customer được thông báo | Medium |
| TC-BP-06-007 | Positive | Lưu thông báo để người dùng xem | Có business event | Mở danh sách thông báo | Event hợp lệ | Hiển thị thông báo | Medium |
| TC-BP-06-008 | Negative | Không gửi thông báo sai người nhận | Event thuộc Customer A | Kiểm tra Customer B | recipient B | B không nhận dữ liệu A | High |
| TC-BP-06-009 | Negative | Không tạo trùng thông báo cho cùng event | Event đã xử lý | Xử lý lại cùng event | same event id | Không tạo bản ghi trùng không cần thiết | High |
| TC-BP-06-010 | Negative | Không gửi nội dung của Trip khác | Có nhiều Trip | Phát notification | trip khác | Nội dung đúng Trip | High |
| TC-BP-06-011 | Boundary | Người dùng chưa có thông báo | 0 notification | Mở danh sách | 0 item | Hiển thị danh sách rỗng | Medium |
| TC-BP-06-012 | Boundary | Chỉ có 1 thông báo | 1 notification | Mở danh sách | 1 item | Hiển thị đúng 1 thông báo | Medium |
| TC-BP-06-013 | Boundary | Nhiều sự kiện liên tiếp | Nhiều event hợp lệ | Phát notification | N events | Ghi nhận đầy đủ, đúng thứ tự hợp lý | Medium |
| TC-BP-06-014 | Empty | recipient rỗng | Có event | Tạo notification | recipient=empty | Không gửi | High |
| TC-BP-06-015 | Empty | event type rỗng | Có recipient | Tạo notification | eventType=empty | Từ chối | High |
| TC-BP-06-016 | Empty | message rỗng | Có event | Tạo notification | message=empty | Xử lý theo rule, không phát nội dung vô nghĩa | High |
| TC-BP-06-017 | Invalid Format/Type | recipient ID sai định dạng | Có event | Tạo notification | recipient=@@@ | Từ chối | High |
| TC-BP-06-018 | Invalid Format/Type | event type ngoài danh mục | Có recipient | Tạo notification | UNKNOWN_EVENT | Từ chối | High |
| TC-BP-06-019 | Invalid Format/Type | payload sai kiểu | Có event | Tạo notification | payload=[] | Validation error | High |
| TC-BP-06-020 | Invalid Format/Type | ID thông báo không tồn tại | User đã đăng nhập | Mở notification | NOTI999 | Báo không tìm thấy | High |

## BP-07 – Operation Management Process

| Test Case ID | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|---|
| TC-BP-07-001 | Positive | Operator xem dữ liệu vận hành | Operator đã đăng nhập | Mở dashboard vận hành | Token Operator | Hiển thị dữ liệu được phép | Medium |
| TC-BP-07-002 | Positive | Operator xem danh sách Booking | Operator đã đăng nhập | Mở Booking management | Dữ liệu hệ thống | Hiển thị danh sách | Medium |
| TC-BP-07-003 | Positive | Operator xem danh sách Trip | Operator đã đăng nhập | Mở Trip management | Dữ liệu hệ thống | Hiển thị danh sách | Medium |
| TC-BP-07-004 | Positive | Operator xem trạng thái Driver | Operator đã đăng nhập | Mở Driver management | Driver data | Hiển thị trạng thái | Medium |
| TC-BP-07-005 | Positive | Administrator quản lý tài khoản | Admin đã đăng nhập | Mở account management | User hợp lệ | Thực hiện chức năng được phân quyền | Medium |
| TC-BP-07-006 | Positive | Tìm kiếm dữ liệu vận hành hợp lệ | Operator đã đăng nhập | Nhập điều kiện → Tìm | ID/status hợp lệ | Trả kết quả phù hợp | Medium |
| TC-BP-07-007 | Positive | Xem chi tiết bản ghi vận hành | Có bản ghi | Mở chi tiết | ID hợp lệ | Hiển thị đúng dữ liệu | Medium |
| TC-BP-07-008 | Negative | Customer truy cập Operation Management | Customer đã login | Mở trang vận hành | Role Customer | Từ chối quyền | High |
| TC-BP-07-009 | Negative | Driver truy cập chức năng Admin | Driver đã login | Mở admin function | Role Driver | Từ chối quyền | High |
| TC-BP-07-010 | Negative | Operator sửa dữ liệu ngoài quyền | Operator đã login | Thực hiện action không được cấp | Restricted action | Từ chối | High |
| TC-BP-07-011 | Negative | Thao tác với tài khoản không tồn tại | Admin đã login | Mở/cập nhật user | USER999 | Báo không tìm thấy | High |
| TC-BP-07-012 | Negative | Thao tác khi phiên hết hạn | Operator token expired | Mở dashboard | Expired token | Yêu cầu xác thực lại | High |
| TC-BP-07-013 | Boundary | Hệ thống chưa có Booking | 0 Booking | Mở danh sách | 0 item | Hiển thị danh sách rỗng | Medium |
| TC-BP-07-014 | Boundary | Chỉ có 1 bản ghi | Có 1 record | Mở danh sách | 1 item | Hiển thị đúng 1 record | Medium |
| TC-BP-07-015 | Empty | Tìm kiếm với từ khóa rỗng | Operator đã login | Để keyword rỗng → Tìm | keyword=empty | Hiển thị mặc định/validation theo thiết kế | High |
| TC-BP-07-016 | Empty | Thiếu token truy cập vận hành | Chưa xác thực | Mở dashboard | Authorization=empty | Từ chối | High |
| TC-BP-07-017 | Invalid Format/Type | ID Booking sai format | Operator đã login | Tìm Booking | @@@ | Từ chối/không tìm thấy | High |
| TC-BP-07-018 | Invalid Format/Type | Status filter sai giá trị | Operator đã login | Lọc dữ liệu | status=UNKNOWN | Từ chối hoặc không trả dữ liệu sai | High |
| TC-BP-07-019 | Invalid Format/Type | Role gửi lên sai kiểu | Admin đã login | Cập nhật quyền | role=[] | Validation error | High |
| TC-BP-07-020 | Invalid Format/Type | Tham số phân trang sai kiểu | Operator đã login | Mở danh sách | page=abc | Validation error | High |

## 3. Tổng hợp

- **07 Test Scenario** theo 07 Business Process trong SRS.
- **20 Test Case/Test Scenario**.
- **Tổng cộng: 140 Test Case**.
- Mỗi Test Scenario có đủ 5 nhóm: **Positive, Negative, Boundary, Empty, Invalid Format/Type**.
- Các giá trị biên không được SRS quy định cụ thể được mô tả theo **rule đã cấu hình** thay vì tự đặt giới hạn mới.