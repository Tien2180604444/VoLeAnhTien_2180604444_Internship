Using AWS Serverless Services to Build a Scalable Customer Feedback Port

•	Excecutive Summary :
Dự án này xây dựng một cổng phản hồi sử dụng các dịch vụ miễn phí của AWS (Free Tier), giúp tôi làm quen với điện toán đám mây mà không tốn chi phí.Trong vòng 3 tuần, tôi thực hiện ứng dụng với các công nghệ như Lambda, DynamoDB, S3 và Cognito, vừa học vừa làm. Dự án giúp tôi rèn luyện kỹ năng thực tế, đồng thời đáp ứng yêu cầu môn học.Giải pháp sử dụng kiến trúc hiện đại, dễ mở rộng, không cần quản lý máy chủ tuy tôi vẫn còn chưa hiểu rõ được lắm . Kết quả là một sản phẩm hoàn chỉnh còn một số lỗi cần sửa , có thể đưa vào CV hoặc portfolio cá nhân sau này.Ngoài giá trị học thuật, dự án còn giúp tôi tích lũy kinh nghiệm với các công nghệ đang được doanh nghiệp quan tâm, tạo nền tảng tốt cho các dự án đám mây sau này.
•	Problem Statement : Các hệ thống phản hồi truyền thống thường gặp nhiều vấn đề như khó mở rộng khi lưu lượng tăng cao, chi phí duy trì máy chủ cao, phức tạp trong quản lý kỹ thuật, bảo mật kém và khó phân tích dữ liệu phản hồi. Giải pháp cổng phản hồi không máy chủ trên AWS giúp khắc phục những điểm yếu này bằng cách cung cấp một hệ thống linh hoạt, tiết kiệm chi phí, bảo mật tốt và tích hợp sẵn công cụ phân tích, mà không cần phải quản lý hạ tầng phức tạp.

•	Solution Architecture:
1.	Architecture Overview 
2.	AWS Services Used
•	Amazon S3 : Lưu trữ các tệp trang web và nội dung tĩnh.
•	Amazon Cognito : Quản lý đăng nhập và tài khoản người dùng.
•	AWS Lamba Function : Chạy mã mỗi khi có người phản hồi.
•	Amazon API Gateway : Tạo các endpoint để đưa vào frontend.
•	Amazon DynamoDB : nơi lưu trữ dữ liệu feedback.
•	Amazon CloudFront : tăng tốc độ tải web.
•	AWS SAM CLI : giúp triển khai một cách dễ dàng hơn.
3.	Component Design
•	Thành phần giao diện (Frontend) : Website React
•	Thành phần xác thực : Đăng nhập/Đăng ký bằng Cognito (Còn lỗi)
•	Thành phần API: Rest API làm endpoint và truy xuất phản hồi
•	Thành phần cơ sở dữ liệu : Bảng NoSQL lưu trữ dữ liệu phản hồi và người dùng.
•	Thành phần thông báo : Gửi email cảnh báo khi có phản hồi mới (Chưa hoàn thiện).
4.	Security Architecture
•	Xác thực người dùng bằng token của Cognito
•	Sử dụng HTPPS cho mọi giao tiếp
•	API Gateway có cơ chế kiểm tra và xác thực yêu cầu
•	Lambda Function chỉ được cấp quyền hạn chế
•	Các bảng DynamoDB được mã hóa khi lưu trữ
•	Frontend không được truy cập trực tiếp vào cơ sở dữ liệu
•	CloudFront cung cấp bảo vệ cơ bản chống tấn công DDos(Chưa áp dụng)
5.	Scalability Design
•	S3 và CloudFront xử lý lưu lượng truy cập frontend không giới hạn
•	Lambda Function tự động mở rộng theo nhu cầu
•	DynamoDB có thể tự động điều chỉnh công suất đọc/ghi
•	Không có chi phí cố định – chỉ trả tiền khi có người 	sử dụng
•	API Gateway có thể xử lí nghìn yêu cầu mỗi ngày
•	Triển khai theo vùng (regional) giúp giảm độ trễ

•	Techical Implementation:
o	Implement phase :
	Tuần 1 : Nền tảng, cài đặt môi trường
•	Ngày 1 -2 : Thiết lập tài khoản AWS và khởi tạo dự án
•	Ngày 3 – 4 : Thiết lập giao diện và tạo người dùng
•	Ngày 5 – 7 : Xây dựng backend
	Tuần 2 : Hoàn thiện xây dựng chức năng 
•	Ngày 1 -3 : Kết nối frontend với api gateway
•	Ngày 4 -7 : Xây dựng cấp quyền lambda function và test gửi feedback
o	Technical requirement :
	Frontend : 
•	React
•	Aws Amplify
•	Bootstrap
	Backend :
•	AWS Lambda with Node.js
•	API Gateway
•	DynamoDB
•	Amazon Cognito
•	Lưu trữ website tĩnh trên S3
	Development tools:
•	VSCode
•	GitHub
•	AWS Console
•	AWS SAM CLI
•	ChatGPT,Copilot,Amazon Q ….
o	Development Approach :
	Tìm hiểu cách thực hiện qua Google,Youtube hoặc AI
	Xây dựng phiên bản đơn giản có thể sử dụng được
	Kiểm thử thủ công
	Có thời gian, cải tiến thêm
o	Testing Strategy :
	Kiểm thử bằng tay : 
•	Tự mình nhấn và trải nghiệm toàn bộ các tính năng
•	Đảm bảo hoạt động ổn định trên Chrome
	Kiểm thử tự động :
•	Đọc console log trả về lỗi gì
o	Deployment Plan
	Triển khai frontend lên S3
•	Làm theo hướng dẫn document của AWS S3 hosting
•	Cấu hình quyền truy cập public cho bucket
•	Upload file lên S3
	Triển khai backend thông qua AWS Manage Console
•	Tải lên các Lambda Function
•	Thiết lập API Gateway trên manage console
•	Kết nôi với nhauu và hi vọng sẽ không có lỗi gì
	Những thứ cần kiểm tra trước khi hoàn tất triển khai
•	Kiểm tra url website
•	Kiểm tra tính năng gửi feedback
•	Chụp màn hình để đưa vào workshop
•	Timeline and Milestone : 
o	Project timeline : 
	Tuần 1 : Giai đoạn nền tảng (Ngày 1 – 10/6)
•	Tìm kiếm chủ đề tham khảo AI
•	Cài đặt các công cụ phát triển
•	Phác thảo roadmap cơ bản và diagram
•	Xây dựng Frontend
	Tuần 2 : Giai đoạn phát triển (11/06 – 30/06)
•	Ngày 11-20: Tính năng cốt lõi : biểu mẫu gửi feedback,lưu trữ diệu vào DynamoDB , API Gateway hoạt động với URL website hoạt động được.
•	Ngày 21 – 25: Tiếp tục hoàn thiện các chức năng và kết hợp thêm bảo mật (Đang lỗi chỗ xử lí authentication)
•	Ngày 26 – 30 : Kiểm thử lại phần gửi feedback và tiếp tục sửa lỗi.
	Tuần 3 : Giai đoạn kiểm thử và hoàn thiện, viết báo cáo (01/07 – 10/07)
•	Ngày 1 – 5 : Kiểm tra chức năng, trang web còn hoạt động không, còn lỗi ở 1 số dịch vụ.
•	Ngày 6 – 10: Viết báo cáo tiến độ
o	Key Milestones
	Khởi động dự án
•	Chuẩn bị môi trường phát triển
•	Lập kế hoạch hoàn thiện project
	Hoàn thiện giao diện
•	UI cơ bản hoạt động
•	Form phản hồi sẵn sàng
	Tích hợp backend
•	API hoạt động
•	Database lưu dữ liệu phản hồi
•	Kết nối frontend với backend
	Bảo mật đầy đủ ( chưa xử lí xong)
	Hoàn thành dự án (còn đang phát triển)
o	Dependencies
	Phụ thuộc kỹ thuật : 
•	Tài khoản AWS
•	Kiến thức về React
•	Hiểu sơ về Lambda Function
•	Cấu hình Cognito
•	DynamoDB
	Phụ thuộc bên ngoài :
•	Kỳ hạn freetier của AWS
•	AWS Documents 
o	Resource Allocation
	Thời gian :
•	Phát triển frontend (3 – 5 tiếng)
•	Nghiên cứu và cài đặt môi trường (2 ngày)
•	Phát triển backend ( 1 tuần)
•	Tích hợp frontend với backend ( 5 ngày)
•	Kiểm thử và sửa lỗi (1 tuần và còn tiếp tục)
•	Đánh giá và viết báo cáo (3 ngày)
	Công cụ kỹ thuật :
•	Laptop cá nhân để phát triển
•	AWS Freetier
•	Các tool hỗ trợ và AI
	Nguồn học tập :
•	Youtube,google
•	Tài liệu trên trang chính AWS
•	Tài liệu do công ty cung cấp
•	AI
•	Project mẫu trên Github
	Ngân sách :
•	Free vì đang trong giai đoạn free tier
•	Dự phòng 10$ nếu qua giai đoạn free
o	Budget Estimination
	Chi phí hạ tầng :
•	Amazon S3 : free
•	Amazon DynamoDB : free
•	AWS Lambda : free
•	Amazon API Gateway : free
•	Amazon Cognito : free
•	Amazon CloudFront : free
	Chi phí phát triển : 
•	Thời gian bỏ ra  : 
o	Nghiên cứu và đọc tài liệu : 1 tuần
o	Lựa chọn chủ đề và cài đặt môi trường : 3 ngày
o	Phát triển cơ bản test các dịch vụ : 1 tuần
o	Phát triển chính : 4 ngày
o	Kiểm thử và sửa lỗi : 1 tuần và tiếp tục
o	Viết báo cáo : 3 ngày
•	Phần mềm công cụ sử dụng
o	VSCode : free
o	Draw.io : free
o	Tool hỗ trợ : free
o	AI : free
•	Chi phí vận hành : chỉ là một project nhỏ chưa phát triển lớn nên chưa có chi phí vận hành
•	Lợi tức đầu tư (ROI) : một project nhỏ test về vấn đề gửi feedback nhận phản hồi thôi chưa phải là 1 project lớn nên tạm thời chưa có lợi ích đầu tư nếu không phát triển them.Lợi ích lớn nhất là kinh nghiệm tự nghiên cứu tự hoàn thiện một project.
•	Risk Assessment
o	Risk Matrix
	Tác động cao,khả năng cao
•	Bị hết thời gian free tier trước khi hoàn thành project phát sinh thêm chi phí
•	Gặp một số lỗi kỹ thuật đang quá sức của bản thân cần nghiên cứu thêm
	Tác động cao,Khả năng thấp
•	Dịch vụ AWS gặp sự cố ( timeout)
•	Mất toàn bộ dữ liệu
	Tác dộng thấp,khả năng cao
•	Giao diện lỗi,hiển thị sai
•	Độ trễ khi khởi tạo Lambda
•	Khó khăn khi cấu hình Cognito
	Tác động thấp,khả năng thấp
•	AWS cập nhật đổi mới dịch vụ
o	Mitigation Strategies
	Rủi ro kỹ thuật
•	Thay vì vào làm project ngay hãy nghiên cứu tài liệu của AWS trước và tham khảo 1 số project mẫu trên youtube,Github
•	Hỏi sớm khi gặp vấn đề
•	Đừng phức tạp hóa vấn đề quá
	Rủi ro về ngân sách
•	Thiết lập cảnh báo bucket hằng tháng
•	Kiểm tra cost hàng tuần
•	Xóa ngay dịch vụ mình không dùng nhiều
	Rủi ro về tiến độ
•	Tập  trung vào cái chính của project
•	Có thể lập danh sách công việc theo mức độ ưu tiên
•	Tự giác làm trước deadline
	Rủi ro bên ngoài
•	Nên chụp ảnh hoặc sao lưu code
o	Contigency Plans
	Phát sinh chi phí : tắt và xóa các tài nguyên trên AWS
	Khó khăn kỹ thuật : tìm hướng phát triển mới hoặc là nhờ AI cũng như đọc tài liệu mới nhất về vấn đề dịch vụ mình gặp phải,ghi lại những khó khăn.

•	Expected Outcomes
o	Success Metrics
	Hầu hết tính năng hoạt động tốt
	Demo chạy ổn định không lỗi quá nghiêm trọng
	Dữ liệu được lưu đúng vào DynamoDB
	Website tải được
o	Business Benefits
	Có được trải nghiệm 1 dự án thực tế để đưa vào CV
	Kỹ năng thực hành và trải nghiệm dịch vụ đang đứng đầu trên thị trường yêu cầu
	Một sản phẩm đáng để tự hào đưa vào profile cá nhân
o	Technical Improvements
	Trải nghiệm thực tế các dịch vụ của AWS
	Phát triển Frontend với React
	Biết được cách dùng API và host lên bằng dịch vụ của AWS
	Kinh nghiệm vẽ sơ đồ kiến trúc bằng draw.io
	Bổ sung được kiến thức đọc tài liệu Tiếng Anh
o	Long-term value
	Nền tảng thi chứng chỉ AWS 
	Có thể tự lực xây dựng ứng dụng đám mây
	Càng ngày càng phát triển càng nắm vững được công nghệ mới đứng đầu
	Có thể quản lý được các chi phí trên AWS

 




				





















	

		
				

