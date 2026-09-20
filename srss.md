# Stakeholder Analysis & Matrix

## 1. Bảng Stakeholder và Vai trò

| Stakeholder | Vai trò |
| :--- | :--- |
| **Ban lãnh đạo Công ty ABC** | Định hướng chiến lược, tài trợ ngân sách, phê duyệt dự án (7 tuần) và theo dõi báo cáo doanh thu/vận hành[cite: 1]. |
| **Khách hàng (Rider)** | Đăng ký tài khoản, đặt xe, theo dõi vị trí tài xế, thanh toán cước phí và đánh giá sau chuyến[cite: 1]. |
| **Tài xế (Driver)** | Quản lý hồ sơ, chia sẻ vị trí thực, bật sẵn sàng làm việc, nhận/từ chối cuốc và cập nhật tiến trình chuyến[cite: 1]. |
| **Nhân viên vận hành** | Quản lý thông tin trên Dashboard, giám sát chuyến đi, xử lý sự cố cuốc xe và tra cứu lịch sử giao dịch[cite: 1]. |
| **Bộ phận tổng đài** | Tiếp nhận yêu cầu đặt xe truyền thống qua điện thoại từ khách hàng[cite: 1]. |
| **Chuyên viên phân tích (BA)** | Làm rõ các quy tắc nghiệp vụ chưa chốt (tính cước, hủy chuyến, ưu tiên xe...) và đặc tả yêu cầu chi tiết[cite: 1]. |
| **Đội ngũ phát triển (Dev/QA)** | Thiết kế kiến trúc chịu tải/mở rộng độc lập, lập trình, kiểm thử và bàn giao sản phẩm trong 7 tuần[cite: 1]. |
| **Cổng thanh toán bên ngoài** | Xử lý giao dịch thanh toán trực tuyến an toàn mà không lưu thông tin thẻ trên hệ thống CAB[cite: 1]. |
| **Nhà cung cấp thông báo** | Cung cấp hạ tầng gửi tin nhắn (SMS/Push Notification) theo thời gian thực tới khách hàng và tài xế[cite: 1]. |

---

## 2. Ma trận Stakeholder (Stakeholder Matrix - Power vs. Interest)

| Nhóm chiến lược | Stakeholder | Quyền lực (Power) | Mức độ quan tâm (Interest) | Chiến lược quản lý |
| :--- | :--- | :---: | :---: | :--- |
| **Manage Closely** *(Quản lý chặt chẽ)* | Ban lãnh đạo Công ty ABC | Cao (High) | Cao (High) | Báo cáo tiến độ định kỳ hàng tuần, bám sát hạn chót 7 tuần và các mục tiêu kinh doanh[cite: 1]. |
| **Manage Closely** *(Quản lý chặt chẽ)* | Chuyên viên BA & Dev/QA | Cao (High) | Cao (High) | Phối hợp liên tục để làm rõ quy tắc nghiệp vụ còn thiếu trước khi triển khai[cite: 1]. |
| **Keep Satisfied** *(Giữ hài lòng)* | Cổng thanh toán bên ngoài | Cao (High) | Thấp (Low) | Tuân thủ tiêu chuẩn kỹ thuật API và quy định bảo mật dữ liệu thẻ[cite: 1]. |
| **Keep Satisfied / Manage Closely** | Nhân viên vận hành | Trung bình (Medium) | Cao (High) | Thu thập phản hồi giao diện quản trị, đào tạo sử dụng và phân quyền thao tác[cite: 1]. |
| **Keep Informed** *(Thông báo thường xuyên)* | Khách hàng (Rider) | Thấp (Low) | Cao (High) | Cập nhật thông báo trạng thái chuyến xe rõ ràng, minh bạch cước phí[cite: 1]. |
| **Keep Informed** *(Thông báo thường xuyên)* | Tài xế (Driver) | Thấp (Low) | Cao (High) | Hướng dẫn ứng dụng, thông báo cuốc xe kịp thời và minh bạch phân công[cite: 1]. |
| **Keep Informed** *(Thông báo thường xuyên)* | Bộ phận tổng đài | Thấp (Low) | Trung bình (Medium) | Hướng dẫn phối hợp dữ liệu với hệ thống mới[cite: 1]. |
| **Monitor** *(Theo dõi định kỳ)* | Nhà cung cấp thông báo | Thấp (Low) | Thấp (Low) | Giám sát chất lượng kết nối API và tỷ lệ gửi tin nhắn thành công[cite: 1]. |

---

## 3. Sơ đồ Mermaid

### 3.1. Sơ đồ Ma trận Phân loại (Quadrant Chart)

```mermaid
quadrantChart
    title Stakeholder Matrix (Power vs Interest)
    x-axis "Mức độ Quan tâm Thấp" --> "Mức độ Quan tâm Cao"
    y-axis "Mức độ Quyền lực Thấp" --> "Mức độ Quyền lực Cao"
    quadrant-1 "Manage Closely (Quản lý chặt)"
    quadrant-2 "Keep Satisfied (Giữ hài lòng)"
    quadrant-3 "Monitor (Theo dõi)"
    quadrant-4 "Keep Informed (Cập nhật thông tin)"
    
    "Ban lanh dao ABC": [0.90, 0.90]
    "Doi ngu BA & Dev": [0.85, 0.85]
    "Cong thanh toan": [0.25, 0.80]
    "Nhan vien van hanh": [0.80, 0.60]
    "Bo phan tong dai": [0.55, 0.35]
    "Nha cung cap thong bao": [0.20, 0.25]
    "Khach hang (Rider)": [0.88, 0.28]
    "Tai xe (Driver)": [0.85, 0.25]
