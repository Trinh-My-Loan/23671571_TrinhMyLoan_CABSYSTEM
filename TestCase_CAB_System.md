# CAB System – Test Scenario & Test Case



## 1. Traceability Test Scenario

| Test Scenario | Business Requirement | Functional Requirements | Acceptance Criteria | API liên quan | Số TC |
|---|---|---|---|---|---:|
| BP-01 | BR-01 | FR-01.01–FR-01.05 | AC-01.01–AC-01.05 | 01–05 | 20 |
| BP-02 | BR-02 | FR-02.01–FR-02.05 | AC-02.01–AC-02.05 | 04–08 | 20 |
| BP-03 | BR-03 | FR-03.01–FR-03.04 | AC-03.01–AC-03.04 | 10 | 20 |
| BP-04 | BR-04 | FR-04.01–FR-04.02 | AC-04.01–AC-04.02 | 09, 10 | 20 |
| BP-05 | BR-05 | FR-05.01–FR-05.03 | AC-05.01–AC-05.03 | 06, 11 | 20 |
| BP-06 | BR-06 | FR-06.01–FR-06.04 | AC-06.01–AC-06.04 | 11, 12 | 20 |
| BP-07 | BR-07 | FR-07.01–FR-07.05 | AC-07.01–AC-07.05 | 12–14 | 20 |
| BP-08 | BR-08 | FR-08.01–FR-08.05 | AC-08.01–AC-08.05 | 15, 16 | 20 |
| BP-09 | BR-09 | FR-09.01–FR-09.03 | AC-09.01–AC-09.03 | 16, 17 | 20 |



## 2. Chi tiết Test Case

## BP-01 – Customer Account Management

**Traceability:** FR-01.01–FR-01.05 → AC-01.01–AC-01.05

| Test Case ID | Test Scenario | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority | API Source |
|---|---|---|---|---|---|---|---|---|---|
| TC-BP01-001 | BP-01 – Customer Account Management | Positive | Đăng ký Customer hợp lệ | Chưa có username tương ứng | 1. Gửi POST đăng ký với đủ trường bắt buộc | username=loan123; password=Password@123; full_name=Trinh My Loan; phone=0901234567; email=loan@example.com | HTTP 201; success=true; trả user_id, username, role=Customer, status=ACTIVE | High | 01-register-customer.yaml |
| TC-BP01-002 | BP-01 – Customer Account Management | Positive | Đăng nhập đúng tài khoản Customer | Customer đã tồn tại | 1. POST login với username/password đúng | loan123 / Password@123 | HTTP 200; trả access_token, token_type=Bearer và role | High | 02-login.yaml |
| TC-BP01-003 | BP-01 – Customer Account Management | Positive | Đăng xuất với token hợp lệ | Đã đăng nhập | 1. POST logout kèm Bearer token | Bearer token hợp lệ | HTTP 200; message=Logout successful | High | 03-logout.yaml |
| TC-BP01-004 | BP-01 – Customer Account Management | Positive | Customer xem đúng hồ sơ của mình | Customer đã đăng nhập | 1. GET /users/me | Bearer token Customer | HTTP 200; trả user_id, full_name, phone, email, role | High | 04-get-profile.yaml |
| TC-BP01-005 | BP-01 – Customer Account Management | Positive | Customer cập nhật hồ sơ hợp lệ | Customer đã đăng nhập | 1. PUT /users/me với dữ liệu mới | full_name, phone, email hợp lệ | HTTP 200; message=Profile updated successfully | High | 05-update-profile.yaml |
| TC-BP01-006 | BP-01 – Customer Account Management | Negative | Đăng nhập sai mật khẩu | Tài khoản tồn tại | 1. POST login với password sai | loan123 / Wrong123 | HTTP 401; không cấp token | High | 02-login.yaml |
| TC-BP01-007 | BP-01 – Customer Account Management | Negative | Xem hồ sơ với token không hợp lệ | Có token sai | 1. GET /users/me | Bearer abc | HTTP 401 | High | 04-get-profile.yaml |
| TC-BP01-008 | BP-01 – Customer Account Management | Negative | Cập nhật hồ sơ khi chưa xác thực | Không có token | 1. PUT /users/me | full_name hợp lệ | HTTP 401 | High | 05-update-profile.yaml |
| TC-BP01-009 | BP-01 – Customer Account Management | Boundary | Đăng nhập ngay sau khi đăng ký | Vừa nhận HTTP 201 từ register | 1. Register<br>2. Login bằng credential vừa tạo | Credential vừa tạo | Login HTTP 200 | Medium | 01-register-customer.yaml + 02-login.yaml |
| TC-BP01-010 | BP-01 – Customer Account Management | Boundary | Đăng xuất ngay sau đăng nhập | Vừa login thành công | 1. Login<br>2. Logout | Token mới cấp | Logout HTTP 200 | Medium | 02-login.yaml + 03-logout.yaml |
| TC-BP01-011 | BP-01 – Customer Account Management | Boundary | Chỉ cập nhật full_name | Customer đã login | 1. PUT profile chỉ có full_name | full_name=Loan Nguyen | HTTP 200; cập nhật thành công | Medium | 05-update-profile.yaml |
| TC-BP01-012 | BP-01 – Customer Account Management | Boundary | Chỉ cập nhật email | Customer đã login | 1. PUT profile chỉ có email | email=new@example.com | HTTP 200; cập nhật thành công | Medium | 05-update-profile.yaml |
| TC-BP01-013 | BP-01 – Customer Account Management | Empty | Thiếu username khi đăng ký | Chưa đăng ký | 1. POST register thiếu username | password/full_name/phone/email có đủ | HTTP 400 | High | 01-register-customer.yaml |
| TC-BP01-014 | BP-01 – Customer Account Management | Empty | Thiếu password khi đăng ký | Chưa đăng ký | 1. POST register thiếu password | username/full_name/phone/email có đủ | HTTP 400 | High | 01-register-customer.yaml |
| TC-BP01-015 | BP-01 – Customer Account Management | Empty | Thiếu full_name khi đăng ký | Chưa đăng ký | 1. POST register thiếu full_name | Các field khác hợp lệ | HTTP 400 | High | 01-register-customer.yaml |
| TC-BP01-016 | BP-01 – Customer Account Management | Empty | Không gửi token khi xem hồ sơ | Chưa xác thực | 1. GET /users/me không Authorization | Không token | HTTP 401 | High | 04-get-profile.yaml |
| TC-BP01-017 | BP-01 – Customer Account Management | Invalid Format/Type | Email đăng ký sai định dạng | Chưa đăng ký | 1. POST register | email=abc | HTTP 400 | High | 01-register-customer.yaml |
| TC-BP01-018 | BP-01 – Customer Account Management | Invalid Format/Type | Body đăng nhập thiếu schema yêu cầu | API hoạt động | 1. POST login body rỗng | {} | HTTP 400 | High | 02-login.yaml |
| TC-BP01-019 | BP-01 – Customer Account Management | Invalid Format/Type | Token sai định dạng khi logout | Có chuỗi token malformed | 1. POST logout | Bearer abc | HTTP 401 | High | 03-logout.yaml |
| TC-BP01-020 | BP-01 – Customer Account Management | Invalid Format/Type | Email cập nhật sai định dạng | Customer đã login | 1. PUT profile | email=abc | HTTP 400 | High | 05-update-profile.yaml |

## BP-02 – Driver Management

**Traceability:** FR-02.01–FR-02.05 → AC-02.01–AC-02.05

| Test Case ID | Test Scenario | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority | API Source |
|---|---|---|---|---|---|---|---|---|---|
| TC-BP02-001 | BP-02 – Driver Management | Positive | Driver xem hồ sơ của mình | Driver đã login | 1. GET /users/me | Token Driver | HTTP 200; trả đúng hồ sơ Driver | High | 04-get-profile.yaml |
| TC-BP02-002 | BP-02 – Driver Management | Positive | Driver cập nhật hồ sơ hợp lệ | Driver đã login | 1. PUT /users/me | full_name/phone/email hợp lệ | HTTP 200 | Medium | 05-update-profile.yaml |
| TC-BP02-003 | BP-02 – Driver Management | Positive | Driver OFFLINE → ONLINE | Driver đang OFFLINE | 1. PATCH status | status=ONLINE | HTTP 200; status=ONLINE | High | 06-update-driver-status.yaml |
| TC-BP02-004 | BP-02 – Driver Management | Positive | Driver ONLINE → AVAILABLE | Driver đang ONLINE | 1. PATCH status | status=AVAILABLE | HTTP 200; status=AVAILABLE | High | 06-update-driver-status.yaml |
| TC-BP02-005 | BP-02 – Driver Management | Positive | Driver cập nhật vị trí hợp lệ | Driver đã login | 1. PUT location | latitude=10.822; longitude=106.687 | HTTP 200; location updated | High | 07-update-driver-location.yaml |
| TC-BP02-006 | BP-02 – Driver Management | Positive | Driver xem phương tiện của mình | Driver có Vehicle | 1. GET vehicles | Token Driver | HTTP 200; trả vehicles của Driver | High | 08-get-driver-vehicles.yaml |
| TC-BP02-007 | BP-02 – Driver Management | Negative | Customer cập nhật Driver status | Customer đã login | 1. PATCH driver status | status=AVAILABLE | HTTP 403 | High | 06-update-driver-status.yaml |
| TC-BP02-008 | BP-02 – Driver Management | Negative | Customer cập nhật Driver location | Customer đã login | 1. PUT driver location | latitude/longitude hợp lệ | HTTP 403 | High | 07-update-driver-location.yaml |
| TC-BP02-009 | BP-02 – Driver Management | Boundary | Driver AVAILABLE → BUSY | Driver AVAILABLE và bắt đầu Trip | 1. PATCH status | status=BUSY | HTTP 200 nếu chuyển trạng thái hợp lệ theo RULE | Medium | 06-update-driver-status.yaml |
| TC-BP02-010 | BP-02 – Driver Management | Boundary | Driver BUSY → AVAILABLE | Trip đã hoàn tất | 1. PATCH status | status=AVAILABLE | HTTP 200 nếu chuyển trạng thái hợp lệ | Medium | 06-update-driver-status.yaml |
| TC-BP02-011 | BP-02 – Driver Management | Boundary | Driver chưa có Vehicle | Driver hợp lệ, không có vehicle | 1. GET vehicles | Token Driver | HTTP 200; vehicles=[] | Medium | 08-get-driver-vehicles.yaml |
| TC-BP02-012 | BP-02 – Driver Management | Boundary | Cập nhật lại cùng vị trí hiện tại | Driver đã login | 1. PUT cùng latitude/longitude | 10.822 / 106.687 | HTTP 200; dữ liệu nhất quán | Low | 07-update-driver-location.yaml |
| TC-BP02-013 | BP-02 – Driver Management | Empty | Status rỗng | Driver đã login | 1. PATCH status thiếu status | {} | HTTP 400 | High | 06-update-driver-status.yaml |
| TC-BP02-014 | BP-02 – Driver Management | Empty | Thiếu latitude | Driver đã login | 1. PUT location chỉ longitude | longitude=106.687 | HTTP 400 | High | 07-update-driver-location.yaml |
| TC-BP02-015 | BP-02 – Driver Management | Empty | Thiếu longitude | Driver đã login | 1. PUT location chỉ latitude | latitude=10.822 | HTTP 400 | High | 07-update-driver-location.yaml |
| TC-BP02-016 | BP-02 – Driver Management | Empty | Không token khi xem Vehicle | Chưa xác thực | 1. GET vehicles | Không token | HTTP 401 | High | 08-get-driver-vehicles.yaml |
| TC-BP02-017 | BP-02 – Driver Management | Invalid Format/Type | Status ngoài enum | Driver đã login | 1. PATCH status | status=READY | HTTP 400 | High | 06-update-driver-status.yaml |
| TC-BP02-018 | BP-02 – Driver Management | Invalid Format/Type | Latitude sai kiểu | Driver đã login | 1. PUT location | latitude=abc | HTTP 400 | High | 07-update-driver-location.yaml |
| TC-BP02-019 | BP-02 – Driver Management | Invalid Format/Type | Longitude sai kiểu | Driver đã login | 1. PUT location | longitude={} | HTTP 400 | High | 07-update-driver-location.yaml |
| TC-BP02-020 | BP-02 – Driver Management | Invalid Format/Type | Token malformed khi xem Vehicle | Driver chưa xác thực hợp lệ | 1. GET vehicles | Bearer abc | HTTP 401 | High | 08-get-driver-vehicles.yaml |

## BP-03 – Create Ride Request

**Traceability:** FR-03.01–FR-03.04 → AC-03.01–AC-03.04

| Test Case ID | Test Scenario | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority | API Source |
|---|---|---|---|---|---|---|---|---|---|
| TC-BP03-001 | BP-03 – Create Ride Request | Positive | Tạo Ride Request hợp lệ | Customer đã login và có Vehicle Type hợp lệ | 1. POST ride-requests | pickup_location=12 Nguyen Van Bao; destination=268 Ly Thuong Kiet; vehicle_type_id=1 | HTTP 201; trả request_id và status=CREATED | High | 10-create-ride-request.yaml |
| TC-BP03-002 | BP-03 – Create Ride Request | Positive | Hệ thống nhận điểm đón hợp lệ | Customer đã login | 1. POST request có pickup hợp lệ | pickup_location=Go Vap | Request được chấp nhận khi các field khác hợp lệ | High | 10-create-ride-request.yaml |
| TC-BP03-003 | BP-03 – Create Ride Request | Positive | Hệ thống nhận điểm đến hợp lệ | Customer đã login | 1. POST request có destination hợp lệ | destination=District 10 | Request được chấp nhận khi các field khác hợp lệ | High | 10-create-ride-request.yaml |
| TC-BP03-004 | BP-03 – Create Ride Request | Positive | Ride Request gắn Vehicle Type đã chọn | Customer đã chọn type | 1. POST request | vehicle_type_id=1 | HTTP 201; request được tạo theo type đã gửi | High | 10-create-ride-request.yaml |
| TC-BP03-005 | BP-03 – Create Ride Request | Negative | Tạo request khi chưa login | Không token | 1. POST ride-requests | Body hợp lệ | HTTP 401 | High | 10-create-ride-request.yaml |
| TC-BP03-006 | BP-03 – Create Ride Request | Negative | Driver dùng API tạo Ride Request | Driver đã login | 1. POST ride-requests | Token Driver + body hợp lệ | HTTP 403 theo phân quyền SRS | High | 10-create-ride-request.yaml |
| TC-BP03-007 | BP-03 – Create Ride Request | Negative | Vehicle Type không tồn tại | Customer đã login | 1. POST request | vehicle_type_id=999999 | Không tạo Ride Request; 400/404 theo API error contract | High | 10-create-ride-request.yaml |
| TC-BP03-008 | BP-03 – Create Ride Request | Negative | Dữ liệu yêu cầu không hợp lệ | Customer đã login | 1. POST request | Body không đạt validation | HTTP 400 | High | 10-create-ride-request.yaml |
| TC-BP03-009 | BP-03 – Create Ride Request | Boundary | Tạo request ngay sau login | Customer vừa login | 1. Login<br>2. POST ride-request | Body hợp lệ | HTTP 201 | Medium | 02-login.yaml + 10-create-ride-request.yaml |
| TC-BP03-010 | BP-03 – Create Ride Request | Boundary | Dùng Vehicle Type đầu tiên trong danh sách | Có ít nhất 1 type | 1. GET vehicle-types<br>2. POST request | vehicle_type_id của item đầu | HTTP 201 | Medium | 09-get-vehicle-types.yaml + 10-create-ride-request.yaml |
| TC-BP03-011 | BP-03 – Create Ride Request | Boundary | Tạo request mới sau Trip trước Completed | Không có Trip active | 1. POST request mới | Body hợp lệ | Hệ thống xử lý request mới bình thường | Medium | 10-create-ride-request.yaml |
| TC-BP03-012 | BP-03 – Create Ride Request | Boundary | Chuỗi địa điểm có khoảng trắng hợp lệ | Customer đã login | 1. POST request | pickup/destination là chuỗi địa chỉ đầy đủ | Không lỗi hệ thống; xử lý theo validation hiện hành | Low | 10-create-ride-request.yaml |
| TC-BP03-013 | BP-03 – Create Ride Request | Empty | Thiếu pickup_location | Customer đã login | 1. POST request | destination + vehicle_type_id | HTTP 400 | High | 10-create-ride-request.yaml |
| TC-BP03-014 | BP-03 – Create Ride Request | Empty | Thiếu destination | Customer đã login | 1. POST request | pickup + vehicle_type_id | HTTP 400 | High | 10-create-ride-request.yaml |
| TC-BP03-015 | BP-03 – Create Ride Request | Empty | Thiếu vehicle_type_id | Customer đã login | 1. POST request | pickup + destination | HTTP 400 | High | 10-create-ride-request.yaml |
| TC-BP03-016 | BP-03 – Create Ride Request | Empty | Body rỗng | Customer đã login | 1. POST request | {} | HTTP 400 | High | 10-create-ride-request.yaml |
| TC-BP03-017 | BP-03 – Create Ride Request | Invalid Format/Type | vehicle_type_id sai kiểu | Customer đã login | 1. POST request | vehicle_type_id=[] | HTTP 400 | High | 10-create-ride-request.yaml |
| TC-BP03-018 | BP-03 – Create Ride Request | Invalid Format/Type | pickup_location sai kiểu | Customer đã login | 1. POST request | pickup_location={} | HTTP 400 | High | 10-create-ride-request.yaml |
| TC-BP03-019 | BP-03 – Create Ride Request | Invalid Format/Type | destination sai kiểu | Customer đã login | 1. POST request | destination=[] | HTTP 400 | High | 10-create-ride-request.yaml |
| TC-BP03-020 | BP-03 – Create Ride Request | Invalid Format/Type | Token malformed | Customer chưa xác thực hợp lệ | 1. POST request | Bearer abc | HTTP 401 | High | 10-create-ride-request.yaml |

## BP-04 – Select Vehicle Type

**Traceability:** FR-04.01–FR-04.02 → AC-04.01–AC-04.02

| Test Case ID | Test Scenario | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority | API Source |
|---|---|---|---|---|---|---|---|---|---|
| TC-BP04-001 | BP-04 – Select Vehicle Type | Positive | Xem danh sách Vehicle Type | Hệ thống có Vehicle Type | 1. GET /vehicle-types | Không body | HTTP 200; trả vehicle_types | High | 09-get-vehicle-types.yaml |
| TC-BP04-002 | BP-04 – Select Vehicle Type | Positive | Danh sách trả đúng vehicle_type_id | Có dữ liệu | 1. GET vehicle-types | Không body | Mỗi item có vehicle_type_id | Medium | 09-get-vehicle-types.yaml |
| TC-BP04-003 | BP-04 – Select Vehicle Type | Positive | Danh sách trả đúng type_name | Có dữ liệu | 1. GET vehicle-types | Không body | Mỗi item có type_name | Medium | 09-get-vehicle-types.yaml |
| TC-BP04-004 | BP-04 – Select Vehicle Type | Positive | Chọn type hợp lệ khi tạo request | Customer login | 1. GET type<br>2. POST ride-request | vehicle_type_id hợp lệ | Request được tạo | High | 09-get-vehicle-types.yaml + 10-create-ride-request.yaml |
| TC-BP04-005 | BP-04 – Select Vehicle Type | Negative | Chọn type không tồn tại | Customer login | 1. POST ride-request | vehicle_type_id=999999 | Không tạo request | High | 10-create-ride-request.yaml |
| TC-BP04-006 | BP-04 – Select Vehicle Type | Negative | Không chọn type trước khi tạo request | Customer login | 1. POST ride-request thiếu type | Không vehicle_type_id | HTTP 400 | High | 10-create-ride-request.yaml |
| TC-BP04-007 | BP-04 – Select Vehicle Type | Negative | Type sai làm không thể xem đúng Driver phù hợp | RideRequest không hợp lệ | 1. Cố tiếp tục luồng | type không hợp lệ | Không tạo luồng chọn Driver hợp lệ | High | 10-create-ride-request.yaml |
| TC-BP04-008 | BP-04 – Select Vehicle Type | Negative | Request dùng type sai schema | Customer login | 1. POST request | vehicle_type_id={} | HTTP 400 | High | 10-create-ride-request.yaml |
| TC-BP04-009 | BP-04 – Select Vehicle Type | Boundary | Danh sách chỉ có 1 Vehicle Type | Dữ liệu có 1 item | 1. GET list | 1 item | HTTP 200; trả đúng 1 item | Medium | 09-get-vehicle-types.yaml |
| TC-BP04-010 | BP-04 – Select Vehicle Type | Boundary | Danh sách Vehicle Type rỗng | Không có type hỗ trợ | 1. GET list | 0 item | HTTP 200; vehicle_types=[] | Medium | 09-get-vehicle-types.yaml |
| TC-BP04-011 | BP-04 – Select Vehicle Type | Boundary | Lấy danh sách nhiều lần | API hoạt động | 1. GET list hai lần | Không body | Kết quả nhất quán nếu dữ liệu không đổi | Low | 09-get-vehicle-types.yaml |
| TC-BP04-012 | BP-04 – Select Vehicle Type | Boundary | Chọn lại cùng Vehicle Type | Customer chưa gửi request | 1. Chọn cùng type<br>2. Tạo request | vehicle_type_id=1 | Request dùng đúng type | Low | 10-create-ride-request.yaml |
| TC-BP04-013 | BP-04 – Select Vehicle Type | Empty | vehicle_type_id bị thiếu | Customer login | 1. POST request | Không field vehicle_type_id | HTTP 400 | High | 10-create-ride-request.yaml |
| TC-BP04-014 | BP-04 – Select Vehicle Type | Empty | Body request rỗng | Customer login | 1. POST request | {} | HTTP 400 | High | 10-create-ride-request.yaml |
| TC-BP04-015 | BP-04 – Select Vehicle Type | Empty | Không có Vehicle Type để chọn | Danh sách rỗng | 1. GET list | [] | Không thể tạo request hợp lệ nếu thiếu type | Medium | 09-get-vehicle-types.yaml |
| TC-BP04-016 | BP-04 – Select Vehicle Type | Empty | type_name rỗng trong dữ liệu nguồn | Dữ liệu lỗi | 1. GET list | type_name empty | Không được coi là lựa chọn hợp lệ theo nghiệp vụ | Medium | 09-get-vehicle-types.yaml |
| TC-BP04-017 | BP-04 – Select Vehicle Type | Invalid Format/Type | vehicle_type_id là chuỗi | Customer login | 1. POST request | vehicle_type_id=abc | HTTP 400 | High | 10-create-ride-request.yaml |
| TC-BP04-018 | BP-04 – Select Vehicle Type | Invalid Format/Type | vehicle_type_id là array | Customer login | 1. POST request | vehicle_type_id=[] | HTTP 400 | High | 10-create-ride-request.yaml |
| TC-BP04-019 | BP-04 – Select Vehicle Type | Invalid Format/Type | vehicle_type_id là object | Customer login | 1. POST request | vehicle_type_id={} | HTTP 400 | High | 10-create-ride-request.yaml |
| TC-BP04-020 | BP-04 – Select Vehicle Type | Invalid Format/Type | Gửi body không đúng API contract | Customer login | 1. POST request schema sai | Sai field/type | HTTP 400 | High | 10-create-ride-request.yaml |

## BP-05 – View Available Drivers

**Traceability:** FR-05.01–FR-05.03 → AC-05.01–AC-05.03

| Test Case ID | Test Scenario | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority | API Source |
|---|---|---|---|---|---|---|---|---|---|
| TC-BP05-001 | BP-05 – View Available Drivers | Positive | Hiển thị Driver AVAILABLE đúng loại xe | Ride Request hợp lệ | 1. GET /ride-requests/{id}/drivers | request_id hợp lệ | HTTP 200; danh sách chỉ gồm Driver phù hợp | High | 11-get-available-drivers.yaml |
| TC-BP05-002 | BP-05 – View Available Drivers | Positive | Kết quả có driver_id | Có Driver phù hợp | 1. GET drivers | request_id | Mỗi item có driver_id | Medium | 11-get-available-drivers.yaml |
| TC-BP05-003 | BP-05 – View Available Drivers | Positive | Kết quả có vehicle_id và vehicle_type | Có Driver phù hợp | 1. GET drivers | request_id | Thông tin Vehicle phù hợp được trả về | Medium | 11-get-available-drivers.yaml |
| TC-BP05-004 | BP-05 – View Available Drivers | Positive | Có nhiều Driver phù hợp để Customer tự chọn | Nhiều Driver AVAILABLE đúng type | 1. GET drivers | request_id | HTTP 200; trả nhiều Driver, không tự chọn best driver | High | 11-get-available-drivers.yaml |
| TC-BP05-005 | BP-05 – View Available Drivers | Negative | Driver BUSY không được hiển thị | Có Driver BUSY đúng type | 1. GET drivers | request_id | Không có Driver BUSY trong kết quả | High | 11-get-available-drivers.yaml |
| TC-BP05-006 | BP-05 – View Available Drivers | Negative | Driver OFFLINE không được hiển thị | Có Driver OFFLINE | 1. GET drivers | request_id | Không hiển thị Driver OFFLINE | High | 11-get-available-drivers.yaml |
| TC-BP05-007 | BP-05 – View Available Drivers | Negative | Driver sai Vehicle Type không được hiển thị | Driver AVAILABLE nhưng type khác | 1. GET drivers | request_id | Không hiển thị Driver sai type | High | 11-get-available-drivers.yaml |
| TC-BP05-008 | BP-05 – View Available Drivers | Negative | Request không thuộc Customer | Request thuộc user khác | 1. GET drivers | request_id khác owner | HTTP 403 theo RULE-15 | High | 11-get-available-drivers.yaml |
| TC-BP05-009 | BP-05 – View Available Drivers | Boundary | Không có Driver phù hợp | 0 Driver đáp ứng | 1. GET drivers | request_id | HTTP 200; drivers=[] | Medium | 11-get-available-drivers.yaml |
| TC-BP05-010 | BP-05 – View Available Drivers | Boundary | Có đúng 1 Driver phù hợp | 1 Driver đáp ứng | 1. GET drivers | request_id | HTTP 200; 1 item | Medium | 11-get-available-drivers.yaml |
| TC-BP05-011 | BP-05 – View Available Drivers | Boundary | Driver vừa chuyển AVAILABLE | Driver đúng type | 1. Driver PATCH AVAILABLE<br>2. Customer GET drivers | Driver hợp lệ | Driver có thể xuất hiện trong kết quả | Medium | 06-update-driver-status.yaml + 11-get-available-drivers.yaml |
| TC-BP05-012 | BP-05 – View Available Drivers | Boundary | Driver vừa chuyển BUSY | Driver trước đó AVAILABLE | 1. PATCH BUSY<br>2. GET drivers | Driver BUSY | Driver không còn trong kết quả | Medium | 06-update-driver-status.yaml + 11-get-available-drivers.yaml |
| TC-BP05-013 | BP-05 – View Available Drivers | Empty | Không token | Customer chưa login | 1. GET drivers | Không Authorization | HTTP 401 | High | 11-get-available-drivers.yaml |
| TC-BP05-014 | BP-05 – View Available Drivers | Empty | Danh sách Driver rỗng | Không Driver phù hợp | 1. GET drivers | request_id | HTTP 200; drivers=[] | Medium | 11-get-available-drivers.yaml |
| TC-BP05-015 | BP-05 – View Available Drivers | Empty | Request thiếu Vehicle Type do dữ liệu không hợp lệ | Ride Request không đủ điều kiện nghiệp vụ | 1. GET drivers | request không có type | Không hiển thị Driver phù hợp sai điều kiện | High | 11-get-available-drivers.yaml |
| TC-BP05-016 | BP-05 – View Available Drivers | Empty | Path id không được cung cấp | Customer login | 1. Gọi URL không có id | /ride-requests//drivers | Không khớp endpoint/không xử lý thành request hợp lệ | High | 11-get-available-drivers.yaml |
| TC-BP05-017 | BP-05 – View Available Drivers | Invalid Format/Type | request id sai định dạng | Customer login | 1. GET drivers | id=abc | HTTP 400/404 theo router | High | 11-get-available-drivers.yaml |
| TC-BP05-018 | BP-05 – View Available Drivers | Invalid Format/Type | request id không tồn tại | Customer login | 1. GET drivers | id=999999 | HTTP 404 | High | 11-get-available-drivers.yaml |
| TC-BP05-019 | BP-05 – View Available Drivers | Invalid Format/Type | Token malformed | Customer chưa xác thực hợp lệ | 1. GET drivers | Bearer abc | HTTP 401 | High | 11-get-available-drivers.yaml |
| TC-BP05-020 | BP-05 – View Available Drivers | Invalid Format/Type | Dùng sai HTTP method | Customer login | 1. POST vào endpoint GET | request_id hợp lệ | Method không được chấp nhận | Low | 11-get-available-drivers.yaml |

## BP-06 – Select Driver

**Traceability:** FR-06.01–FR-06.04 → AC-06.01–AC-06.04

| Test Case ID | Test Scenario | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority | API Source |
|---|---|---|---|---|---|---|---|---|---|
| TC-BP06-001 | BP-06 – Select Driver | Positive | Customer chọn Driver AVAILABLE | Driver nằm trong danh sách | 1. POST driver-selection | driver_id=10 | HTTP 201; tạo Trip Offer PENDING | High | 12-select-driver.yaml |
| TC-BP06-002 | BP-06 – Select Driver | Positive | Trip Offer trả đúng request_id | Selection thành công | 1. Kiểm tra response | request_id hiện tại | Response gắn đúng request_id | High | 12-select-driver.yaml |
| TC-BP06-003 | BP-06 – Select Driver | Positive | Trip Offer trả đúng driver_id | Selection thành công | 1. Kiểm tra response | driver_id=10 | Response gắn đúng driver_id | High | 12-select-driver.yaml |
| TC-BP06-004 | BP-06 – Select Driver | Positive | Offer có status PENDING | Selection thành công | 1. Kiểm tra response | driver_id hợp lệ | status=PENDING | High | 12-select-driver.yaml |
| TC-BP06-005 | BP-06 – Select Driver | Negative | Driver không còn AVAILABLE | Driver chuyển BUSY trước POST | 1. POST selection | driver_id=10 | Không tạo Trip Offer mới | High | 12-select-driver.yaml |
| TC-BP06-006 | BP-06 – Select Driver | Negative | Driver sai Vehicle Type | Driver không phù hợp request | 1. POST selection | driver_id sai type | Từ chối theo RULE-06 | High | 12-select-driver.yaml |
| TC-BP06-007 | BP-06 – Select Driver | Negative | Driver không tồn tại | Request hợp lệ | 1. POST selection | driver_id=999999 | HTTP 404 | High | 12-select-driver.yaml |
| TC-BP06-008 | BP-06 – Select Driver | Negative | Request không thuộc Customer | Customer B login | 1. POST selection cho request A | driver_id hợp lệ | HTTP 403 | High | 12-select-driver.yaml |
| TC-BP06-009 | BP-06 – Select Driver | Boundary | Có đúng 1 Driver phù hợp | List có 1 item | 1. Chọn Driver duy nhất | driver_id hợp lệ | HTTP 201 | Medium | 12-select-driver.yaml |
| TC-BP06-010 | BP-06 – Select Driver | Boundary | Driver đổi AVAILABLE → BUSY giữa GET và POST | Đã xem list | 1. GET list<br>2. Driver BUSY<br>3. POST selection | driver_id | Hệ thống re-check và từ chối | High | 11-get-available-drivers.yaml + 12-select-driver.yaml |
| TC-BP06-011 | BP-06 – Select Driver | Boundary | Lựa chọn lại Driver khác sau lần thất bại | Offer chưa tạo | 1. POST driver 1 lỗi<br>2. POST driver 2 | driver_id khác | Driver 2 hợp lệ được tạo offer | Medium | 12-select-driver.yaml |
| TC-BP06-012 | BP-06 – Select Driver | Boundary | Chọn ngay sau khi tải danh sách | Driver vẫn AVAILABLE | 1. GET list<br>2. POST selection | driver_id hợp lệ | HTTP 201 | Medium | 11-get-available-drivers.yaml + 12-select-driver.yaml |
| TC-BP06-013 | BP-06 – Select Driver | Empty | Thiếu driver_id | Request hợp lệ | 1. POST selection | {} | HTTP 400 | High | 12-select-driver.yaml |
| TC-BP06-014 | BP-06 – Select Driver | Empty | Body rỗng | Request hợp lệ | 1. POST selection | {} | HTTP 400 | High | 12-select-driver.yaml |
| TC-BP06-015 | BP-06 – Select Driver | Empty | Không token | Chưa login | 1. POST selection | Không Authorization | HTTP 401 | High | 12-select-driver.yaml |
| TC-BP06-016 | BP-06 – Select Driver | Empty | Path request id thiếu | Customer login | 1. Gọi URL thiếu id | /ride-requests//driver-selection | Không xử lý thành request hợp lệ | High | 12-select-driver.yaml |
| TC-BP06-017 | BP-06 – Select Driver | Invalid Format/Type | driver_id sai kiểu | Request hợp lệ | 1. POST selection | driver_id=abc | HTTP 400 | High | 12-select-driver.yaml |
| TC-BP06-018 | BP-06 – Select Driver | Invalid Format/Type | driver_id là array | Request hợp lệ | 1. POST selection | driver_id=[] | HTTP 400 | High | 12-select-driver.yaml |
| TC-BP06-019 | BP-06 – Select Driver | Invalid Format/Type | request id không tồn tại | Customer login | 1. POST selection | id=999999 | HTTP 404 | High | 12-select-driver.yaml |
| TC-BP06-020 | BP-06 – Select Driver | Invalid Format/Type | Token malformed | Customer chưa xác thực hợp lệ | 1. POST selection | Bearer abc | HTTP 401 | High | 12-select-driver.yaml |

## BP-07 – Driver Responds to Trip Offer

**Traceability:** FR-07.01–FR-07.05 → AC-07.01–AC-07.05

| Test Case ID | Test Scenario | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority | API Source |
|---|---|---|---|---|---|---|---|---|---|
| TC-BP07-001 | BP-07 – Driver Responds to Trip Offer | Positive | Driver xem Trip Offer của mình | Driver có offer | 1. GET trip-offers | Token Driver | HTTP 200; trả trip_offers của Driver | High | 13-get-trip-offers.yaml |
| TC-BP07-002 | BP-07 – Driver Responds to Trip Offer | Positive | Driver ACCEPT offer hợp lệ | Offer PENDING; Driver có thể nhận chuyến | 1. PATCH response | response=ACCEPT | HTTP 200; status=ACCEPTED; có trip_id | High | 14-respond-trip-offer.yaml |
| TC-BP07-003 | BP-07 – Driver Responds to Trip Offer | Positive | Driver REJECT offer hợp lệ | Offer PENDING | 1. PATCH response | response=REJECT | HTTP 200; status=REJECTED | High | 14-respond-trip-offer.yaml |
| TC-BP07-004 | BP-07 – Driver Responds to Trip Offer | Positive | Trip chỉ được tạo sau ACCEPT | Offer PENDING | 1. ACCEPT<br>2. Kiểm tra response | ACCEPT | trip_id được tạo sau ACCEPT | High | 14-respond-trip-offer.yaml |
| TC-BP07-005 | BP-07 – Driver Responds to Trip Offer | Negative | Driver khác phản hồi Offer | Offer thuộc Driver A | 1. Driver B PATCH response | offer_id của A | HTTP 403 | High | 14-respond-trip-offer.yaml |
| TC-BP07-006 | BP-07 – Driver Responds to Trip Offer | Negative | Customer gọi API phản hồi Offer | Customer login | 1. PATCH response | ACCEPT | HTTP 403 | High | 14-respond-trip-offer.yaml |
| TC-BP07-007 | BP-07 – Driver Responds to Trip Offer | Negative | ACCEPT khi Driver đang BUSY | Driver có Trip active | 1. PATCH ACCEPT | ACCEPT | Từ chối theo RULE-08 | High | 14-respond-trip-offer.yaml |
| TC-BP07-008 | BP-07 – Driver Responds to Trip Offer | Negative | Phản hồi Offer không tồn tại | Driver login | 1. PATCH response | id=999999 | HTTP 404 | High | 14-respond-trip-offer.yaml |
| TC-BP07-009 | BP-07 – Driver Responds to Trip Offer | Boundary | Driver không có Offer | Không có Trip Offer | 1. GET offers | Token Driver | HTTP 200; trip_offers=[] | Medium | 13-get-trip-offers.yaml |
| TC-BP07-010 | BP-07 – Driver Responds to Trip Offer | Boundary | Driver có đúng 1 Offer | Có 1 offer | 1. GET offers | Token Driver | HTTP 200; 1 item | Medium | 13-get-trip-offers.yaml |
| TC-BP07-011 | BP-07 – Driver Responds to Trip Offer | Boundary | Reject rồi Customer chọn Driver khác | Offer 1 REJECTED | 1. Reject<br>2. Customer chọn Driver 2 | Driver 2 hợp lệ | Tạo Trip Offer mới mà không nhập lại Ride Request | High | 14-respond-trip-offer.yaml + 12-select-driver.yaml |
| TC-BP07-012 | BP-07 – Driver Responds to Trip Offer | Boundary | ACCEPT trả trip_id nullable thành giá trị thực | Offer PENDING | 1. PATCH ACCEPT | ACCEPT | trip_id không null khi Trip được tạo | High | 14-respond-trip-offer.yaml |
| TC-BP07-013 | BP-07 – Driver Responds to Trip Offer | Empty | response bị thiếu | Offer PENDING | 1. PATCH response | {} | HTTP 400 | High | 14-respond-trip-offer.yaml |
| TC-BP07-014 | BP-07 – Driver Responds to Trip Offer | Empty | Không token khi xem offers | Chưa login | 1. GET offers | Không token | HTTP 401 | High | 13-get-trip-offers.yaml |
| TC-BP07-015 | BP-07 – Driver Responds to Trip Offer | Empty | Không token khi phản hồi | Chưa login | 1. PATCH response | ACCEPT | HTTP 401 | High | 14-respond-trip-offer.yaml |
| TC-BP07-016 | BP-07 – Driver Responds to Trip Offer | Empty | Path offer id thiếu | Driver login | 1. Gọi URL thiếu id | /trip-offers//response | Không xử lý thành request hợp lệ | High | 14-respond-trip-offer.yaml |
| TC-BP07-017 | BP-07 – Driver Responds to Trip Offer | Invalid Format/Type | response ngoài enum | Offer PENDING | 1. PATCH response | response=MAYBE | HTTP 400 | High | 14-respond-trip-offer.yaml |
| TC-BP07-018 | BP-07 – Driver Responds to Trip Offer | Invalid Format/Type | response sai kiểu | Offer PENDING | 1. PATCH response | response=[] | HTTP 400 | High | 14-respond-trip-offer.yaml |
| TC-BP07-019 | BP-07 – Driver Responds to Trip Offer | Invalid Format/Type | offer id sai định dạng | Driver login | 1. PATCH response | id=abc | HTTP 400/404 theo router | High | 14-respond-trip-offer.yaml |
| TC-BP07-020 | BP-07 – Driver Responds to Trip Offer | Invalid Format/Type | Token malformed | Driver chưa xác thực hợp lệ | 1. GET offers | Bearer abc | HTTP 401 | High | 13-get-trip-offers.yaml |

## BP-08 – Trip Execution

**Traceability:** FR-08.01–FR-08.05 → AC-08.01–AC-08.05

| Test Case ID | Test Scenario | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority | API Source |
|---|---|---|---|---|---|---|---|---|---|
| TC-BP08-001 | BP-08 – Trip Execution | Positive | Customer xem Trip của mình | Trip thuộc Customer | 1. GET /trips/{id} | trip_id hợp lệ | HTTP 200; trả đúng Trip | High | 15-get-trip.yaml |
| TC-BP08-002 | BP-08 – Trip Execution | Positive | Driver xem Trip được phân công | Trip thuộc Driver | 1. GET Trip | trip_id hợp lệ | HTTP 200 | High | 15-get-trip.yaml |
| TC-BP08-003 | BP-08 – Trip Execution | Positive | Assigned → Arriving | Driver được phân công | 1. PATCH status | status=Arriving | HTTP 200; status=Arriving | High | 16-update-trip-status.yaml |
| TC-BP08-004 | BP-08 – Trip Execution | Positive | Arriving → Arrived | Trip Arriving | 1. PATCH status | status=Arrived | HTTP 200 | High | 16-update-trip-status.yaml |
| TC-BP08-005 | BP-08 – Trip Execution | Positive | Arrived → PickedUp | Trip Arrived | 1. PATCH status | status=PickedUp | HTTP 200 | High | 16-update-trip-status.yaml |
| TC-BP08-006 | BP-08 – Trip Execution | Positive | PickedUp → InProgress | Trip PickedUp | 1. PATCH status | status=InProgress | HTTP 200 | High | 16-update-trip-status.yaml |
| TC-BP08-007 | BP-08 – Trip Execution | Positive | InProgress → Completed | Trip InProgress | 1. PATCH status | status=Completed | HTTP 200; Trip Completed | High | 16-update-trip-status.yaml |
| TC-BP08-008 | BP-08 – Trip Execution | Negative | Nhảy Assigned → Completed | Trip Assigned | 1. PATCH status | Completed | Từ chối theo RULE-13 | High | 16-update-trip-status.yaml |
| TC-BP08-009 | BP-08 – Trip Execution | Negative | Driver khác cập nhật Trip | Trip thuộc Driver A | 1. Driver B PATCH status | Arriving | HTTP 403 | High | 16-update-trip-status.yaml |
| TC-BP08-010 | BP-08 – Trip Execution | Negative | Customer cập nhật Trip status | Customer login | 1. PATCH status | Arriving | HTTP 403 | High | 16-update-trip-status.yaml |
| TC-BP08-011 | BP-08 – Trip Execution | Boundary | Customer GET ngay sau Driver đổi status | Trip vừa đổi status | 1. Driver PATCH<br>2. Customer GET | trip_id | Customer thấy trạng thái hiện tại | Medium | 16-update-trip-status.yaml + 15-get-trip.yaml |
| TC-BP08-012 | BP-08 – Trip Execution | Boundary | Completed không quay lại trạng thái trước | Trip Completed | 1. PATCH InProgress | InProgress | Từ chối theo RULE-14 | High | 16-update-trip-status.yaml |
| TC-BP08-013 | BP-08 – Trip Execution | Boundary | Bước đầu lifecycle | Trip Assigned | 1. PATCH Arriving | Arriving | HTTP 200 | Medium | 16-update-trip-status.yaml |
| TC-BP08-014 | BP-08 – Trip Execution | Boundary | Bước cuối lifecycle | Trip InProgress | 1. PATCH Completed | Completed | HTTP 200 | Medium | 16-update-trip-status.yaml |
| TC-BP08-015 | BP-08 – Trip Execution | Empty | status bị thiếu | Driver được phân công | 1. PATCH status | {} | HTTP 400 | High | 16-update-trip-status.yaml |
| TC-BP08-016 | BP-08 – Trip Execution | Empty | Không token khi xem Trip | Chưa login | 1. GET Trip | Không token | HTTP 401 | High | 15-get-trip.yaml |
| TC-BP08-017 | BP-08 – Trip Execution | Invalid Format/Type | status ngoài enum | Driver được phân công | 1. PATCH status | status=RUNNING | HTTP 400 | High | 16-update-trip-status.yaml |
| TC-BP08-018 | BP-08 – Trip Execution | Invalid Format/Type | status sai kiểu | Driver được phân công | 1. PATCH status | status=[] | HTTP 400 | High | 16-update-trip-status.yaml |
| TC-BP08-019 | BP-08 – Trip Execution | Invalid Format/Type | trip id không tồn tại | User login | 1. GET Trip | id=999999 | HTTP 404 | High | 15-get-trip.yaml |
| TC-BP08-020 | BP-08 – Trip Execution | Invalid Format/Type | Token malformed | User chưa xác thực hợp lệ | 1. GET Trip | Bearer abc | HTTP 401 | High | 15-get-trip.yaml |

## BP-09 – Trip History

**Traceability:** FR-09.01–FR-09.03 → AC-09.01–AC-09.03

| Test Case ID | Test Scenario | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority | API Source |
|---|---|---|---|---|---|---|---|---|---|
| TC-BP09-001 | BP-09 – Trip History | Positive | Trip Completed xuất hiện trong lịch sử | Trip vừa Completed | 1. Complete Trip<br>2. GET history | trip_id vừa hoàn thành | HTTP 200; Trip xuất hiện | High | 16-update-trip-status.yaml + 17-get-trip-history.yaml |
| TC-BP09-002 | BP-09 – Trip History | Positive | Customer xem lịch sử của mình | Customer có Trip | 1. GET /users/me/trips | Token Customer | HTTP 200; trả Trip thuộc Customer | High | 17-get-trip-history.yaml |
| TC-BP09-003 | BP-09 – Trip History | Positive | Driver xem lịch sử của mình | Driver có Trip | 1. GET history | Token Driver | HTTP 200; trả Trip thuộc Driver | High | 17-get-trip-history.yaml |
| TC-BP09-004 | BP-09 – Trip History | Positive | History trả các trường Trip cơ bản | Có Trip Completed | 1. GET history | Token hợp lệ | Mỗi item có trip_id, status, pickup_location, destination, completed_at | Medium | 17-get-trip-history.yaml |
| TC-BP09-005 | BP-09 – Trip History | Negative | Customer không thấy Trip người khác | Có dữ liệu Customer khác | 1. GET history | Token Customer A | Không trả Trip Customer B | High | 17-get-trip-history.yaml |
| TC-BP09-006 | BP-09 – Trip History | Negative | Driver không thấy Trip Driver khác | Có dữ liệu Driver khác | 1. GET history | Token Driver A | Không trả Trip Driver B | High | 17-get-trip-history.yaml |
| TC-BP09-007 | BP-09 – Trip History | Negative | Chưa login xem history | Không token | 1. GET history | Không Authorization | HTTP 401 | High | 17-get-trip-history.yaml |
| TC-BP09-008 | BP-09 – Trip History | Negative | Token không hợp lệ xem history | Token sai | 1. GET history | Bearer abc | HTTP 401 | High | 17-get-trip-history.yaml |
| TC-BP09-009 | BP-09 – Trip History | Boundary | Customer chưa có Trip | 0 Trip | 1. GET history | Token Customer | HTTP 200; trips=[] | Medium | 17-get-trip-history.yaml |
| TC-BP09-010 | BP-09 – Trip History | Boundary | Driver chưa có Trip | 0 Trip | 1. GET history | Token Driver | HTTP 200; trips=[] | Medium | 17-get-trip-history.yaml |
| TC-BP09-011 | BP-09 – Trip History | Boundary | Có đúng 1 Trip Completed | 1 Trip | 1. GET history | Token hợp lệ | HTTP 200; 1 item | Medium | 17-get-trip-history.yaml |
| TC-BP09-012 | BP-09 – Trip History | Boundary | Trip vừa Completed | Vừa PATCH Completed | 1. GET history ngay | Token hợp lệ | Trip được ghi nhận trong history | Medium | 17-get-trip-history.yaml |
| TC-BP09-013 | BP-09 – Trip History | Empty | History rỗng của tài khoản mới | Customer mới | 1. GET history | Token Customer | HTTP 200; trips=[] | Medium | 17-get-trip-history.yaml |
| TC-BP09-014 | BP-09 – Trip History | Empty | Không Authorization header | Chưa xác thực | 1. GET history | Header absent | HTTP 401 | High | 17-get-trip-history.yaml |
| TC-BP09-015 | BP-09 – Trip History | Empty | Không có Trip Completed | User chưa hoàn thành Trip | 1. GET history | Token hợp lệ | Không hiển thị Trip chưa hoàn thành như lịch sử Completed | Medium | 17-get-trip-history.yaml |
| TC-BP09-016 | BP-09 – Trip History | Empty | Danh sách kết quả rỗng không gây lỗi | Không có dữ liệu | 1. GET history | 0 item | HTTP 200 và mảng rỗng | Low | 17-get-trip-history.yaml |
| TC-BP09-017 | BP-09 – Trip History | Invalid Format/Type | Token malformed | Token sai định dạng | 1. GET history | Bearer [] | HTTP 401 | High | 17-get-trip-history.yaml |
| TC-BP09-018 | BP-09 – Trip History | Invalid Format/Type | Authorization scheme sai | Có token nhưng scheme sai | 1. GET history | Token abc | HTTP 401 | High | 17-get-trip-history.yaml |
| TC-BP09-019 | BP-09 – Trip History | Invalid Format/Type | Dùng sai HTTP method | User login | 1. POST vào history endpoint | Token hợp lệ | Method không được chấp nhận | Low | 17-get-trip-history.yaml |
| TC-BP09-020 | BP-09 – Trip History | Invalid Format/Type | Header Authorization có giá trị không hợp lệ | User login không hợp lệ | 1. GET history | Authorization=123 | HTTP 401 | High | 17-get-trip-history.yaml |

- Các endpoint, HTTP method, request field, enum và HTTP response được đối chiếu với **17 file YAML hiện tại**.
- Các quy tắc nghiệp vụ quan trọng được kiểm thử: chỉ Driver `AVAILABLE`, đúng Vehicle Type, Customer tự chọn Driver, một Driver không thực hiện nhiều Trip cùng lúc, Driver chỉ phản hồi Offer của mình, Trip chỉ tạo sau Accept và Trip status phải theo đúng thứ tự.
- Không tạo Test Case cho Payment, Rating, Notification, AI Matching hoặc Dynamic Pricing vì SRS xác định chúng ngoài phạm vi MVP.
