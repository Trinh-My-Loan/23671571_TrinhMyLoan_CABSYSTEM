# SRS – CAB System

# 1. Stakeholder Analysis

## 1.1. Mục đích

Stakeholder là các cá nhân, nhóm hoặc tổ chức có ảnh hưởng đến dự án CAB System hoặc chịu ảnh hưởng từ hoạt động của hệ thống.

Dựa trên yêu cầu của khách hàng, các stakeholder được xác định gồm các nhóm nội bộ, bên ngoài và các hệ thống bên thứ ba.

---

## 1.2. Danh sách Stakeholder và Vai trò

| STT | Stakeholder | Loại | Vai trò |
|---:|---|---|---|
| 1 | Ban giám đốc | Internal | Định hướng dự án, phê duyệt ngân sách và theo dõi hiệu quả kinh doanh |
| 2 | Khách hàng | External | Đăng ký, đặt xe, theo dõi chuyến, thanh toán và đánh giá tài xế |
| 3 | Tài xế | External | Nhận chuyến, thực hiện chuyến và cập nhật trạng thái chuyến |
| 4 | Nhân viên vận hành | Internal | Quản lý khách hàng, tài xế, phương tiện và chuyến đi |
| 5 | Quản trị viên hệ thống | Internal | Quản lý tài khoản, phân quyền, cấu hình và bảo mật hệ thống |
| 6 | Bộ phận kế toán / tài chính | Internal | Quản lý giao dịch, doanh thu và đối soát thanh toán |
| 7 | Bộ phận chăm sóc khách hàng | Internal | Hỗ trợ khách hàng, xử lý khiếu nại và sự cố |
| 8 | Business Analyst | Internal | Thu thập, phân tích và làm rõ yêu cầu nghiệp vụ |
| 9 | Đội phát triển phần mềm | Internal | Thiết kế, xây dựng và bảo trì hệ thống |
| 10 | QA / Tester | Internal | Kiểm thử và đảm bảo chất lượng hệ thống |
| 11 | DevOps / System Administrator | Internal | Triển khai, giám sát và đảm bảo hệ thống hoạt động ổn định |
| 12 | Nhà cung cấp thanh toán | External | Xử lý các giao dịch thanh toán điện tử |
| 13 | Nhà cung cấp bản đồ / GPS | External | Cung cấp vị trí, khoảng cách và hỗ trợ tính ETA |
| 14 | Nhà cung cấp dịch vụ thông báo | External | Gửi thông báo qua Push Notification, SMS hoặc Email |

---

# 2. Stakeholder Matrix

## 2.1. Tiêu chí đánh giá

Stakeholder được phân loại dựa trên hai tiêu chí:

- **Power (Mức độ ảnh hưởng):** Khả năng tác động đến quyết định, phạm vi và kết quả dự án.
- **Interest (Mức độ quan tâm):** Mức độ quan tâm đến hoạt động và kết quả của hệ thống.

Mỗi stakeholder được phân loại vào một trong bốn nhóm:

| Nhóm | Power | Interest | Chiến lược |
|---|---|---|---|
| Manage Closely | Cao | Cao | Quản lý chặt chẽ, thường xuyên trao đổi |
| Keep Satisfied | Cao | Thấp | Đảm bảo hài lòng và cập nhật khi cần |
| Keep Informed | Thấp | Cao | Cung cấp thông tin thường xuyên |
| Monitor | Thấp | Thấp | Theo dõi và cập nhật khi cần |

---

## 2.2. Phân loại Stakeholder

| Stakeholder | Power | Interest | Nhóm | Chiến lược |
|---|---|---|---|---|
| Ban giám đốc | Cao | Cao | Manage Closely | Báo cáo tiến độ, rủi ro và kết quả dự án |
| Nhân viên vận hành | Cao | Cao | Manage Closely | Tham gia phân tích và xác nhận quy trình nghiệp vụ |
| Khách hàng | Thấp | Cao | Keep Informed | Thu thập phản hồi và cập nhật tính năng |
| Tài xế | Thấp | Cao | Keep Informed | Thu thập phản hồi và hướng dẫn sử dụng |
| Quản trị viên hệ thống | Cao | Cao | Manage Closely | Tham gia thiết kế quyền, bảo mật và vận hành |
| Kế toán / Tài chính | Cao | Cao | Manage Closely | Xác nhận yêu cầu thanh toán và báo cáo tài chính |
| Chăm sóc khách hàng | Thấp | Cao | Keep Informed | Thu thập yêu cầu hỗ trợ và phản hồi |
| Business Analyst | Cao | Cao | Manage Closely | Phân tích, quản lý và xác nhận yêu cầu |
| Đội phát triển phần mềm | Cao | Cao | Manage Closely | Phối hợp triển khai giải pháp kỹ thuật |
| QA / Tester | Thấp | Cao | Keep Informed | Cập nhật yêu cầu và tiêu chí kiểm thử |
| DevOps / System Administrator | Cao | Cao | Manage Closely | Phối hợp triển khai, giám sát và mở rộng hệ thống |
| Nhà cung cấp thanh toán | Cao | Thấp | Keep Satisfied | Quản lý tích hợp và đảm bảo dịch vụ ổn định |
| Nhà cung cấp bản đồ / GPS | Thấp | Thấp | Monitor | Theo dõi chất lượng dịch vụ |
| Nhà cung cấp thông báo | Thấp | Thấp | Monitor | Theo dõi khả năng gửi thông báo |

---

## 2.3. Stakeholder Power / Interest Matrix

```mermaid
quadrantChart
    title Stakeholder Power / Interest Matrix
    x-axis "Low Interest" --> "High Interest"
    y-axis "Low Power" --> "High Power"

    quadrant-1 "Manage Closely"
    quadrant-2 "Keep Satisfied"
    quadrant-3 "Monitor"
    quadrant-4 "Keep Informed"

    "Ban giám đốc": [0.85, 0.90]
    "Nhân viên vận hành": [0.85, 0.80]
    "Quản trị viên hệ thống": [0.80, 0.85]
    "Kế toán / Tài chính": [0.75, 0.75]
    "Business Analyst": [0.90, 0.85]
    "Đội phát triển": [0.85, 0.75]
    "DevOps": [0.80, 0.80]

    "Khách hàng": [0.85, 0.30]
    "Tài xế": [0.80, 0.25]
    "Chăm sóc khách hàng": [0.75, 0.30]
    "QA / Tester": [0.70, 0.25]

    "Nhà cung cấp thanh toán": [0.25, 0.75]
    "Nhà cung cấp bản đồ / GPS": [0.25, 0.30]
    "Nhà cung cấp thông báo": [0.20, 0.25]
