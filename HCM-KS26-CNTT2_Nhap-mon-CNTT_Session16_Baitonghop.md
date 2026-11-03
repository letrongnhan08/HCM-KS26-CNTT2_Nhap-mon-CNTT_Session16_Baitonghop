### **(Bài tập tổng hợp)**

### **Phần A: Thiết lập Profile và Bookmark chuẩn Dev**

1. **Giải thích điều xảy ra khi dùng chung 1 Profile cho cả GitHub cá nhân và GitHub công ty**  
+  Làm rối loạn giữa tab GitHub cá nhân và GitHub công ty  
+  Mở đồng thời 2 tài khoản GitHub khác nhau trên 1 cửa sổ sẽ bị tự động văng 1 tài khoản do Xung đột Session / Cookie.  
+  Lẫn lộn Bookmark,extension, Lịch sử duyệt web và Mật khẩu: Trộn lẫn các trang web nội bộ công ty với dữ liệu cá nhân, sẽ có rủi ro lộ thông tin nhạy cảm của công ty

2. **Áp dụng Mô hình 3 Profile chuẩn Developer vào bối cảnh công ty:**

| Profile | Tên Profile  | Mục đích                                                                                                                                                    |
| ------- | ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1       | Personal     | Sử dụng cho hoạt động cá nhân như quản lý mã nguồn trên tài khoản GitHub cá nhân, hoặc giải trí                                                             |
| 2       | Company      | Chỉ luôn luôn sử dụng cho công việc trên công ty, tài khoản profile công ty cấp chỉ đăng nhập vào web mà công ty cho phép hoặc các trang nội bộ của công ty |
| 3       | Sandbox/Test | thử nghiệm (testing), debug lỗi giao diện, và kiểm tra các tính năng mới<br>                                                                                |

3. **Thiết kế cấu trúc Bookmark gồm 3 thư mục, mỗi thư mục liệt kê 2 trang web nên lưu (theo đúng logic phân loại đã học).**  
- 01\_work\_Developer (Github, StackOverflow)  
- 02\_study (Lms, Outlook)  
- 03\_Tools-kits (JSON Formatter, WhatFont)

4. **Đồng nghiệp mượn máy bạn 5 phút để tra cứu nhanh — bạn cho họ dùng chế độ/Profile nào để không lộ dữ liệu cá nhân? Giải thích ngắn gọn.**  
- Sẽ cho bạn dùng chế độ Guest Profile vì nó sẽ tự động hủy toàn bộ lịch sử mà mình làm trước đó khi đóng tài khoản Guest lại.

### 

### 

### 

### **Phần B – Chọn đúng Extension hỗ trợ**

1. **Gọi đúng tên tiện ích và giải thích vì sao 2 nhóm còn lại không phù hợp.**  
- Nhóm Extension phù hợp: Dev Suite
- Tên tiện ích: JSON Viewer/ Formatter  
- Phù hợp do:  JSON Viewer dùng để đọc JSON 

- 2 nhóm còn lại không phù hợp vì:   
- Productivity Suite  
+ Mục đích: Hỗ trợ quản lý công việc, ghi chú, kiểm tra lỗi ngữ pháp  
+ Lý do: Các tiện ích này không có tính năng phân tích cú pháp hay soi phông chữ dạng (syntax highlighting) và không chuyển JSON thành dữ liệu đọc. Nên không giải quyết được vấn đề dữ liệu kỹ thuật từ API  

- Security Suite  
+ Mục đích: Chặn quảng cáo, theo dõi , quét mã độc trang web, quản lý mật khẩu   
+ Lý do: Nhóm này chỉ đóng vai trò bảo vệ hoặc lọc nội dung nguy hiểm.

     2\.   **Sau khi cài, nên cấu hình quyền Site Access là On click hay On all sites?**

- Sau khi cài, nên cấu hình quyền On click vì: hạn chế quyền đọc dữ liệu web của Extension để bảo mật thông tin thay vì chọn On all sites vì nó sẽ đọc hết tất cả từ web có nguy cơ rò rỉ dữ liệu.

### 

### **Phần C – Phân tích luồng HTTP Request**

1. **Khi gõ test.internal-tool.com và nhấn Enter, liệt kê đúng thứ tự 4 giai đoạn xử lý (từ lúc gõ địa chỉ đến khi trang hiển thị).**  
- DNS Lookup: trình duyệt yêu cầu DNS tra cứu IP của test.internal-tool.com 

- TCP / TLS Handshake: trình duyệt kết nối thành công tới IP của trang web.

- HTTP Request: trình duyệt sẽ gửi yêu cầu lấy nội dung từ máy chủ  
     
- Browser Render: trình duyệt nhận dữ liệu tải về, phân tích HTML và CSS để làm cây DOM và CSSOM, sau đó tính toán bố cục Layout và vẽ các ảnh lên màn hình để người dùng nhìn thấy giao diện hoàn chỉnh. 

2. **So sánh 2 mã trạng thái và hướng debug ban đầu:**

| Mã trạng thái             | Ý nghĩa                         | Lỗi nằm ở đâu ?                                                                  | Hướng Debug ban đầu                                                                                                          |
| ------------------------- | ------------------------------- | -------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| 404 Not Found             | không tìm thấy file đó, sai URL | Nằm ở phía máy cá nhân hoặc máy khác do nhập sai URL hoặc trang web đó đã bị xóa | Nhập lại chính xác đường dẫn URL, cần nhấn Ctrl \+ F5 để xóa đi file đã lưu trong Cache để trình duyệt cập nhật lại file mới |
| 500 Internal Server Error | lỗi Server                      | Nằm ở phía máy chủ mặc dù đã đúng địa chỉ IP, do máy chủ bị sập hoặc quá tải     | Kiểm tra lại các code trong file, xem có chỗ nào báo lỗi màu đỏ  không.                                                      |

   ### 

###  **3\. Trong 4 Tab DevTools (Elements / Console / Network / Application), nên mở Tab nào để xem mã trạng thái HTTP của trang? Vì sao không chọn các Tab còn lại?**

- Mở Tab NetWork để xem mã trạng thái vì ghi lại toàn bộ các hoạt động truyền tải mạng của trang web (tải file HTML, CSS, JavaScript, hình ảnh và API), giúp thấy rõ mã trạng thái HTTP (200 OK, 404 Not Found, 500 Internal Server Error) sẽ dễ dàng xác định API nào đang bị lỗi (hiển thị màu đỏ)
Vì sao không chọn các Tab còn lại:
- Tab Elements: dùng để chỉnh sửa kích cỡ chữ, thay đổi màu sắc, xem các đoạn code.  
- Console: viết code Javascript, CSS,...  
- Application: dùng để xem các tên miền, xóa cookies,....

### 

### **Phần D – Chẩn đoán Cache và Cookies**

1. **Dev vừa sửa CSS nhưng F5 vẫn thấy giao diện cũ. Chẩn đoán nguyên nhân và thao tác khắc phục**  
- Nguyên nhân là do trình duyệt đang sử dụng file CSS cũ đã đc lưu vào Cache trước đó nên sẽ lấy file cũ đó để hiện ra màn hình chứ không lấy file đã sửa lại.  
- Cách khắc phục: nhấn Ctrl \+ shil \+ R hoặc Ctrl \+ F5 để xóa đi file cũ đã lưu trong Cache và trình duyệt sẽ cập nhật lại file mới.

2. **Trong tab Application, Cookie session\_id không có dấu tích ở cột HttpOnly. Rủi ro bảo mật xảy ra là**  
- Rủi ro: tấn công thông qua mã độc XSS để đánh cắp Session Cookie thông qua mã tệp lệnh JavaScript (document.cookie)  
- Tên loại tấn công: XSS (Cross-Site Scripting)   
    
1. **Thao tác xóa phiên đăng nhập mà vẫn giữ lại Cache**  
- Nhấn F12 rồi chuyển sang tab Application rồi tìm mục Storage, nhấp vào Cookies  \> Chọn tên miền  \> Nhấn vào Clear all cookies (biểu tương có ba dấu bằng và 1 dấu x)  
- Nhấn F5 để tải lại trang, toàn bộ ảnh, CSS trong bộ nhớ đệm vẫn được giữ nguyên. 

### **Phần E – Debug bằng Inspect Element và Network Tab**

1. **Sửa màu trực tiếp nút "Đăng nhập" trên trình duyệt**  
- Nhấp chuột phải vào nút "Đăng nhập" \> chọn Inspect để mở tab Elements.  
- Tìm dòng mã màu: Tab Elements, quan sát phần giao diện bên phải chuyển sang tab Styles.
- Tìm đến thuộc tính màu sắc đang áp dụng cho nút.
- Thử màu mới: nhấp chuột vào mã màu cũ để nhập trực tiếp mã màu mới, rồi sao chép lại mã màu mới này để gửi cho Dev.

**2\. Trên tab Network, một request API đang hiện dòng màu đỏ. Áp dụng đúng Quy trình 4 Bước Debugging.**

- B1: Kích hoạt F12 và Disable Cache: bật cả 2 để trình duyệt luôn tải mã mới nhất từ server  
- B2: Định vị lỗi với tab Element  
- B3: Kiểm tra mã trạng thái NetWork là gì: 404 Not Found / 500 Internal Server Error
- B4: Kiểm tra Headers và Reponse Body ( soi chi tiết dữ liệu gửi đi và dữ liệu phản hồi từ máy chủ để xác nhận tính chính xác)

**3\. nêu  2 thao tác cần bật trên tab Network.**

1. Lọc chỉ xem lời gọi API:  Lọc loại tệp (Filter by Type)
- Bấm chọn Fetch/XHR (để ẩn toàn bộ ảnh, CSS, JS, font )

2\.   Đảm bảo lấy dữ liệu mới nhất (không dùng bộ nhớ đệm):
+ Tích chọn vào ô Disable cache để xóa file cũ và luôn lấy bản mới nhất