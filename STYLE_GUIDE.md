# STYLE_GUIDE.md

## Mục đích

File `STYLE_GUIDE.md` được tạo ra để hướng dẫn phong cách trình bày cho tất cả các tài liệu liên quan đến MCP trong repository của bạn. Mục đích chính:

1. **Đảm bảo sự nhất quán**: tất cả tài liệu, sơ đồ, hình minh họa và bảng biểu sẽ tuân theo cùng một phong cách.
2. **Hỗ trợ cộng đồng đóng góp**: khi người khác muốn đóng góp tài liệu con hoặc ví dụ, họ biết rõ style chuẩn.
3. **Hướng dẫn hiển thị trên GitHub Pages**: giúp trang GitHub Pages trông chuyên nghiệp và đồng bộ.

## 1. Theme & Color

* **Phong cách chính**: Modern Blue Theme
* **Tông màu chủ đạo**: Xanh dương (#1E90FF) với các sắc độ nhấn nhá
* **Background**: trắng hoặc xám nhạt (#F9F9F9) để làm nổi bật block highlight
* **Text**: chữ đen #000 hoặc xám đậm #333

## 2. Bố cục

* **Tiêu đề**: H1 – H3, dùng Markdown chuẩn
* **Danh sách**: Bullet points, có thể dùng icon trước mỗi item để trực quan hóa
* **Block highlight**: dùng `>` hoặc code block để nhấn mạnh ý chính

## 3. Icon & Hình minh họa

* Sử dụng icon vector (SVG) hoặc emoji khi cần minh họa đơn giản
* Sơ đồ kiến trúc, luồng hoạt động: lưu trong `/assets/diagrams/`
* Icon phổ biến: 🧠 AI, 🖥️ Server, 🗄️ Database, ⚡ Action

## 4. Đặt tên và thư mục

* File tài liệu con: `DOC_<tên>.md`
* Hình ảnh/diagrams: `/assets/diagrams/<tên>.svg` hoặc `.png`
* Tuân theo cấu trúc thư mục chuẩn của GitHub Pages để dễ quản lý

## 5. GitHub Pages

* Sử dụng Markdown chuẩn, Table of Contents auto tạo bằng `[TOC]` hoặc plugin Jekyll
* Block highlight và màu sắc có thể tùy chỉnh CSS của theme trên Pages

## 6. Lời khuyên

* Luôn giữ sự nhất quán về font, màu, icon và layout
* Tài liệu con nên tập trung vào chi tiết kỹ thuật, sử dụng Style Guide để trình bày đẹp mắt
* Sử dụng comment hoặc note nếu cần giải thích nội dung phức tạp trong file Markdown
