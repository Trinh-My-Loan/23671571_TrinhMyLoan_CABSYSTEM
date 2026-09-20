# Phân tích các bên liên quan (Stakeholder Analysis) - Dự án CAB System

## 1. Bảng danh sách Stakeholders và Vai trò

| Mã Stakeholder | Tên Stakeholder | Phân loại | Vai trò & Trách nhiệm chính | Mối quan tâm chính / Kỳ vọng |
| :--- | :--- | :--- | :--- | :--- |
| **STK-01** | **Ban giám đốc / Ban lãnh đạo (Công ty ABC)** | Nội bộ (Internal) | Chủ đầu tư, phê duyệt ngân sách, định hướng chiến lược kinh doanh và phạm vi nền tảng. | Hệ thống ổn định khi tải cao, có khả năng mở rộng kinh doanh lâu dài, báo cáo doanh thu/hiệu quả chính xác, hoàn thành trong 7 tuần. |
| **STK-02** | **Khách hàng (Passenger / Rider)** | Bên ngoài (External) | Người dùng cuối dịch vụ đặt xe trực tuyến. | Đặt xe dễ dàng, biết rõ trạng thái tìm/đến của xe, thời gian dự kiến, minh bạch giá cước, thanh toán tiện lợi và an toàn thông tin. |
| **STK-03** | **Tài xế (Driver)** | Bên ngoài / Đối tác (External) | Người cung cấp phương tiện và thực hiện vận chuyển khách hàng. | Nhận chuyến xe phù hợp và nhanh chóng, cập nhật trạng thái tiện lợi, giao diện nhận/từ chối rõ ràng, quản lý thu nhập minh bạch. |
| **STK-04** | **Nhân viên vận hành (Operations Staff)** | Nội bộ (Internal) | Quản lý người dùng, xe, giám sát các chuyến đi thời gian thực, can thiệp xử lý sự cố. | Công cụ quản trị trực quan, dễ tra cứu lịch sử, thao tác phân quyền an toàn, hỗ trợ xử lý lỗi chuyến đi kịp thời. |
| **STK-05** | **Đội ngũ phát triển & Phân tích (BA, Dev, QA, PM)** | Nội bộ (Internal) | Phân tích yêu cầu, thiết kế kiến trúc, lập trình, kiểm thử và bàn giao hệ thống. | Yêu cầu nghiệp vụ rõ ràng (cách tính cước, matching rule,...), kiến trúc tách biệt linh hoạt, tiến độ giao hàng khả thi (7 tuần). |
| **STK-06** | **Cổng thanh toán bên thứ ba (Payment Gateway Partner)** | Bên ngoài (External) | Cung cấp dịch vụ xử lý giao dịch điện tử an toàn. | Tích hợp chuẩn giao thức bảo mật (PCI-DSS), xử lý callback/webhook mượt mà, không lưu trữ thông tin thẻ nhạy cảm trên CAB. |
| **STK-07** | **Nhà cung cấp dịch vụ Thông báo (SMS/Push/Email Providers)** | Bên ngoài (External) | Chuyển phát tin nhắn thông báo (Push Notification, SMS) đến người dùng. | Tích hợp chuẩn API, đảm bảo tỷ lệ gửi tin cao, hỗ trợ mở rộng thêm kênh sau này. |

---

## 2. Ma trận các bên liên quan (Stakeholder Matrix - Quyền lực & Mức độ quan tâm)

Ma trận phân loại theo mô hình **Power vs. Interest Grid**:

| Mức độ | Mức độ quan tâm Thấp (Low Interest) | Mức độ quan tâm Cao (High Interest) |
| :--- | :--- | :--- |
| **Quyền lực Cao (High Power)** | **Làm cho họ hài lòng (Keep Satisfied)**<br>• Cổng thanh toán (Payment Gateway)<br>• Cơ quan quản lý/Đối tác hạ tầng viễn thông | **Quản lý chặt chẽ (Manage Closely)**<br>• Ban giám đốc Công ty ABC<br>• Bộ phận Vận hành & Quản trị |
| **Quyền lực Thấp (Low Power)** | **Giám sát tối thiểu (Monitor)**<br>• Nhà cung cấp hạ tầng thông báo phụ | **Cung cấp thông tin đầy đủ (Keep Informed)**<br>• Khách hàng (Riders)<br>• Tài xế (Drivers)<br>• Đội ngũ phát triển & Kiểm thử (Dev/QA Team) |

---

## 3. Sơ đồ Ma trận Stakeholder (Mermaid Diagram)

```mermaid
quadrantChart
    title Ma trận Stakeholder (Power vs Interest) - CAB System
    x-axis "Mức độ quan tâm thấp (Low Interest)" --> "Mức độ quan tâm cao (High Interest)"
    y-axis "Quyền lực thấp (Low Power)" --> "Quyền lực cao (High Power)"
    quadrant-1 "Quản lý chặt chẽ (Manage Closely)"
    quadrant-2 "Giữ hài lòng (Keep Satisfied)"
    quadrant-3 "Theo dõi (Monitor)"
    quadrant-4 "Cập nhật thông tin (Keep Informed)"
    
    "Ban Giám Đốc (ABC)": [0.85, 0.90]
    "Nhân Viên Vận Hành": [0.82, 0.72]
    "Cổng Thanh Toán Thứ Ba": [0.35, 0.78]
    "Khách Hàng (Passenger)": [0.88, 0.38]
    "Tài Xế (Driver)": [0.86, 0.35]
    "Nhóm Phát Triển (BA/Dev/QA)": [0.75, 0.45]
    "Nhà Cung Cấp Thông Báo (SMS/Push)": [0.25, 0.28]
