# Tài liệu tổng quan về Model Context Protocol (MCP)

<!-- Style được tách ra file riêng STYLE_GUIDE.md -->

## 1. MCP là gì?

**Model Context Protocol (MCP)** là một **giao thức mở** được tạo ra để chuẩn hóa cách các mô hình AI (đặc biệt là mô hình ngôn ngữ lớn – LLM) truy cập và tương tác với **dữ liệu, công cụ và dịch vụ bên ngoài**.

Trước đây, mỗi ứng dụng AI cần được lập trình tích hợp riêng với từng API, cơ sở dữ liệu hoặc hệ thống nội bộ. Điều đó khiến việc kết nối AI mở rộng theo quy mô doanh nghiệp trở nên phức tạp và tốn chi phí.

MCP giải quyết vấn đề này bằng một chuẩn thống nhất — giúp AI có thể "hiểu" và "giao tiếp" với nguồn lực bên ngoài theo cùng một khuôn dạng, tương tự như vai trò của **USB-C** trong việc chuẩn hóa kết nối phần cứng.

## 2. MCP Server là gì?

**MCP Server** là thành phần trung gian đóng vai trò như "bộ kết nối chuẩn hóa" giữa mô hình AI và các tài nguyên bên ngoài. Thay vì để AI trực tiếp gọi API hay truy cập database, mọi tương tác đều đi qua MCP Server.

MCP Server chịu trách nhiệm:

* Cung cấp **danh sách các công cụ (tools)** và **nguồn dữ liệu (resources)** mà AI có thể sử dụng
* Nhận yêu cầu từ AI → chuyển đổi thành hành động cụ thể với hệ thống bên ngoài
* Trả kết quả về lại cho AI theo đúng định dạng chuẩn MCP
* Kiểm soát quyền truy cập và đảm bảo an toàn dữ liệu

Có thể coi MCP Server như **một API Gateway dành riêng cho AI**, giúp việc tích hợp với hệ thống doanh nghiệp trở nên dễ dàng, bảo mật và có kiểm soát.

## 3. Kiến trúc MCP

Kiến trúc MCP được thiết kế theo mô hình **Client – Server – External Services** nhằm tách biệt rõ vai trò giữa mô hình AI, lớp giao tiếp và hệ thống nguồn dữ liệu.

### Thành phần chính

* **AI Agent / LLM**: Tác nhân thông minh tạo yêu cầu sử dụng dữ liệu/công cụ
* **MCP Client**: Cầu nối giao tiếp giữa AI và MCP Server, hỗ trợ truy vấn metadata và thực thi tool
* **MCP Server**: Chuẩn hoá quyền truy cập, mapping AI → API/Database/System
* **External Resources**: Hệ thống doanh nghiệp, API, kho dữ liệu, dịch vụ chuyên dụng, file nội bộ

### Luồng hoạt động

1. AI yêu cầu sử dụng công cụ hoặc dữ liệu (qua MCP Client)
2. MCP Client gửi request tiêu chuẩn đến MCP Server
3. MCP Server gọi đến hệ thống bên ngoài (API/DB)
4. Kết quả trả về qua MCP Client về AI theo đúng format MCP

---

📌 *Hình minh họa kiến trúc sẽ được bổ sung dưới dạng SVG/PNG chuyên nghiệp trong thư mục `/assets/diagrams/`*

## 4. Ứng dụng thực tế của MCP

MCP mở ra khả năng tích hợp AI vào hệ thống doanh nghiệp một cách **an toàn, linh hoạt và mở rộng theo quy mô**. Dưới đây là những kịch bản sử dụng điển hình:

### 4.1 Trợ lý AI trong doanh nghiệp

* Tự động hóa thao tác với CRM, ERP, HRM, ticket system
* Quản lý công việc, truy vấn trạng thái dự án từ Jira, GitHub, ClickUp…
* Truy vấn thông tin khách hàng từ cơ sở dữ liệu nội bộ

### 4.2 Trợ lý AI dành cho Developer / DevOps

* Thực thi tool CI/CD (deploy, rollback, check build status)
* Phân tích log hệ thống, đề xuất khắc phục sự cố
* Tự động hóa quản lý môi trường Dev/Stg/Prod

### 4.3 AI có khả năng truy vấn dữ liệu nâng cao

* Khai thác kho dữ liệu lớn (BigQuery, PostgreSQL…) bằng câu hỏi tự nhiên
* Trực quan hóa số liệu ngay trong cuộc hội thoại
* Hỗ trợ nhân viên phân tích BI mà không cần SQL

### 4.4 Tích hợp Chat Ops cho nhóm hỗ trợ khách hàng

* Đọc ticket, file đính kèm, lịch sử trao đổi
* Đưa ra tóm tắt nhanh và mức độ ưu tiên xử lý
* Kích hoạt các workflow backend trực tiếp từ chat

### 4.5 Tối ưu hóa quy trình trong doanh nghiệp

* Tự động điền biểu mẫu, xuất báo cáo định kỳ
* Phát hiện rò rỉ lỗi thủ công và đề xuất cải thiện
* Hỗ trợ đào tạo nội bộ bằng dữ liệu riêng của công ty

💡 *MCP đặc biệt phù hợp với môi trường có nhiều hệ thống rời rạc, nơi AI cần giao tiếp với nhiều API khác nhau nhưng vẫn phải đảm bảo bảo mật và kiểm soát quyền truy cập.*

## 5. Ưu điểm và tiềm năng của MCP

* **Chuẩn hoá giao tiếp giữa AI và hệ thống bên ngoài** → Giảm phụ thuộc vào API tùy biến
* **Tăng cường bảo mật và kiểm soát** → Quyền truy cập được quản lý tập trung
* **Mở rộng linh hoạt theo quy mô tổ chức** → Thêm công cụ/dữ liệu mà không cần sửa AI
* **Tương thích đa nền tảng** → Hoạt động với nhiều mô hình AI và hệ thống khác nhau
* **Tăng tốc triển khai ứng dụng AI thực tế** → Tập trung vào logic thay vì xử lý giao tiếp

➡️ MCP hứa hẹn trở thành tiêu chuẩn chung trong hệ sinh thái AI Agent

## 6. Rủi ro và khuyến nghị triển khai

### 6.1 Rủi ro tiềm ẩn

* **Lộ dữ liệu nhạy cảm** nếu AI được cấp quyền truy cập rộng vào hệ thống nội bộ
* **Sai lệch hành động ngoài ý muốn** do AI kích hoạt tool không phù hợp
* **Phụ thuộc vào hạ tầng trung gian** → MCP Server trở thành một điểm sự cố (Single Point of Failure)
* **Kiểm soát truy cập phức tạp** nếu không phân quyền theo vai trò rõ ràng
* **Khó kiểm toán truy vết** nếu thiếu log theo chuẩn và quan sát vận hành
* **Độ trễ hoặc nghẽn kết nối** khi nhiều hệ thống được gọi gián tiếp qua MCP

### 6.2 Khuyến nghị triển khai

* **Nguyên tắc Least-Privilege**: Chỉ cấp AI quyền tối thiểu cần thiết
* **Tách môi trường rõ ràng**: Dev/Stg/Prod với profile quyền riêng
* **Cơ chế kiểm duyệt phía người dùng** cho các hành động có rủi ro
* **Giám sát & logging chuẩn hóa**: Ghi nhận đầy đủ yêu cầu và hành động từ AI
* **Kiểm thử hành động AI trước khi cấp quyền thật sự** nhằm ngăn hành vi sai lệch
* **High availability cho MCP Server**: dùng load balancer, auto-restart, monitoring
* **Thiết lập ranh giới bảo mật** giữa MCP Server và hệ thống nội bộ (Firewall, IAM)

➡️ MCP trở thành **lớp bảo vệ trung gian an toàn** thay vì tạo ra rủi ro mới

## 7. Tương lai của MCP và AI Agent

### 7.1 Sự phát triển của AI Agent

* AI Agent sẽ chủ động tương tác với các hệ thống doanh nghiệp, tự động hóa công việc và hỗ trợ quyết định
* Khả năng học hỏi từ hành vi và dữ liệu trước đó để cải thiện hiệu quả

### 7.2 MCP trở thành tiêu chuẩn mở

* Tiêu chuẩn hóa cách các mô hình AI giao tiếp với các công cụ và dịch vụ
* Đóng vai trò giống như "USB-C" trong thế giới AI: mọi agent có thể plug-in vào bất kỳ hệ thống nào hỗ trợ MCP

### 7.3 Hệ sinh thái mở

* MCP Server và plugin/tool từ cộng đồng sẽ hình thành marketplace cho AI
* Các doanh nghiệp và dev có thể tạo và chia sẻ module, công cụ mở rộng

### 7.4 Governance & Security

* Tăng cường kiểm soát và trách nhiệm cho AI khi thực hiện tác vụ nhạy cảm
* Áp dụng các quy tắc bảo mật, logging và audit chuẩn hóa

### 7.5 Native Integration

* MCP sẽ dần được tích hợp sẵn trong IDE, nền tảng DevOps, CI/CD, hệ thống BI
* Giúp các doanh nghiệp triển khai AI Agent nhanh chóng và an toàn

➡️ Sự kết hợp giữa **tầm nhìn dài hạn** và **ứng dụng thực tế** sẽ thúc đẩy MCP trở thành trung tâm của hệ sinh thái AI Agent, tạo điều kiện cho AI trở nên thông minh, chủ động và an toàn trong môi trường doanh nghiệp.
