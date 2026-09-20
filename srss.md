# Phân tích các Bên liên quan (Stakeholder Analysis)

## 1. Bảng xác định Stakeholder và Vai trò

| STT | Tên Stakeholder | Phân loại | Vai trò & Trách nhiệm chính | Mối quan tâm cốt lõi đối với hệ thống |
| :--- | :--- | :--- | :--- | :--- |
| 1 | **Ban lãnh đạo / Ban giám đốc Công ty ABC** | Nội bộ (Internal) | - Đưa ra định hướng chiến lược, tài trợ ngân sách dự án.<br>- Phê duyệt phạm vi, thời hạn (7 tuần) và tiêu chuẩn chất lượng. | - Hiệu quả kinh doanh, mở rộng nền tảng phục vụ lượng lớn người dùng.<br>- Báo cáo doanh thu, số chuyến, tỷ lệ hoàn thành/hủy và hiệu suất tài xế. |
| 2 | **Khách hàng (Rider / Passenger)** | Bên ngoài (External) | - Nhóm người dùng cuối sử dụng dịch vụ vận chuyển.<br>- Đặt xe, theo dõi hành trình, thanh toán và đánh giá tài xế. | - Đặt xe nhanh, tài xế đón đúng giờ, giá cả minh bạch.<br>- Theo dõi chuyến đi theo thời gian thực, bảo mật thông tin tài khoản/thanh toán. |
| 3 | **Tài xế (Driver)** | Bên ngoài / Đối tác (Partner) | - Người trực tiếp thực hiện dịch vụ vận chuyển.<br>- Nhận chuyến, cập nhật trạng thái di chuyển và hoàn thành chuyến đi. | - Nhận thông báo cuốc xe phù hợp, cơ chế phân công minh bạch.<br>- Thao tác ứng dụng đơn giản, cập nhật trạng thái dễ dàng, cước phí rõ ràng. |
| 4 | **Nhân viên Vận hành (Operations Staff)** | Nội bộ (Internal) | - Quản lý hồ sơ khách hàng, tài xế, phương tiện và chuyến đi.<br>- Giám sát chuyến đi trực tiếp, can thiệp hỗ trợ xử lý sự cố, tra cứu giao dịch. | - Giao diện quản trị (Admin Dashboard) trực quan, cập nhật thời gian thực.<br>- Cơ chế phân quyền chặt chẽ để tránh thao tác nhầm các tác vụ nhạy cảm. |
| 5 | **Bộ phận Tổng đài (Call Center / Dispatchers)** | Nội bộ (Internal) | - Tiếp nhận yêu cầu đặt xe truyền thống từ khách hàng qua điện thoại.<br>- Phối hợp chuyển tiếp thông tin vào hệ thống mới. | - Giao diện nhập thông tin chuyến đi nhanh chóng, đồng bộ mượt mà với tài xế. |
| 6 | **Chuyên viên Phân tích Nghiệp vụ (Business Analyst - BA)** | Nội bộ (Internal) | - Phân tích, làm rõ quy tắc nghiệp vụ còn thiếu (cách tính cước, tiêu chí ưu tiên, hủy chuyến...).<br>- Soạn thảo tài liệu đặc tả yêu cầu (SRS) và nghiệm thu chức năng. | - Yêu cầu nghiệp vụ được làm rõ với các bên liên quan trước khi triển khai.<br>- Quy trình nhất quán giữa khách hàng, tài xế và vận hành. |
| 7 | **Đội ngũ Phát triển & QA (Development & Testing Team)** | Nội bộ (Internal) | - Thiết kế kiến trúc phần mềm, phát triển các tính năng và kiểm thử hệ thống.<br>- Đảm bảo hoàn thành sản phẩm trong khung thời gian 7 tuần. | - Kiến trúc linh hoạt, các module mở rộng độc lập (thanh toán, thông báo...).<br>- Khả năng chịu tải cao, hệ thống không bị gián đoạn toàn bộ khi một dịch vụ gặp lỗi. |
| 8 | **Nhà cung cấp Cổng thanh toán (Third-party Payment Provider)** | Đối tác (External) | - Xử lý các giao dịch thanh toán điện tử trực tuyến an toàn. | - Tuân thủ bảo mật, không lưu thông tin thẻ nhạy cảm trên hệ thống CAB.<br>- Cung cấp cơ chế xử lý lỗi/giao dịch thất bại chính xác. |
| 9 | **Nhà cung cấp Dịch vụ Thông báo (Push/SMS Notification Provider)** | Đối tác (External) | - Cung cấp hạ tầng gửi SMS OTP, thông báo đẩy (Push Notifications) đến thiết bị người dùng. | - Đường truyền ổn định, tốc độ gửi nhanh theo thời gian thực.<br>- Dễ dàng mở rộng, tích hợp thêm nhiều kênh thông báo trong tương lai. |

---

## 2. Ma trận Phân tích Stakeholder (Stakeholder Matrix - Power vs. Interest)

Ma trận phân nhóm stakeholder dựa trên mức độ **Quyền lực (Power/Influence)** và **Mức độ quan tâm (Interest)** để đưa ra chiến lược phối hợp hiệu quả:

| Nhóm Chiến lược | Tên Stakeholder | Quyền lực (Power) | Mức độ quan tâm (Interest) | Chiến lược Quản lý & Tương tác |
| :--- | :--- | :---: | :---: | :--- |
| **Manage Closely** *(Quản lý chặt chẽ)* | **Ban giám đốc ABC** | Cao (High) | Cao (High) | Báo cáo tiến độ thường xuyên theo từng tuần (trong 7 tuần), tham vấn các quyết định chiến lược và chính sách kinh doanh. |
| **Manage Closely** *(Quản lý chặt chẽ)* | **Bộ phận BA & Đội ngũ Phát triển** | Cao (High) | Cao (High) | Họp thường xuyên (Daily/Weekly Standup), làm rõ các điểm nghiệp vụ chưa chốt để bám sát tiến độ bàn giao. |
| **Keep Satisfied** *(Giữ hài lòng)* | **Nhà cung cấp Cổng thanh toán** | Cao (High) | Thấp (Low) | Ký kết cam kết chất lượng dịch vụ (SLA), tuân thủ tiêu chuẩn kỹ thuật tích hợp và chuẩn bảo mật dữ liệu thẻ. |
| **Keep Satisfied / Manage Closely** | **Nhân viên Vận hành** | Trung bình (Medium) | Cao (High) | Lấy phản hồi về quy trình quản trị, đào tạo hướng dẫn sử dụng Dashboard và thiết lập cơ chế phân quyền bảo mật. |
| **Keep Informed** *(Cập nhật thông tin)* | **Khách hàng** | Thấp (Low) | Cao (High) | Cung cấp thông báo liên tục về tiến trình chuyến xe, thu thập đánh giá chất lượng dịch vụ sau mỗi chuyến. |
| **Keep Informed** *(Cập nhật thông tin)* | **Tài xế** | Thấp (Low) | Cao (High) | Cập nhật thông báo nhận chuyến rõ ràng, hướng dẫn thao tác ứng dụng, minh bạch về số tiền cước thu được. |
| **Keep Informed** *(Cập nhật thông tin)* | **Bộ phận Tổng đài** | Thấp (Low) | Trung bình (Medium) | Hướng dẫn thao tác nhập cuốc xe vào hệ thống mới, hỗ trợ giải đáp khó khăn khi chuyển đổi quy trình. |
| **Monitor** *(Theo dõi)* | **Nhà cung cấp Thông báo (SMS/Push)** | Thấp (Low) | Thấp (Low) | Theo dõi tỉ lệ gửi tin thành công, dung lượng sử dụng và chi phí định kỳ qua hệ thống logs/metric. |

---

## 3. Sơ đồ Ma trận Stakeholder (Mermaid Diagram)

### 3.1. Sơ đồ Quadrant Chart (Power vs. Interest Grid)

```mermaid
quadrantChart
    title Ma trận Stakeholder (Power vs Interest)
    x-axis "Mức độ Quan tâm Thấp" --> "Mức độ Quan tâm Cao"
    y-axis "Mức độ Quyền lực Thấp" --> "Mức độ Quyền lực Cao"
    quadrant-1 "Manage Closely (Quản lý chặt chẽ)"
    quadrant-2 "Keep Satisfied (Giữ hài lòng)"
    quadrant-3 "Monitor (Theo dõi định kỳ)"
    quadrant-4 "Keep Informed (Cập nhật thông tin)"
    
    "Ban giam doc ABC": [0.92, 0.90]
    "Doi ngu BA & Dev": [0.85, 0.82]
    "Cong thanh toan ben ngoai": [0.25, 0.80]
    "Nhan vien Van hanh": [0.80, 0.60]
    "Tong dai vien": [0.55, 0.35]
    "Nha cung cap SMS & Push": [0.20, 0.25]
    "Khach hang (Rider)": [0.88, 0.28]
    "Tai xe (Driver)": [0.85, 0.25]
