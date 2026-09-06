# 2. Stakeholder Analysis

## 2.1. Identified Stakeholders

Các bên liên quan (Stakeholders) của hệ thống CAB được xác định như sau:

| Stakeholder                   | Vai trò                                                                                                |
| ----------------------------- | ------------------------------------------------------------------------------------------------------ |
| Customer (Khách hàng)         | Sử dụng hệ thống để đặt xe, theo dõi chuyến đi, thanh toán và đánh giá tài xế.                         |
| Driver (Tài xế)               | Nhận và thực hiện chuyến đi, cập nhật trạng thái hoạt động và vị trí.                                  |
| Operator (Nhân viên vận hành) | Quản lý khách hàng, tài xế, phương tiện và hỗ trợ xử lý các vấn đề phát sinh trong quá trình vận hành. |
| Administrator                 | Quản lý hệ thống, phân quyền người dùng và kiểm soát các chức năng quản trị.                           |
| Management (Ban lãnh đạo)     | Theo dõi hoạt động kinh doanh, doanh thu và các báo cáo về hiệu quả hoạt động của hệ thống.            |
| Payment Provider              | Cung cấp dịch vụ xử lý thanh toán điện tử cho hệ thống.                                                |
| Notification Provider         | Cung cấp dịch vụ gửi thông báo đến khách hàng và tài xế.                                               |
| Development Team              | Phát triển, kiểm thử, triển khai và bảo trì hệ thống CAB.                                              |
| Business Analyst              | Thu thập, phân tích và làm rõ yêu cầu giữa khách hàng và nhóm phát triển.                              |

---

## 2.2. Stakeholder Matrix

Stakeholder Matrix được xây dựng dựa trên hai tiêu chí:

* **Power:** Mức độ ảnh hưởng đến dự án.
* **Interest:** Mức độ quan tâm đến hệ thống.

| Stakeholder           | Power  | Interest | Management Strategy |
| --------------------- | ------ | -------- | ------------------- |
| Management            | High   | High     | Manage Closely      |
| Operator              | High   | High     | Manage Closely      |
| Customer              | Low    | High     | Keep Informed       |
| Driver                | Low    | High     | Keep Informed       |
| Administrator         | High   | High     | Manage Closely      |
| Payment Provider      | High   | Medium   | Keep Satisfied      |
| Notification Provider | Medium | Medium   | Monitor             |
| Development Team      | Medium | High     | Keep Informed       |
| Business Analyst      | Medium | High     | Keep Informed       |

---

## 2.3. Power – Interest Matrix

```mermaid
quadrantChart
    title Stakeholder Power - Interest Matrix
    x-axis Low Interest --> High Interest
    y-axis Low Power --> High Power

    quadrant-1 Manage Closely
    quadrant-2 Keep Satisfied
    quadrant-3 Monitor
    quadrant-4 Keep Informed

    Management: [0.9, 0.9]
    Administrator: [0.8, 0.9]
    Operator: [0.8, 0.8]

    Payment Provider: [0.5, 0.8]

    Notification Provider: [0.4, 0.5]

    Customer: [0.9, 0.3]
    Driver: [0.8, 0.3]
    Development Team: [0.8, 0.5]
    Business Analyst: [0.8, 0.5]
```

---

## 2.4. Stakeholder Relationship Diagram

```mermaid
flowchart TB

    Management[Management]
    BA[Business Analyst]
    Dev[Development Team]

    Customer[Customer]
    Driver[Driver]
    Operator[Operator]
    Admin[Administrator]

    CAB[CAB System]

    Payment[Payment Provider]
    Notification[Notification Provider]

    Management -->|Business Goals & Decisions| BA
    BA -->|Requirements| Dev

    Customer -->|Booking & Payment| CAB
    Driver -->|Accept & Perform Trip| CAB
    Operator -->|Manage Operations| CAB
    Admin -->|System Administration| CAB

    CAB -->|Payment Request| Payment
    Payment -->|Payment Result| CAB

    CAB -->|Send Notification| Notification

    Dev -->|Develop & Maintain| CAB
    Management -->|Monitor Reports| CAB
```

---

## 2.5. Stakeholder Classification

### Primary Stakeholders

Các Stakeholder trực tiếp sử dụng hệ thống:

* Customer
* Driver
* Operator
* Administrator

### Key Stakeholders

Các Stakeholder có ảnh hưởng lớn đến dự án:

* Management
* Business Analyst
* Development Team

### External Stakeholders

Các bên cung cấp dịch vụ bên ngoài:

* Payment Provider
* Notification Provider

# 4. Business Goals

## 4.1. Business Goal Identification

Dựa trên yêu cầu và kỳ vọng của khách hàng, các mục tiêu nghiệp vụ của dự án CAB System được xác định như sau:

| ID    | Customer Requirement                                                    | Business Goal                                                                   |
| ----- | ----------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| BG-01 | Hệ thống hiện tại phân công tài xế chủ yếu thủ công.                    | Tự động hóa quá trình tìm kiếm và phân công tài xế phù hợp.                     |
| BG-02 | Khách hàng khó theo dõi trạng thái chuyến đi.                           | Nâng cao khả năng theo dõi và quản lý trạng thái chuyến đi theo thời gian thực. |
| BG-03 | Thông tin thanh toán chưa được quản lý tập trung.                       | Xây dựng cơ chế tính cước và quản lý thanh toán tập trung, an toàn.             |
| BG-04 | Bộ phận vận hành gặp khó khăn trong việc quản lý và mở rộng hệ thống.   | Nâng cao hiệu quả quản lý và vận hành hoạt động đặt xe.                         |
| BG-05 | Hệ thống cần phục vụ số lượng lớn khách hàng và tài xế.                 | Xây dựng hệ thống có khả năng mở rộng và đáp ứng nhu cầu tăng trưởng.           |
| BG-06 | Khách hàng và tài xế cần được thông báo về các sự kiện quan trọng.      | Cung cấp cơ chế thông báo kịp thời trong quá trình sử dụng dịch vụ.             |
| BG-07 | Ban lãnh đạo cần theo dõi số chuyến, doanh thu và hiệu quả tài xế.      | Cung cấp dữ liệu và báo cáo hỗ trợ quản lý và ra quyết định.                    |
| BG-08 | Dữ liệu cá nhân, vị trí và giao dịch cần được bảo vệ.                   | Đảm bảo an toàn và bảo mật thông tin trong hệ thống.                            |
| BG-09 | Các chức năng quản trị cần được kiểm soát quyền truy cập.               | Đảm bảo kiểm soát và phân quyền phù hợp cho người dùng hệ thống.                |
| BG-10 | Hệ thống cần có khả năng phát triển thêm các tính năng trong tương lai. | Xây dựng nền tảng linh hoạt, dễ bảo trì và hỗ trợ mở rộng trong tương lai.      |

---

## 4.2. Detailed Business Goals

### BG-01: Automate Driver Matching and Assignment

Tự động hóa quá trình tìm kiếm, lựa chọn và phân công tài xế phù hợp nhằm giảm sự phụ thuộc vào việc điều phối thủ công và nâng cao hiệu quả phục vụ khách hàng.

---

### BG-02: Improve Trip Visibility

Cung cấp khả năng theo dõi trạng thái chuyến đi và thông tin liên quan, giúp khách hàng và bộ phận vận hành dễ dàng kiểm soát quá trình thực hiện chuyến đi.

---

### BG-03: Centralize Fare and Payment Management

Xây dựng cơ chế tính cước và quản lý thanh toán tập trung, hỗ trợ nhiều phương thức thanh toán và đảm bảo an toàn thông tin giao dịch.

---

### BG-04: Improve Operational Efficiency

Cung cấp công cụ hỗ trợ bộ phận vận hành quản lý khách hàng, tài xế, phương tiện và chuyến đi, từ đó nâng cao hiệu quả hoạt động của doanh nghiệp.

---

### BG-05: Support System Scalability

Xây dựng hệ thống có khả năng đáp ứng số lượng lớn khách hàng và tài xế, đồng thời cho phép các thành phần được mở rộng khi nhu cầu sử dụng tăng.

---

### BG-06: Provide Timely Notifications

Cung cấp cơ chế thông báo kịp thời cho khách hàng và tài xế về các sự kiện quan trọng trong quá trình đặt và thực hiện chuyến đi.

---

### BG-07: Support Business Monitoring and Decision Making

Cung cấp các báo cáo và dữ liệu cần thiết về hoạt động kinh doanh, doanh thu, chuyến đi và hiệu quả tài xế nhằm hỗ trợ ban lãnh đạo theo dõi và ra quyết định.

---

### BG-08: Ensure Data Security

Đảm bảo thông tin cá nhân, dữ liệu vị trí và dữ liệu giao dịch được bảo vệ, đồng thời hạn chế các rủi ro liên quan đến bảo mật thông tin.

---

### BG-09: Ensure Access Control

Thiết lập cơ chế phân quyền phù hợp nhằm đảm bảo người dùng chỉ có thể truy cập và thực hiện các chức năng được cho phép.

---

### BG-10: Enable Future System Expansion

Xây dựng nền tảng có kiến trúc linh hoạt, cho phép bổ sung dịch vụ, phương thức thanh toán, nhà cung cấp thông báo và các chức năng mới mà không cần xây dựng lại toàn bộ hệ thống.

---

## 4.3. Business Goal Hierarchy

```mermaid
mindmap
  root((CAB System))
    Improve Service
      Automate Driver Matching
      Improve Trip Visibility
      Provide Notifications
    Improve Operations
      Improve Operational Efficiency
      Centralize Payment Management
      Provide Business Reports
    Build Sustainable Platform
      Ensure Scalability
      Ensure Security
      Ensure Access Control
      Enable Future Expansion
```
# 5. Project Scope

## 5.1. Scope Identification

Dựa trên các Business Goals đã xác định, phạm vi dự án được giới hạn dựa trên:

* Thời gian phát triển dự án: **7 tuần**.
* Mục tiêu xây dựng phiên bản MVP.
* Ưu tiên các chức năng cốt lõi của hệ thống đặt xe.
* Các module phải trực tiếp hỗ trợ Business Goals.
* Các chức năng nâng cao sẽ được phát triển trong các giai đoạn sau.

Quy trình cốt lõi của CAB System:

```text
Account
   ↓
Booking
   ↓
Driver Matching
   ↓
Trip Management
   ↓
Fare Calculation
   ↓
Payment
   ↓
Notification
   ↓
Rating
```

---

## 5.2. Business Goals to Modules Mapping

| Business Goal                                          | Module đề xuất                                                                   |
| ------------------------------------------------------ | -------------------------------------------------------------------------------- |
| BG-01: Automate Driver Matching and Assignment         | Booking Management, Driver Matching                                              |
| BG-02: Improve Trip Visibility                         | Trip Management, Location Tracking                                               |
| BG-03: Centralize Fare and Payment Management          | Fare Calculation, Payment Management                                             |
| BG-04: Improve Operational Efficiency                  | Customer Management, Driver Management, Vehicle Management, Operation Management |
| BG-05: Support System Scalability                      | System Architecture, Module-based Design                                         |
| BG-06: Provide Timely Notifications                    | Notification Management                                                          |
| BG-07: Support Business Monitoring and Decision Making | Basic Reporting                                                                  |
| BG-08: Ensure Data Security                            | Authentication, Authorization                                                    |
| BG-09: Ensure Access Control                           | Authorization, Role Management                                                   |
| BG-10: Enable Future System Expansion                  | Modular Architecture, Integration Design                                         |

---

# 5.3. In Scope – MVP Modules

Trong phạm vi MVP, các module sau sẽ được phát triển.

| ID   | Module                              | Mục đích                                    |
| ---- | ----------------------------------- | ------------------------------------------- |
| M-01 | Authentication & Account Management | Quản lý tài khoản và xác thực người dùng    |
| M-02 | Customer Management                 | Quản lý thông tin khách hàng                |
| M-03 | Driver Management                   | Quản lý thông tin và trạng thái tài xế      |
| M-04 | Vehicle Management                  | Quản lý phương tiện của tài xế              |
| M-05 | Booking Management                  | Tiếp nhận và quản lý yêu cầu đặt xe         |
| M-06 | Driver Matching & Assignment        | Tìm và phân công tài xế phù hợp             |
| M-07 | Trip Management                     | Quản lý quá trình thực hiện chuyến đi       |
| M-08 | Fare Calculation                    | Tính cước chuyến đi                         |
| M-09 | Payment Management                  | Quản lý thanh toán                          |
| M-10 | Notification Management             | Gửi thông báo cho khách hàng và tài xế      |
| M-11 | Operation Management                | Hỗ trợ nhân viên vận hành quản lý hệ thống  |
| M-12 | Authorization & Access Control      | Phân quyền người dùng và kiểm soát truy cập |

---

## 5.4. Module Priority

Do giới hạn thời gian 7 tuần, các module được phân loại theo mức độ ưu tiên.

### P0 – Must Have

Các module bắt buộc phải có để hệ thống có thể vận hành:

| Module                              | Business Goal hỗ trợ |
| ----------------------------------- | -------------------- |
| Authentication & Account Management | BG-08, BG-09         |
| Driver Management                   | BG-01, BG-04         |
| Booking Management                  | BG-01, BG-02         |
| Driver Matching & Assignment        | BG-01                |
| Trip Management                     | BG-02                |
| Fare Calculation                    | BG-03                |
| Payment Management                  | BG-03                |
| Basic Authorization                 | BG-08, BG-09         |

---

### P1 – Should Have

Các module quan trọng nhưng có thể triển khai ở mức cơ bản trong MVP:

| Module                  | Business Goal hỗ trợ |
| ----------------------- | -------------------- |
| Customer Management     | BG-04                |
| Vehicle Management      | BG-04                |
| Notification Management | BG-06                |
| Operation Management    | BG-04                |
| Location Tracking       | BG-02                |

---

### P2 – Could Have

Các module có giá trị bổ sung nhưng không ảnh hưởng trực tiếp đến khả năng vận hành cơ bản của hệ thống:

| Module                        | Business Goal hỗ trợ    |
| ----------------------------- | ----------------------- |
| Rating & Review               | Improve Service Quality |
| Basic Reporting               | BG-07                   |
| Driver Performance Statistics | BG-07                   |
| Audit Log                     | BG-08                   |

---

# 5.5. Module Scope Diagram

```mermaid
flowchart TB

    CAB[CAB System]

    CAB --> CORE[Core Modules - P0]
    CAB --> HIGH[Important Modules - P1]
    CAB --> OPTIONAL[Optional Modules - P2]

    CORE --> A[Authentication & Account]
    CORE --> B[Driver Management]
    CORE --> C[Booking Management]
    CORE --> D[Driver Matching]
    CORE --> E[Trip Management]
    CORE --> F[Fare Calculation]
    CORE --> G[Payment Management]
    CORE --> H[Authorization]

    HIGH --> I[Customer Management]
    HIGH --> J[Vehicle Management]
    HIGH --> K[Notification]
    HIGH --> L[Operation Management]
    HIGH --> M[Location Tracking]

    OPTIONAL --> N[Rating & Review]
    OPTIONAL --> O[Basic Reporting]
    OPTIONAL --> P[Driver Statistics]
    OPTIONAL --> Q[Audit Log]
```

---

# 5.6. Core Business Flow

Các module trong MVP tập trung hỗ trợ quy trình nghiệp vụ chính:

```mermaid
flowchart LR

    A[Customer Login]
    --> B[Create Booking]
    --> C[Driver Matching]
    --> D[Driver Assignment]
    --> E[Trip Execution]
    --> F[Fare Calculation]
    --> G[Payment]
    --> H[Trip Completed]
```

Các module hỗ trợ:

```mermaid
flowchart TB

    A[Authentication]
    B[Driver Management]
    C[Vehicle Management]
    D[Notification]
    E[Authorization]

    A --> CORE[Core Business Flow]
    B --> CORE
    C --> CORE
    D --> CORE
    E --> CORE
```

---

# 5.7. Out of Scope

Các chức năng sau không thuộc phạm vi MVP do giới hạn thời gian và nguồn lực:

### Advanced Features

* AI Driver Matching.
* Machine Learning.
* Predictive Analytics.
* Advanced Driver Ranking.
* Dynamic Pricing.
* Demand Forecasting.

### Customer Experience Features

* Loyalty Program.
* Membership.
* Voucher và Promotion.
* Referral Program.
* Subscription.

### Advanced Booking

* Scheduled Booking.
* Recurring Booking.
* Multi-stop Trip.
* Ride Sharing.

### Advanced Analytics

* Business Intelligence Dashboard.
* Advanced Analytics.
* Real-time Analytics.
* Predictive Reporting.

Các chức năng trên có thể được xem xét phát triển trong các giai đoạn tiếp theo.

---

# 5.8. Scope Boundary

```mermaid
flowchart TB

    subgraph MVP["MVP Scope - 7 Weeks"]

        A[Authentication]
        B[Booking]
        C[Driver Management]
        D[Driver Matching]
        E[Trip Management]
        F[Fare Calculation]
        G[Payment]
        H[Notification]
        I[Basic Operation Management]

    end

    subgraph FUTURE["Future Scope"]

        J[AI Matching]
        K[Dynamic Pricing]
        L[Loyalty Program]
        M[Advanced Analytics]
        N[Promotion]
        O[Ride Sharing]

    end

    MVP --> FUTURE
```

---

# 5.9. Scope Summary

Dự án CAB System trong giai đoạn MVP tập trung vào các chức năng cần thiết để vận hành một hệ thống đặt xe cơ bản.

### Core Modules

* Authentication & Account Management
* Driver Management
* Booking Management
* Driver Matching & Assignment
* Trip Management
* Fare Calculation
* Payment Management

### Supporting Modules

* Vehicle Management
* Notification Management
* Operation Management
* Authorization & Access Control

### Future Modules

* Rating & Review
* Advanced Reporting
* AI Driver Matching
* Dynamic Pricing
* Loyalty Program
* Advanced Analytics
# 6. Business Requirements

## 6.1. Overview

Dựa trên các Business Goals và phạm vi MVP đã xác định, CAB System cần đáp ứng các Business Requirements sau.

Các Business Requirements tập trung vào những nhu cầu nghiệp vụ cốt lõi của doanh nghiệp trong phạm vi dự án 7 tuần.

---

## 6.2. Business Requirements by Module

### BR-01. Account & Authentication

Hệ thống cần hỗ trợ quản lý tài khoản và xác thực người dùng để đảm bảo chỉ những người dùng hợp lệ mới có thể sử dụng các chức năng tương ứng.

**Business Requirements:**

* BR-01.01: Hệ thống phải hỗ trợ các nhóm người dùng chính gồm Customer, Driver và Operator.
* BR-01.02: Người dùng phải được xác thực trước khi sử dụng các chức năng yêu cầu tài khoản.
* BR-01.03: Mỗi nhóm người dùng chỉ được truy cập các chức năng phù hợp với vai trò của mình.
* BR-01.04: Hệ thống phải cho phép người dùng quản lý thông tin tài khoản cơ bản.

---

### BR-02. Driver Management

Hệ thống cần hỗ trợ doanh nghiệp quản lý thông tin và trạng thái hoạt động của tài xế.

**Business Requirements:**

* BR-02.01: Hệ thống phải lưu trữ thông tin cơ bản của tài xế.
* BR-02.02: Hệ thống phải quản lý thông tin phương tiện của tài xế.
* BR-02.03: Tài xế phải có trạng thái hoạt động để xác định khả năng nhận chuyến.
* BR-02.04: Chỉ tài xế đủ điều kiện và đang sẵn sàng mới được tham gia quá trình nhận chuyến.
* BR-02.05: Một tài xế không được thực hiện nhiều chuyến tại cùng một thời điểm.

---

### BR-03. Booking Management

Hệ thống cần cho phép khách hàng tạo và quản lý yêu cầu đặt xe.

**Business Requirements:**

* BR-03.01: Khách hàng phải cung cấp điểm đón và điểm đến khi tạo yêu cầu đặt xe.
* BR-03.02: Khách hàng phải lựa chọn loại dịch vụ hoặc loại xe phù hợp.
* BR-03.03: Mỗi yêu cầu đặt xe phải được hệ thống quản lý theo trạng thái.
* BR-03.04: Khách hàng phải có khả năng theo dõi trạng thái yêu cầu đặt xe.
* BR-03.05: Hệ thống phải thông báo cho khách hàng khi có thay đổi quan trọng liên quan đến yêu cầu đặt xe.

---

### BR-04. Driver Matching & Assignment

Hệ thống cần tự động hỗ trợ quá trình tìm kiếm và phân công tài xế phù hợp cho khách hàng.

**Business Requirements:**

* BR-04.01: Hệ thống phải xác định các tài xế phù hợp với yêu cầu đặt xe.
* BR-04.02: Việc lựa chọn tài xế phải dựa trên trạng thái hoạt động và vị trí của tài xế.
* BR-04.03: Hệ thống nên ưu tiên tài xế phù hợp và gần khách hàng.
* BR-04.04: Tài xế phải có quyền chấp nhận hoặc từ chối yêu cầu chuyến đi.
* BR-04.05: Nếu tài xế từ chối hoặc không phản hồi, hệ thống phải tiếp tục tìm tài xế khác.
* BR-04.06: Khách hàng không phải tạo lại yêu cầu khi hệ thống tìm tài xế khác.
* BR-04.07: Nếu không tìm được tài xế phù hợp, khách hàng phải được thông báo.

---

### BR-05. Trip Management

Hệ thống cần quản lý toàn bộ vòng đời của một chuyến đi.

**Business Requirements:**

* BR-05.01: Mỗi chuyến đi phải được quản lý theo các trạng thái rõ ràng.
* BR-05.02: Tài xế phải cập nhật trạng thái trong quá trình thực hiện chuyến đi.
* BR-05.03: Khách hàng phải có khả năng theo dõi trạng thái hiện tại của chuyến đi.
* BR-05.04: Bộ phận vận hành phải có khả năng theo dõi các chuyến đi đang diễn ra.
* BR-05.05: Hệ thống phải lưu lịch sử chuyến đi sau khi hoàn thành.

---

### BR-06. Fare Calculation

Hệ thống cần hỗ trợ xác định chi phí của chuyến đi.

**Business Requirements:**

* BR-06.01: Hệ thống phải xác định giá cước sau khi chuyến đi hoàn thành.
* BR-06.02: Giá cước phải dựa trên loại dịch vụ và thông tin của chuyến đi.
* BR-06.03: Thông tin giá cước phải được lưu cùng với chuyến đi.
* BR-06.04: Khách hàng phải biết số tiền cần thanh toán.

> Công thức tính giá cước chi tiết sẽ được xác định trong quá trình làm rõ yêu cầu.

---

### BR-07. Payment Management

Hệ thống cần hỗ trợ quản lý thanh toán cho các chuyến đi.

**Business Requirements:**

* BR-07.01: Hệ thống phải hỗ trợ thanh toán bằng tiền mặt.
* BR-07.02: Hệ thống phải hỗ trợ phương thức thanh toán điện tử.
* BR-07.03: Thanh toán điện tử phải được xử lý thông qua nhà cung cấp thanh toán bên ngoài.
* BR-07.04: Hệ thống không được lưu trực tiếp thông tin thanh toán nhạy cảm của khách hàng.
* BR-07.05: Kết quả thanh toán phải được cập nhật vào chuyến đi tương ứng.
* BR-07.06: Khi thanh toán thất bại, khách hàng phải được thông báo và xử lý theo chính sách của doanh nghiệp.

---

### BR-08. Notification Management

Hệ thống cần cung cấp thông báo về các sự kiện quan trọng trong quá trình đặt và thực hiện chuyến đi.

**Business Requirements:**

* BR-08.01: Khách hàng phải nhận được thông báo khi yêu cầu đặt xe được tiếp nhận.
* BR-08.02: Tài xế phải nhận được thông báo khi có yêu cầu chuyến đi phù hợp.
* BR-08.03: Khách hàng phải được thông báo khi tài xế nhận chuyến.
* BR-08.04: Khách hàng phải được thông báo khi tài xế đến điểm đón.
* BR-08.05: Các bên liên quan phải được thông báo khi chuyến đi hoàn thành.
* BR-08.06: Khách hàng phải được thông báo về kết quả thanh toán.

---

### BR-09. Operation Management

Hệ thống cần hỗ trợ bộ phận vận hành quản lý các hoạt động chính của doanh nghiệp.

**Business Requirements:**

* BR-09.01: Nhân viên vận hành phải có khả năng quản lý thông tin khách hàng.
* BR-09.02: Nhân viên vận hành phải có khả năng quản lý tài xế.
* BR-09.03: Nhân viên vận hành phải có khả năng quản lý thông tin phương tiện.
* BR-09.04: Nhân viên vận hành phải có khả năng theo dõi các chuyến đi đang diễn ra.
* BR-09.05: Nhân viên vận hành phải có khả năng tra cứu lịch sử chuyến đi.
* BR-09.06: Nhân viên vận hành phải có khả năng hỗ trợ xử lý các trường hợp phát sinh.

---

### BR-10. Authorization & Access Control

Hệ thống cần kiểm soát quyền truy cập của người dùng.

**Business Requirements:**

* BR-10.01: Hệ thống phải phân quyền dựa trên vai trò của người dùng.
* BR-10.02: Người dùng chỉ được truy cập các chức năng phù hợp với vai trò.
* BR-10.03: Các chức năng quản trị nhạy cảm phải được giới hạn quyền truy cập.
* BR-10.04: Các thao tác quan trọng cần có khả năng truy vết khi cần thiết.

---

## 6.3. Business Requirements Summary

| ID    | Business Requirement                   | Related Module           |
| ----- | -------------------------------------- | ------------------------ |
| BR-01 | Quản lý và xác thực người dùng         | Account & Authentication |
| BR-02 | Quản lý tài xế và trạng thái hoạt động | Driver Management        |
| BR-03 | Quản lý yêu cầu đặt xe                 | Booking Management       |
| BR-04 | Tự động tìm và phân công tài xế        | Driver Matching          |
| BR-05 | Quản lý vòng đời chuyến đi             | Trip Management          |
| BR-06 | Tính giá cước chuyến đi                | Fare Calculation         |
| BR-07 | Quản lý thanh toán                     | Payment Management       |
| BR-08 | Quản lý thông báo                      | Notification Management  |
| BR-09 | Hỗ trợ hoạt động vận hành              | Operation Management     |
| BR-10 | Phân quyền và kiểm soát truy cập       | Authorization            |

---

## 6.4. Business Requirement Relationship

```mermaid
flowchart TB

    BG[Business Goals]

    BG --> M1[Account & Authentication]
    BG --> M2[Driver Management]
    BG --> M3[Booking Management]
    BG --> M4[Driver Matching]
    BG --> M5[Trip Management]
    BG --> M6[Fare Calculation]
    BG --> M7[Payment Management]
    BG --> M8[Notification Management]
    BG --> M9[Operation Management]

    M1 --> BR1[BR-01]
    M2 --> BR2[BR-02]
    M3 --> BR3[BR-03]
    M4 --> BR4[BR-04]
    M5 --> BR5[BR-05]
    M6 --> BR6[BR-06]
    M7 --> BR7[BR-07]
    M8 --> BR8[BR-08]
    M9 --> BR9[BR-09]
```
# 7. Business Process Modeling

## 7.1. Overview

Dựa trên các Business Requirements đã xác định, CAB System có các quy trình nghiệp vụ chính sau:

| ID    | Business Process                     | Related Business Requirements |
| ----- | ------------------------------------ | ----------------------------- |
| BP-01 | User & Driver Management             | BR-01, BR-02, BR-10           |
| BP-02 | Ride Booking Process                 | BR-03                         |
| BP-03 | Driver Matching & Assignment Process | BR-04                         |
| BP-04 | Trip Execution Process               | BR-05                         |
| BP-05 | Fare Calculation & Payment Process   | BR-06, BR-07                  |
| BP-06 | Notification Process                 | BR-08                         |
| BP-07 | Operation Management Process         | BR-09                         |

Các quy trình trên liên kết với nhau để tạo thành quy trình nghiệp vụ tổng thể của hệ thống CAB.

---

# 7.2. Overall Business Process

Quy trình nghiệp vụ tổng thể của hệ thống bắt đầu từ khi khách hàng tạo yêu cầu đặt xe và kết thúc khi chuyến đi được thanh toán và hoàn thành.

```mermaid
flowchart LR

    A([Start])

    A --> B[Customer Login]

    B --> C[Create Booking]

    C --> D[Find Suitable Driver]

    D --> E{Driver Found?}

    E -- No --> F[Notify Customer]
    F --> Z([End])

    E -- Yes --> G[Send Trip Request]

    G --> H{Driver Accept?}

    H -- No --> D

    H -- Yes --> I[Assign Driver]

    I --> J[Driver Arrives]

    J --> K[Passenger Picked Up]

    K --> L[Trip In Progress]

    L --> M[Trip Completed]

    M --> N[Calculate Fare]

    N --> O[Payment]

    O --> P{Payment Successful?}

    P -- No --> Q[Notify Payment Failure]
    Q --> O

    P -- Yes --> R[Notify Payment Success]

    R --> S([End])
```

---

# 7.3. BP-01: User & Driver Management Process

**Objective:**
Quản lý tài khoản, thông tin người dùng và trạng thái hoạt động của tài xế.

**Actors:**

* Customer
* Driver
* Operator
* Administrator

### Process Flow

```mermaid
flowchart TD

    A([Start])

    A --> B{User Type}

    B -- Customer --> C[Register Account]

    B -- Driver --> D{Registration Method}

    D -- Self Registration --> E[Register Driver Account]

    D -- Created by Operator --> F[Operator Creates Driver Account]

    C --> G[Authenticate User]

    E --> G
    F --> G

    G --> H[Access System]

    H --> I{Driver?}

    I -- No --> Z([End])

    I -- Yes --> J[Update Driver Profile]

    J --> K[Update Vehicle Information]

    K --> L[Update Working Status]

    L --> Z
```

### Business Rules Applied

* User phải được xác thực trước khi sử dụng hệ thống.
* Driver phải có trạng thái hoạt động.
* Chỉ Driver đang sẵn sàng mới có thể nhận chuyến.
* Quyền truy cập phụ thuộc vào vai trò người dùng.

---

# 7.4. BP-02: Ride Booking Process

**Objective:**
Cho phép khách hàng tạo và theo dõi yêu cầu đặt xe.

**Primary Actor:** Customer

### Process Flow

```mermaid
flowchart TD

    A([Start])

    A --> B[Login]

    B --> C[Enter Pickup Location]

    C --> D[Enter Destination]

    D --> E[Select Vehicle Type]

    E --> F{Valid Information?}

    F -- No --> G[Display Error]

    G --> C

    F -- Yes --> H[Create Booking]

    H --> I[Booking Request Created]

    I --> J[Update Booking Status]

    J --> K[Notify Customer]

    K --> L([End])
```

### Business Rules Applied

* Customer phải cung cấp điểm đón.
* Customer phải cung cấp điểm đến.
* Customer phải chọn loại xe.
* Booking phải được quản lý theo trạng thái.

---

# 7.5. BP-03: Driver Matching & Assignment Process

**Objective:**
Tự động tìm và phân công Driver phù hợp cho Booking.

**Actors:**

* System
* Driver
* Customer

### Process Flow

```mermaid
flowchart TD

    A([Booking Created])

    A --> B[Get Available Drivers]

    B --> C[Check Driver Status]

    C --> D[Check Driver Location]

    D --> E[Select Suitable Driver]

    E --> F{Driver Available?}

    F -- No --> G[Notify Customer No Driver Found]

    G --> Z([End])

    F -- Yes --> H[Send Trip Request to Driver]

    H --> I{Driver Response}

    I -- Accept --> J[Assign Driver]

    J --> K[Update Booking Status]

    K --> L[Notify Customer]

    L --> Z

    I -- Reject --> M[Find Another Driver]

    M --> B

    I -- No Response --> M
```

### Business Rules Applied

* Driver phải ở trạng thái Available.
* Driver được ưu tiên dựa trên vị trí và tiêu chí vận hành.
* Driver có quyền Accept hoặc Reject.
* Khi Driver từ chối hoặc không phản hồi, hệ thống tiếp tục tìm Driver khác.
* Customer không cần tạo lại Booking.
* Nếu không tìm được Driver, Customer phải được thông báo.

---

# 7.6. BP-04: Trip Execution Process

**Objective:**
Quản lý quá trình thực hiện chuyến đi từ khi Driver được phân công đến khi chuyến đi hoàn thành.

**Actors:**

* Driver
* Customer
* Operator

### Process Flow

```mermaid
stateDiagram-v2

    [*] --> DriverAssigned

    DriverAssigned --> DriverArriving

    DriverArriving --> DriverArrived

    DriverArrived --> PassengerPickedUp

    PassengerPickedUp --> InProgress

    InProgress --> Completed

    Completed --> [*]
```

### Trip Status Flow

```text
Driver Assigned
      ↓
Driver Arriving
      ↓
Driver Arrived
      ↓
Passenger Picked Up
      ↓
Trip In Progress
      ↓
Trip Completed
```

### Business Rules Applied

* Mỗi chuyến đi phải có trạng thái rõ ràng.
* Driver chịu trách nhiệm cập nhật trạng thái chuyến.
* Customer có thể theo dõi trạng thái chuyến.
* Operator có thể theo dõi các chuyến đang diễn ra.
* Lịch sử chuyến đi được lưu sau khi hoàn thành.

---

# 7.7. BP-05: Fare Calculation & Payment Process

**Objective:**
Tính cước và xử lý thanh toán sau khi chuyến đi hoàn thành.

**Actors:**

* System
* Customer
* Payment Provider

### Process Flow

```mermaid
flowchart TD

    A([Trip Completed])

    A --> B[Collect Trip Information]

    B --> C[Calculate Fare]

    C --> D[Display Fare]

    D --> E{Payment Method}

    E -- Cash --> F[Confirm Cash Payment]

    E -- Electronic Payment --> G[Send Payment Request]

    G --> H[Payment Provider Processes Transaction]

    H --> I{Payment Successful?}

    I -- Yes --> J[Update Payment Status]

    I -- No --> K[Notify Payment Failure]

    K --> L{Retry Payment?}

    L -- Yes --> G

    L -- No --> M[Mark Payment Pending]

    F --> J

    J --> N[Notify Customer]

    N --> Z([End])

    M --> Z
```

### Business Rules Applied

* Giá cước được xác định dựa trên thông tin chuyến đi.
* Hệ thống hỗ trợ Cash và Electronic Payment.
* Thông tin thanh toán nhạy cảm không được lưu trực tiếp.
* Payment điện tử được xử lý bởi Payment Provider.
* Payment Result phải được cập nhật vào chuyến đi.

---

# 7.8. BP-06: Notification Process

**Objective:**
Thông báo cho Customer và Driver về các sự kiện quan trọng.

### Notification Events

| Event            | Recipient        |
| ---------------- | ---------------- |
| Booking Created  | Customer         |
| New Trip Request | Driver           |
| Driver Assigned  | Customer         |
| Driver Arrived   | Customer         |
| Trip Completed   | Customer, Driver |
| Payment Success  | Customer         |
| Payment Failed   | Customer         |
| No Driver Found  | Customer         |

### Process Flow

```mermaid
flowchart LR

    A[Business Event]

    A --> B{Event Type}

    B --> C[Booking Event]
    B --> D[Driver Matching Event]
    B --> E[Trip Event]
    B --> F[Payment Event]

    C --> G[Create Notification]
    D --> G
    E --> G
    F --> G

    G --> H[Determine Recipient]

    H --> I[Send Notification]

    I --> J([End])
```

---

# 7.9. BP-07: Operation Management Process

**Objective:**
Hỗ trợ nhân viên vận hành theo dõi và quản lý hoạt động của hệ thống.

**Primary Actor:** Operator

### Process Flow

```mermaid
flowchart TD

    A([Operator Login])

    A --> B{Select Function}

    B --> C[Manage Customers]

    B --> D[Manage Drivers]

    B --> E[Manage Vehicles]

    B --> F[Monitor Active Trips]

    B --> G[Search Trip History]

    B --> H[Handle Operational Issues]

    C --> I[Update Information]

    D --> I

    E --> I

    F --> I

    G --> I

    H --> I

    I --> Z([End])
```

### Business Rules Applied

* Operator chỉ được truy cập các chức năng được phân quyền.
* Các thao tác nhạy cảm phải được kiểm soát quyền truy cập.
* Thông tin chuyến đi phải có khả năng tra cứu.
* Các trường hợp lỗi phải được hỗ trợ xử lý.

---

# 7.10. Business Process Relationship

```mermaid
flowchart LR

    BP1[BP-01<br/>User & Driver Management]

    BP2[BP-02<br/>Ride Booking]

    BP3[BP-03<br/>Driver Matching]

    BP4[BP-04<br/>Trip Execution]

    BP5[BP-05<br/>Fare & Payment]

    BP6[BP-06<br/>Notification]

    BP7[BP-07<br/>Operation Management]

    BP1 --> BP2

    BP2 --> BP3

    BP3 --> BP4

    BP4 --> BP5

    BP2 -.-> BP6
    BP3 -.-> BP6
    BP4 -.-> BP6
    BP5 -.-> BP6

    BP7 -.-> BP1
    BP7 -.-> BP2
    BP7 -.-> BP3
    BP7 -.-> BP4
    BP7 -.-> BP5
```

---

# 7.11. Business Process Summary

| ID    | Process                  | Input                | Output             |
| ----- | ------------------------ | -------------------- | ------------------ |
| BP-01 | User & Driver Management | User Information     | Valid User Account |
| BP-02 | Ride Booking             | Pickup & Destination | Booking Request    |
| BP-03 | Driver Matching          | Booking Request      | Assigned Driver    |
| BP-04 | Trip Execution           | Assigned Driver      | Completed Trip     |
| BP-05 | Fare & Payment           | Completed Trip       | Payment Result     |
| BP-06 | Notification             | Business Event       | Notification       |
| BP-07 | Operation Management     | System Data          | Operational Action |

````

## Lưu ý về cấu trúc bài của bạn

Mình thấy thứ tự hiện tại khá logic:

```text
1. Introduction
        ↓
2. Stakeholder Analysis
        ↓
3. Customer Requirements
        ↓
4. Business Goals
        ↓
5. Project Scope & Module Identification
        ↓
6. Business Requirements
        ↓
7. Business Process Modeling
````

Sau Business Process Modeling thì nên làm tiếp:

```text
8. Functional Requirements
        ↓
9. Non-Functional Requirements
        ↓
10. Business Rules
        ↓
11. Use Case Modeling
```

### Một lưu ý quan trọng

Trong bài này, **BP-02 → BP-05 là các Business Process quan trọng nhất**, vì chúng tạo thành core flow:

```text
Create Booking
      ↓
Find Driver
      ↓
Assign Driver
      ↓
Execute Trip
      ↓
Calculate Fare
      ↓
Payment
```
# 8. System Requirements and Functional Decomposition

## 8.2. Business Process to System Requirements Mapping

| Business Process                   | System Requirements |
| ---------------------------------- | ------------------- |
| BP-01 User & Driver Management     | SR-01 → SR-09       |
| BP-02 Ride Booking                 | SR-10 → SR-16       |
| BP-03 Driver Matching & Assignment | SR-17 → SR-24       |
| BP-04 Trip Execution               | SR-25 → SR-31       |
| BP-05 Fare Calculation & Payment   | SR-32 → SR-40       |
| BP-06 Notification                 | SR-41 → SR-45       |
| BP-07 Operation Management         | SR-46 → SR-52       |

---

# 8.3. SR-01: User & Account Management

**Related Business Process:** BP-01
**Related Business Requirement:** BR-01

Hệ thống phải hỗ trợ quản lý tài khoản và xác thực người dùng.

| ID       | System Requirement                                                      |
| -------- | ----------------------------------------------------------------------- |
| SR-01.01 | Hệ thống phải cho phép Customer đăng ký tài khoản.                      |
| SR-01.02 | Hệ thống phải cho phép Driver đăng ký hoặc được Operator tạo tài khoản. |
| SR-01.03 | Hệ thống phải xác thực người dùng khi đăng nhập.                        |
| SR-01.04 | Hệ thống phải cho phép người dùng đăng xuất.                            |
| SR-01.05 | Hệ thống phải cho phép người dùng xem thông tin tài khoản.              |
| SR-01.06 | Hệ thống phải cho phép người dùng cập nhật thông tin cá nhân.           |
| SR-01.07 | Hệ thống phải xác định vai trò của người dùng sau khi đăng nhập.        |
| SR-01.08 | Hệ thống phải kiểm soát quyền truy cập theo vai trò.                    |
| SR-01.09 | Hệ thống phải quản lý trạng thái hoạt động của tài khoản.               |


# 8.4. SR-02: Driver Management

**Related Business Process:** BP-01
**Related Business Requirement:** BR-02

Hệ thống phải hỗ trợ quản lý thông tin và trạng thái hoạt động của Driver.

| ID       | System Requirement                                                   |
| -------- | -------------------------------------------------------------------- |
| SR-02.01 | Hệ thống phải lưu thông tin cơ bản của Driver.                       |
| SR-02.02 | Hệ thống phải cho phép Driver cập nhật hồ sơ cá nhân.                |
| SR-02.03 | Hệ thống phải quản lý thông tin phương tiện của Driver.              |
| SR-02.04 | Hệ thống phải cho phép Driver cập nhật trạng thái hoạt động.         |
| SR-02.05 | Hệ thống phải xác định Driver có đủ điều kiện nhận chuyến hay không. |
| SR-02.06 | Hệ thống phải xác định Driver đang thực hiện chuyến đi.              |
| SR-02.07 | Hệ thống phải ngăn Driver nhận nhiều chuyến cùng lúc.                |



# 8.5. SR-03: Ride Booking Management

**Related Business Process:** BP-02
**Related Business Requirement:** BR-03

Hệ thống phải hỗ trợ Customer tạo và quản lý yêu cầu đặt xe.

| ID       | System Requirement                                             |
| -------- | -------------------------------------------------------------- |
| SR-03.01 | Hệ thống phải cho phép Customer nhập điểm đón.                 |
| SR-03.02 | Hệ thống phải cho phép Customer nhập điểm đến.                 |
| SR-03.03 | Hệ thống phải cho phép Customer lựa chọn loại xe hoặc dịch vụ. |
| SR-03.04 | Hệ thống phải kiểm tra thông tin đặt xe trước khi tạo Booking. |
| SR-03.05 | Hệ thống phải tạo Booking khi thông tin hợp lệ.                |
| SR-03.06 | Hệ thống phải gán mã định danh cho mỗi Booking.                |
| SR-03.07 | Hệ thống phải quản lý trạng thái Booking.                      |
| SR-03.08 | Hệ thống phải cho phép Customer xem trạng thái Booking.        |



# 8.6. SR-04: Driver Matching & Assignment

**Related Business Process:** BP-03
**Related Business Requirement:** BR-04

Hệ thống phải tự động tìm kiếm và phân công Driver phù hợp cho Booking.

| ID       | System Requirement                                                             |
| -------- | ------------------------------------------------------------------------------ |
| SR-04.01 | Hệ thống phải xác định danh sách Driver đang sẵn sàng.                         |
| SR-04.02 | Hệ thống phải kiểm tra trạng thái hoạt động của Driver.                        |
| SR-04.03 | Hệ thống phải lấy vị trí hiện tại của Driver.                                  |
| SR-04.04 | Hệ thống phải xác định Driver phù hợp với Booking.                             |
| SR-04.05 | Hệ thống phải ưu tiên Driver theo vị trí hoặc tiêu chí vận hành.               |
| SR-04.06 | Hệ thống phải gửi yêu cầu chuyến đi đến Driver.                                |
| SR-04.07 | Hệ thống phải ghi nhận phản hồi Accept hoặc Reject của Driver.                 |
| SR-04.08 | Hệ thống phải phân công Driver khi Driver chấp nhận chuyến.                    |
| SR-04.09 | Hệ thống phải tiếp tục tìm Driver khác khi Driver từ chối hoặc không phản hồi. |
| SR-04.10 | Hệ thống phải thông báo Customer khi không tìm được Driver.                    |


# 8.7. SR-05: Trip Management

**Related Business Process:** BP-04
**Related Business Requirement:** BR-05

Hệ thống phải quản lý toàn bộ vòng đời của chuyến đi.

| ID       | System Requirement                                                      |
| -------- | ----------------------------------------------------------------------- |
| SR-05.01 | Hệ thống phải tạo Trip sau khi Driver được phân công.                   |
| SR-05.02 | Hệ thống phải liên kết Trip với Customer và Driver.                     |
| SR-05.03 | Hệ thống phải quản lý trạng thái Trip.                                  |
| SR-05.04 | Hệ thống phải cho phép Driver cập nhật trạng thái chuyến đi.            |
| SR-05.05 | Hệ thống phải cho phép Customer theo dõi trạng thái chuyến đi.          |
| SR-05.06 | Hệ thống phải lưu thời gian của các sự kiện quan trọng trong chuyến đi. |
| SR-05.07 | Hệ thống phải lưu lịch sử chuyến đi sau khi hoàn thành.                 |


# 8.8. SR-06: Fare Calculation

**Related Business Process:** BP-05
**Related Business Requirement:** BR-06

Hệ thống phải tính toán giá cước cho chuyến đi.

| ID       | System Requirement                                        |
| -------- | --------------------------------------------------------- |
| SR-06.01 | Hệ thống phải thu thập thông tin cần thiết để tính cước.  |
| SR-06.02 | Hệ thống phải xác định loại dịch vụ của chuyến đi.        |
| SR-06.03 | Hệ thống phải tính giá cước dựa trên thông tin chuyến đi. |
| SR-06.04 | Hệ thống phải lưu thông tin giá cước.                     |
| SR-06.05 | Hệ thống phải hiển thị giá cước cho Customer.             |

> Công thức tính giá cước sẽ được xác định chi tiết trong quá trình làm rõ yêu cầu.

---

# 8.9. SR-07: Payment Management

**Related Business Process:** BP-05
**Related Business Requirement:** BR-07

Hệ thống phải hỗ trợ xử lý thanh toán cho chuyến đi.

| ID       | System Requirement                                                 |
| -------- | ------------------------------------------------------------------ |
| SR-07.01 | Hệ thống phải cho phép Customer lựa chọn phương thức thanh toán.   |
| SR-07.02 | Hệ thống phải hỗ trợ thanh toán bằng tiền mặt.                     |
| SR-07.03 | Hệ thống phải hỗ trợ thanh toán điện tử.                           |
| SR-07.04 | Hệ thống phải gửi yêu cầu thanh toán điện tử đến Payment Provider. |
| SR-07.05 | Hệ thống phải nhận kết quả thanh toán từ Payment Provider.         |
| SR-07.06 | Hệ thống phải cập nhật trạng thái thanh toán.                      |
| SR-07.07 | Hệ thống phải xử lý trường hợp thanh toán thất bại.                |
| SR-07.08 | Hệ thống phải cho phép thực hiện lại thanh toán khi cần thiết.     |

# 8.10. SR-08: Notification Management

**Related Business Process:** BP-06
**Related Business Requirement:** BR-08

Hệ thống phải thông báo các sự kiện quan trọng cho người dùng.

| ID       | System Requirement                                             |
| -------- | -------------------------------------------------------------- |
| SR-08.01 | Hệ thống phải tạo thông báo khi Booking được tạo.              |
| SR-08.02 | Hệ thống phải thông báo Driver khi có yêu cầu chuyến đi mới.   |
| SR-08.03 | Hệ thống phải thông báo Customer khi Driver được phân công.    |
| SR-08.04 | Hệ thống phải thông báo Customer khi Driver đến điểm đón.      |
| SR-08.05 | Hệ thống phải thông báo các bên liên quan khi Trip hoàn thành. |
| SR-08.06 | Hệ thống phải thông báo kết quả thanh toán cho Customer.       |
| SR-08.07 | Hệ thống phải thông báo Customer khi không tìm được Driver.    |

# 9. Business Rules and Exceptions

## 9.1. Business Rules

| ID    | Business Rule                                                            |
| ----- | ------------------------------------------------------------------------ |
| BR-01 | Người dùng phải đăng nhập để sử dụng các chức năng yêu cầu tài khoản.    |
| BR-02 | Customer phải cung cấp điểm đón và điểm đến trước khi tạo Booking.       |
| BR-03 | Booking chỉ được tạo khi thông tin hợp lệ.                               |
| BR-04 | Chỉ Driver ở trạng thái Available mới được nhận chuyến.                  |
| BR-05 | Một Driver chỉ được thực hiện một chuyến tại một thời điểm.              |
| BR-06 | Driver có quyền chấp nhận hoặc từ chối yêu cầu chuyến đi.                |
| BR-07 | Khi Driver từ chối hoặc không phản hồi, hệ thống phải tìm Driver khác.   |
| BR-08 | Customer không cần tạo lại Booking khi Driver từ chối chuyến.            |
| BR-09 | Mỗi Trip phải được quản lý theo trạng thái xác định.                     |
| BR-10 | Giá cước được tính dựa trên thông tin thực tế của chuyến đi.             |
| BR-11 | Thanh toán điện tử phải được xử lý thông qua Payment Provider.           |
| BR-12 | Hệ thống không lưu trực tiếp thông tin thanh toán nhạy cảm.              |
| BR-13 | Kết quả thanh toán phải được cập nhật vào Trip tương ứng.                |
| BR-14 | Người dùng chỉ được truy cập các chức năng phù hợp với vai trò của mình. |
| BR-15 | Các sự kiện quan trọng phải được thông báo đến người dùng liên quan.     |

---

## 9.2. Driver Status Rules

| Status    | Description                                             |
| --------- | ------------------------------------------------------- |
| OFFLINE   | Driver không hoạt động trên hệ thống.                   |
| ONLINE    | Driver đang trực tuyến nhưng chưa sẵn sàng nhận chuyến. |
| AVAILABLE | Driver sẵn sàng nhận chuyến.                            |
| BUSY      | Driver đang thực hiện chuyến đi.                        |

### Status Transition

```mermaid
stateDiagram-v2
    OFFLINE --> ONLINE
    ONLINE --> AVAILABLE
    AVAILABLE --> BUSY
    BUSY --> AVAILABLE
    AVAILABLE --> OFFLINE
```

---

## 9.3. Trip Status Rules

```mermaid
stateDiagram-v2
    [*] --> Assigned
    Assigned --> Arriving
    Arriving --> Arrived
    Arrived --> PickedUp
    PickedUp --> InProgress
    InProgress --> Completed
    Completed --> [*]
```

| Status     | Description               |
| ---------- | ------------------------- |
| Assigned   | Driver đã được phân công. |
| Arriving   | Driver đang đến điểm đón. |
| Arrived    | Driver đã đến điểm đón.   |
| PickedUp   | Customer đã lên xe.       |
| InProgress | Chuyến đi đang diễn ra.   |
| Completed  | Chuyến đi đã hoàn thành.  |

---

# 9.4. Exceptions

## EX-01: Invalid Booking Information

**Condition:** Customer nhập thiếu hoặc sai thông tin đặt xe.

**System Handling:** Hệ thống thông báo lỗi và yêu cầu Customer nhập lại.

---

## EX-02: No Driver Available

**Condition:** Không tìm thấy Driver phù hợp.

**System Handling:** Cập nhật trạng thái Booking và thông báo cho Customer.

---

## EX-03: Driver Rejects Trip

**Condition:** Driver từ chối yêu cầu chuyến đi.

**System Handling:** Hệ thống tiếp tục tìm Driver khác.

---

## EX-04: Driver Does Not Respond

**Condition:** Driver không phản hồi trong thời gian quy định.

**System Handling:** Hệ thống chuyển sang tìm Driver khác.

---

## EX-05: Payment Failed

**Condition:** Giao dịch thanh toán điện tử thất bại.

**System Handling:** Thông báo Customer và cho phép thanh toán lại.

---

## EX-06: Payment Provider Unavailable

**Condition:** Payment Provider không phản hồi hoặc gặp sự cố.

**System Handling:** Ghi nhận giao dịch ở trạng thái Pending và thông báo cho Customer.

---

## EX-07: Unauthorized Access

**Condition:** User cố truy cập chức năng không thuộc quyền của mình.

**System Handling:** Từ chối truy cập và thông báo lỗi phù hợp.

---

## EX-08: Driver Becomes Unavailable

**Condition:** Driver đã được chọn nhưng chuyển sang trạng thái không thể nhận chuyến.

**System Handling:** Hệ thống tìm Driver khác.

---

## 9.5. Exception Summary

| ID    | Exception                    | System Handling         |
| ----- | ---------------------------- | ----------------------- |
| EX-01 | Invalid Booking Information  | Yêu cầu nhập lại        |
| EX-02 | No Driver Available          | Thông báo Customer      |
| EX-03 | Driver Rejects Trip          | Tìm Driver khác         |
| EX-04 | Driver No Response           | Tìm Driver khác         |
| EX-05 | Payment Failed               | Cho phép thanh toán lại |
| EX-06 | Payment Provider Unavailable | Pending Payment         |
| EX-07 | Unauthorized Access          | Từ chối truy cập        |
| EX-08 | Driver Unavailable           | Tìm Driver khác         |

# 10. Non-Functional Requirements

## 10.1. Overview

Non-Functional Requirements mô tả các yêu cầu về chất lượng và cách hệ thống hoạt động, không phải các chức năng nghiệp vụ cụ thể.

---

## 10.2. Performance

| ID     | Requirement                                                                       |
| ------ | --------------------------------------------------------------------------------- |
| NFR-01 | Hệ thống phải phản hồi các thao tác thông thường trong thời gian hợp lý.          |
| NFR-02 | Hệ thống phải xử lý việc tìm kiếm Driver mà không làm gián đoạn quá trình đặt xe. |
| NFR-03 | Hệ thống phải hỗ trợ nhiều người dùng truy cập đồng thời.                         |

---

## 10.3. Availability

| ID     | Requirement                                                                                              |
| ------ | -------------------------------------------------------------------------------------------------------- |
| NFR-04 | Hệ thống phải đảm bảo hoạt động ổn định trong quá trình vận hành.                                        |
| NFR-05 | Lỗi của một dịch vụ bên ngoài không được làm toàn bộ hệ thống ngừng hoạt động.                           |
| NFR-06 | Hệ thống phải có khả năng xử lý khi Payment Provider hoặc Notification Provider tạm thời không khả dụng. |

---

## 10.4. Security

| ID     | Requirement                                                                       |
| ------ | --------------------------------------------------------------------------------- |
| NFR-07 | Người dùng phải được xác thực trước khi truy cập các chức năng yêu cầu tài khoản. |
| NFR-08 | Hệ thống phải kiểm soát quyền truy cập dựa trên vai trò người dùng.               |
| NFR-09 | Dữ liệu cá nhân của Customer và Driver phải được bảo vệ.                          |
| NFR-10 | Hệ thống không được lưu trực tiếp thông tin thanh toán nhạy cảm.                  |
| NFR-11 | Thông tin trao đổi giữa người dùng và hệ thống phải được bảo vệ.                  |

---

## 10.5. Scalability

| ID     | Requirement                                                             |
| ------ | ----------------------------------------------------------------------- |
| NFR-12 | Hệ thống phải có khả năng mở rộng khi số lượng Customer và Driver tăng. |
| NFR-13 | Các module chính phải có khả năng mở rộng độc lập khi cần thiết.        |
| NFR-14 | Hệ thống phải hỗ trợ bổ sung các dịch vụ mới trong tương lai.           |

---

## 10.6. Reliability

| ID     | Requirement                                                         |
| ------ | ------------------------------------------------------------------- |
| NFR-15 | Dữ liệu Booking, Trip và Payment phải được lưu chính xác.           |
| NFR-16 | Hệ thống phải hạn chế việc tạo dữ liệu trùng lặp.                   |
| NFR-17 | Trạng thái Booking, Trip và Payment phải được đồng bộ và nhất quán. |

---

## 10.7. Usability

| ID     | Requirement                                                                                   |
| ------ | --------------------------------------------------------------------------------------------- |
| NFR-18 | Giao diện phải dễ sử dụng đối với Customer, Driver và Operator.                               |
| NFR-19 | Người dùng phải nhận được thông báo rõ ràng khi xảy ra lỗi.                                   |
| NFR-20 | Các thao tác chính như đặt xe và cập nhật trạng thái chuyến đi phải đơn giản và dễ thực hiện. |

---

## 10.8. Maintainability

| ID     | Requirement                                                          |
| ------ | -------------------------------------------------------------------- |
| NFR-21 | Hệ thống phải được thiết kế theo cấu trúc module để dễ bảo trì.      |
| NFR-22 | Các thay đổi ở một module nên hạn chế ảnh hưởng đến các module khác. |
| NFR-23 | Mã nguồn và tài liệu hệ thống phải dễ bảo trì và cập nhật.           |

---

## 10.9. Compatibility

| ID     | Requirement                                                                        |
| ------ | ---------------------------------------------------------------------------------- |
| NFR-24 | Hệ thống phải hỗ trợ các trình duyệt hiện đại.                                     |
| NFR-25 | Hệ thống phải có khả năng tích hợp với các dịch vụ bên ngoài như Payment Provider. |

---

## 10.10. Non-Functional Requirements Summary

| Category        | Related Requirements |
| --------------- | -------------------- |
| Performance     | NFR-01 → NFR-03      |
| Availability    | NFR-04 → NFR-06      |
| Security        | NFR-07 → NFR-11      |
| Scalability     | NFR-12 → NFR-14      |
| Reliability     | NFR-15 → NFR-17      |
| Usability       | NFR-18 → NFR-20      |
| Maintainability | NFR-21 → NFR-23      |
| Compatibility   | NFR-24 → NFR-25      |


# 11. Entity Identification and ERD Design

## 11.1. Entity Identification

Dựa trên Business Processes và System Requirements, các thực thể chính của CAB System được xác định như sau:

| ID   | Entity          | Description                         |
| ---- | --------------- | ----------------------------------- |
| E-01 | User            | Lưu thông tin tài khoản người dùng. |
| E-02 | Role            | Lưu thông tin vai trò người dùng.   |
| E-03 | Customer        | Lưu thông tin khách hàng.           |
| E-04 | Driver          | Lưu thông tin tài xế.               |
| E-05 | Vehicle         | Lưu thông tin phương tiện.          |
| E-06 | Booking         | Lưu yêu cầu đặt xe của khách hàng.  |
| E-07 | Trip            | Lưu thông tin chuyến đi.            |
| E-08 | Payment         | Lưu thông tin thanh toán.           |
| E-09 | Notification    | Lưu thông báo gửi đến người dùng.   |
| E-10 | Driver Location | Lưu vị trí của tài xế.              |

---

## 11.2. Entity Mapping from Business Processes

| Business Process               | Related Entities                         |
| ------------------------------ | ---------------------------------------- |
| BP-01 User & Driver Management | User, Role, Customer, Driver, Vehicle    |
| BP-02 Ride Booking             | Customer, Booking                        |
| BP-03 Driver Matching          | Booking, Driver, Driver Location         |
| BP-04 Trip Execution           | Booking, Driver, Customer, Trip          |
| BP-05 Fare & Payment           | Trip, Payment                            |
| BP-06 Notification             | User, Notification                       |
| BP-07 Operation Management     | Customer, Driver, Vehicle, Booking, Trip |

---

# 11.3. Core Entities

## User

Đại diện cho tài khoản đăng nhập của người dùng.

| Attribute  | Description          |
| ---------- | -------------------- |
| user_id    | Mã người dùng        |
| username   | Tên đăng nhập        |
| password   | Mật khẩu đã mã hóa   |
| full_name  | Họ tên               |
| phone      | Số điện thoại        |
| email      | Email                |
| role_id    | Vai trò              |
| status     | Trạng thái tài khoản |
| created_at | Thời gian tạo        |

---

## Role

Đại diện cho vai trò của người dùng trong hệ thống.

| Attribute   | Description |
| ----------- | ----------- |
| role_id     | Mã vai trò  |
| role_name   | Tên vai trò |
| description | Mô tả       |

Ví dụ:

```text
Customer
Driver
Operator
Administrator
```

---

## Customer

Lưu thông tin mở rộng của khách hàng.

| Attribute   | Description        |
| ----------- | ------------------ |
| customer_id | Mã khách hàng      |
| user_id     | Tài khoản liên kết |
| created_at  | Ngày tham gia      |

---

## Driver

Lưu thông tin nghiệp vụ của tài xế.

| Attribute      | Description          |
| -------------- | -------------------- |
| driver_id      | Mã tài xế            |
| user_id        | Tài khoản liên kết   |
| license_number | Số giấy phép lái xe  |
| driver_status  | Trạng thái hoạt động |
| rating         | Điểm đánh giá        |
| created_at     | Ngày tạo             |

---

## Vehicle

Lưu thông tin phương tiện.

| Attribute     | Description           |
| ------------- | --------------------- |
| vehicle_id    | Mã phương tiện        |
| driver_id     | Tài xế sở hữu/sử dụng |
| license_plate | Biển số xe            |
| vehicle_type  | Loại xe               |
| model         | Model xe              |
| status        | Trạng thái            |

---

## Booking

Lưu yêu cầu đặt xe.

| Attribute       | Description        |
| --------------- | ------------------ |
| booking_id      | Mã Booking         |
| customer_id     | Khách hàng đặt xe  |
| pickup_location | Điểm đón           |
| destination     | Điểm đến           |
| vehicle_type    | Loại xe yêu cầu    |
| booking_status  | Trạng thái Booking |
| created_at      | Thời gian tạo      |

---

## Trip

Lưu thông tin chuyến đi thực tế.

| Attribute       | Description          |
| --------------- | -------------------- |
| trip_id         | Mã chuyến đi         |
| booking_id      | Booking liên quan    |
| driver_id       | Driver thực hiện     |
| trip_status     | Trạng thái chuyến    |
| assigned_at     | Thời gian phân công  |
| started_at      | Thời gian bắt đầu    |
| completed_at    | Thời gian hoàn thành |
| actual_distance | Khoảng cách thực tế  |
| total_fare      | Tổng cước phí        |

---

## Payment

Lưu thông tin thanh toán.

| Attribute      | Description              |
| -------------- | ------------------------ |
| payment_id     | Mã thanh toán            |
| trip_id        | Chuyến đi                |
| amount         | Số tiền                  |
| payment_method | Phương thức thanh toán   |
| payment_status | Trạng thái               |
| transaction_id | Mã giao dịch từ Provider |
| paid_at        | Thời gian thanh toán     |

---

## Notification

Lưu thông báo hệ thống.

| Attribute         | Description                |
| ----------------- | -------------------------- |
| notification_id   | Mã thông báo               |
| user_id           | Người nhận                 |
| title             | Tiêu đề                    |
| content           | Nội dung                   |
| notification_type | Loại thông báo             |
| status            | Trạng thái đã đọc/chưa đọc |
| created_at        | Thời gian tạo              |

---

## Driver Location

Lưu vị trí của Driver phục vụ Driver Matching và Trip Tracking.

| Attribute   | Description        |
| ----------- | ------------------ |
| location_id | Mã vị trí          |
| driver_id   | Driver             |
| latitude    | Vĩ độ              |
| longitude   | Kinh độ            |
| updated_at  | Thời gian cập nhật |

---

# 11.4. Entity Relationships

Các mối quan hệ chính:

| Entity A | Relationship | Entity B        | Cardinality |
| -------- | ------------ | --------------- | ----------- |
| Role     | assigns      | User            | 1:N         |
| User     | represents   | Customer        | 1:0..1      |
| User     | represents   | Driver          | 1:0..1      |
| Driver   | owns/uses    | Vehicle         | 1:N         |
| Customer | creates      | Booking         | 1:N         |
| Booking  | generates    | Trip            | 1:0..1      |
| Driver   | performs     | Trip            | 1:N         |
| Trip     | has          | Payment         | 1:1         |
| User     | receives     | Notification    | 1:N         |
| Driver   | updates      | Driver Location | 1:N         |

---

# 11.5. Conceptual ERD

```mermaid
erDiagram

    ROLE ||--o{ USER : assigns

    USER ||--o| CUSTOMER : represents
    USER ||--o| DRIVER : represents

    DRIVER ||--o{ VEHICLE : uses

    CUSTOMER ||--o{ BOOKING : creates

    BOOKING ||--o| TRIP : generates

    DRIVER ||--o{ TRIP : performs

    TRIP ||--|| PAYMENT : has

    USER ||--o{ NOTIFICATION : receives

    DRIVER ||--o{ DRIVER_LOCATION : updates
```

---

# 11.6. Logical ERD

```mermaid
erDiagram

    ROLE {
        int role_id PK
        string role_name
        string description
    }

    USER {
        int user_id PK
        int role_id FK
        string username
        string password
        string full_name
        string phone
        string email
        string status
        datetime created_at
    }

    CUSTOMER {
        int customer_id PK
        int user_id FK
        datetime created_at
    }

    DRIVER {
        int driver_id PK
        int user_id FK
        string license_number
        string driver_status
        decimal rating
        datetime created_at
    }

    VEHICLE {
        int vehicle_id PK
        int driver_id FK
        string license_plate
        string vehicle_type
        string model
        string status
    }

    BOOKING {
        int booking_id PK
        int customer_id FK
        string pickup_location
        string destination
        string vehicle_type
        string booking_status
        datetime created_at
    }

    TRIP {
        int trip_id PK
        int booking_id FK
        int driver_id FK
        string trip_status
        datetime assigned_at
        datetime started_at
        datetime completed_at
        decimal actual_distance
        decimal total_fare
    }

    PAYMENT {
        int payment_id PK
        int trip_id FK
        decimal amount
        string payment_method
        string payment_status
        string transaction_id
        datetime paid_at
    }

    NOTIFICATION {
        int notification_id PK
        int user_id FK
        string title
        string content
        string notification_type
        string status
        datetime created_at
    }

    DRIVER_LOCATION {
        int location_id PK
        int driver_id FK
        decimal latitude
        decimal longitude
        datetime updated_at
    }

    ROLE ||--o{ USER : has

    USER ||--o| CUSTOMER : has
    USER ||--o| DRIVER : has

    DRIVER ||--o{ VEHICLE : owns

    CUSTOMER ||--o{ BOOKING : creates

    BOOKING ||--o| TRIP : generates

    DRIVER ||--o{ TRIP : performs

    TRIP ||--|| PAYMENT : has

    USER ||--o{ NOTIFICATION : receives

    DRIVER ||--o{ DRIVER_LOCATION : updates
```

---

# 11.7. Entity Relationship Summary

```text
ROLE
  │
  └── USER
        │
        ├── CUSTOMER
        │      │
        │      └── BOOKING
        │             │
        │             └── TRIP
        │
        ├── DRIVER
        │      ├── VEHICLE
        │      ├── DRIVER_LOCATION
        │      └── TRIP
        │
        └── NOTIFICATION

TRIP
  │
  └── PAYMENT
```

---

## 11.8. Core Data Flow

```mermaid
flowchart LR

    Customer --> Booking

    Booking --> DriverMatching

    DriverMatching --> Driver

    Driver --> Trip

    Booking --> Trip

    Trip --> FareCalculation

    FareCalculation --> Payment

    Trip --> Notification
```

---

## 11.9. Entity Traceability

| System Requirement            | Main Entities                            |
| ----------------------------- | ---------------------------------------- |
| SR-01 User Management         | User, Role                               |
| SR-02 Driver Management       | Driver, Vehicle                          |
| SR-03 Booking Management      | Customer, Booking                        |
| SR-04 Driver Matching         | Driver, Booking, Driver Location         |
| SR-05 Trip Management         | Trip, Booking, Driver                    |
| SR-06 Fare Calculation        | Trip                                     |
| SR-07 Payment Management      | Payment, Trip                            |
| SR-08 Notification Management | Notification, User                       |
| SR-09 Operation Management    | Customer, Driver, Vehicle, Booking, Trip |

```
```
