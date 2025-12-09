---
title: "Blog 1"
date: 2025-09-09
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# AWS cho các Ngành Công Nghiệp: Equinox Xây Dựng Kiến Trúc Có Khả Năng Mở Rộng và Tái Sử Dụng Bằng Dịch Vụ AWS IoT

**Tác giả: Girish Nazhiyath — 07/07/2025**
_Danh mục: Amazon Data Firehose, Amazon SageMaker AI, Amazon Simple Storage Service (S3), AWS IoT Core, AWS IoT Greengrass, Các ngành công nghiệp, Kinesis Data Streams, Bán lẻ_

---

Với hơn 100 câu lạc bộ trên toàn cầu, công ty thể hình cao cấp Equinox cần một cơ sở hạ tầng có khả năng mở rộng và tái sử dụng để hỗ trợ các trải nghiệm kỹ thuật số và vật lý tích hợp của mình. Các trải nghiệm kết nối, bao gồm các lớp đạp xe thi đấu, là một dịch vụ chủ chốt giúp thúc đẩy các thành viên theo dõi và đạt được mục tiêu thể chất thông qua ứng dụng di động.

Tuy nhiên, việc cung cấp thông tin chi tiết về thể chất trong thời gian gần thực (near real time) là một thách thức đối với công ty. Khi mới phát triển các trải nghiệm kết nối, Equinox vận hành khối lượng công việc trên máy chủ dựa trên Windows. Mỗi dịch vụ chạy như một tác vụ riêng lẻ. Điều này có nghĩa là các kỹ sư của Equinox phải quản lý việc cập nhật cho từng dịch vụ, việc này tốn nhiều thời gian và dẫn đến sự không nhất quán trong các bản cập nhật phần mềm.

> “Đó là một cơn ác mộng,” Sindhura Nallapareddy, giám đốc kỹ thuật cấp cao tại Equinox cho biết. “Không chỉ là một thành phần mà chúng tôi phải quản lý. Chúng tôi phải kiểm tra máy chủ, cơ sở dữ liệu và các cài đặt trình môi giới tin nhắn (message broker) mỗi khi thực hiện cập nhật.”

Equinox muốn hợp lý hóa việc cập nhật phần mềm cho các kỹ sư của mình và hỗ trợ truyền dữ liệu gần thời gian thực. Vì vậy, công ty đã chuyển sang Amazon Web Services (AWS) để tái cấu trúc hệ thống công nghệ của mình.

> “Chúng tôi không muốn bị kìm hãm bởi các thách thức vận hành,” Nallapareddy nói. “Chúng tôi muốn tập trung vào những khả năng mà mình có thể tạo ra, bao gồm các thử thách thể dục trong phòng tập và giữa các câu lạc bộ.”

## Kết Nối Thiết Bị Tại Câu Lạc Bộ Lên Đám Mây Sử Dụng AWS IoT Core

Equinox đã đánh giá các giải pháp dựa trên đám mây để hỗ trợ xử lý dữ liệu gần thời gian thực và hợp lý hóa quy trình làm việc kỹ thuật. Ưu tiên sự ổn định và dễ sử dụng, Equinox đã thử nghiệm AWS IoT Core, dịch vụ giúp kết nối các thiết bị với đám mây một cách dễ dàng và an toàn.

Để thu thập dữ liệu từ xe đạp, Equinox sử dụng các thiết bị Internet vạn vật (IoT) VAST được cài đặt trên thiết bị tập luyện của mình. Các thiết bị này tuân theo giao thức MPU. Trước khi áp dụng AWS IoT Core, công ty thu thập dữ liệu từ xe đạp dưới dạng các gói giao thức datagram người dùng (UDP), được lưu trữ trên các PC kết nối với mạng cục bộ.

Sau khi thu thập, dữ liệu được xử lý bằng các tác vụ và công việc tùy chỉnh. Các công việc này sẽ chạy trong vài giờ trước khi cung cấp thông tin chi tiết về thể chất cho ứng dụng di động của thành viên.

> “Bản thử nghiệm (PoC) mà chúng tôi tạo ra nhằm xem liệu chúng tôi có thể đồng bộ dữ liệu từ máy chủ biên lên AWS và liệu có thể thiết lập kết nối đám mây một cách đáng tin cậy để hỗ trợ việc triển khai liền mạch hơn hay không,” Aneesh Pillai, kỹ sư tại Equinox cho biết.

Sử dụng AWS IoT Core, công ty có thể thu thập các gói UDP từ xe đạp sử dụng giao thức MQTT, sau đó truyền dữ liệu vào các máy chủ biên và Amazon Simple Storage Service (Amazon S3), một dịch vụ lưu trữ đối tượng được xây dựng để truy xuất bất kỳ lượng dữ liệu nào từ bất kỳ đâu.

Bằng cách lưu trữ dữ liệu trên các thiết bị biên và trên đám mây, Equinox đã giảm khả năng mất dữ liệu, cải thiện chất lượng dữ liệu tổng thể.

> “Chúng tôi đánh giá cao độ tin cậy của dữ liệu được gửi giữa các máy chủ biên và AWS,” Pillai nói. “Tốc độ và sự dễ dàng trong việc quản lý các thành phần này là những lợi ích hàng đầu đối với tôi.”

## Triển Khai Phần Mềm Thống Nhất Với AWS IoT Greengrass

Việc hợp lý hóa việc triển khai phần mềm là điều cần thiết để giúp các kỹ sư tập trung vào việc xây dựng trải nghiệm cá nhân hóa hơn cho thành viên. Vì vậy, Equinox đã xây dựng một ứng dụng quản lý phần mềm cho đội ngũ kỹ thuật của mình sử dụng AWS IoT Greengrass, một môi trường thực thi tại biên và dịch vụ đám mây mã nguồn mở để xây dựng, triển khai và quản lý phần mềm thiết bị.

Để bắt đầu, Equinox triển khai một instance AWS IoT Greengrass duy nhất lên một trong các máy chủ biên của mình. Sau khi ổn định, đội ngũ Equinox đã nhân bản thiết lập này trên tất cả các máy chủ biên. Trước đây, Equinox thu thập dữ liệu đạp xe từ 48 câu lạc bộ; sử dụng AWS IoT Greengrass, công ty đã có thể triển khai cho 80 câu lạc bộ chỉ trong vài tháng.

Khi có bản cập nhật phần mềm, Equinox có thể kích hoạt triển khai trong khi các lớp học đang diễn ra mà không bị mất dữ liệu. Ngoài ra, công ty có thể bắt đầu triển khai tại một câu lạc bộ đơn lẻ hoặc trên tất cả các địa điểm của mình.

> “Đó là một cải tiến quan trọng giúp chúng tôi vượt qua các thách thức vận hành mà chúng tôi đã đối mặt trước đây,” Nallapareddy nói. “AWS IoT Greengrass đã giảm tải cho các đội ngũ của chúng tôi bằng cách gửi các bản cập nhật trong một gói đóng gói sẵn.”

## Bảo Mật Luồng Dữ Liệu Trên Đám Mây

Equinox đã triển khai Amazon Data Firehose để tải các luồng dữ liệu gần thời gian thực một cách đáng tin cậy vào các hồ dữ liệu (data lakes), kho dữ liệu và các dịch vụ phân tích. Để truyền dữ liệu lên đám mây, các kỹ sư của Equinox đã tạo ra hai bộ quy tắc để thu thập dữ liệu từ các thiết bị IoT sử dụng Amazon Kinesis Data Streams, dịch vụ có thể dễ dàng truyền dữ liệu ở bất kỳ quy mô nào.

Một luồng thu thập nhịp tim và dữ liệu sinh trắc học. Luồng còn lại truyền dữ liệu liên quan đến việc sử dụng xe đạp, chẳng hạn như năng lượng pin. Dữ liệu được đồng bộ hóa lên đám mây trên cơ sở sự kiện trong thời gian gần thực. Công ty cũng đã thêm logic bổ sung vào giải pháp của mình để tính toán lượng calo đã đốt cháy và số dặm đã đạp, thông tin này được cung cấp cho các thành viên thông qua ứng dụng di động.

> “Amazon Kinesis Data Streams thực sự tuyệt vời,” Pillai nói. “Tôi có thể nhìn ngay bây giờ và thấy tất cả dữ liệu có sẵn và thiết bị nào đang được sử dụng. Nó diễn ra trong thời gian gần thực, và không có độ trễ hay mất mát dữ liệu.”

Để tránh trùng lặp dữ liệu từ xe đạp, Equinox đã thực hiện lọc dữ liệu. Đội ngũ kỹ thuật cũng thiết lập một mạng riêng thứ hai để truyền các gói UDP từ xe đạp và các thiết bị tập luyện khác, giúp giữ an toàn cho dữ liệu của các thành viên.

## Tăng Năng Suất Kỹ Thuật Và Thử Nghiệm Với AI/ML

Với một hệ thống có khả năng mở rộng và tái sử dụng chạy trên AWS, Equinox đã giải phóng các kỹ sư của mình khỏi các việc triển khai và tích hợp phức tạp. Sử dụng một tập lệnh tùy chỉnh, Equinox có thể mở rộng giải pháp IoT của mình đến các câu lạc bộ trong vài phút, và các kỹ sư đang tiết kiệm thời gian triển khai mỗi tháng.

> “Chúng tôi có thể tập trung vào kinh doanh thay vì các thách thức vận hành,” Pillai nói. “Chúng tôi không phải lo lắng về kết nối giữa đám mây và máy tính cục bộ. Triển khai liền mạch là một trong những lợi ích lớn nhất của kiến trúc chúng tôi.”

Việc thiết lập tự động đã trao quyền cho các kỹ sư của Equinox tập trung vào các tác vụ gia tăng giá trị, bao gồm thử nghiệm với trí tuệ nhân tạo (AI) và máy học (ML). Các nhóm của họ có kế hoạch sử dụng Amazon SageMaker AI để xây dựng, huấn luyện và triển khai các mô hình máy học—bao gồm các mô hình nền tảng (foundation models)—cho bất kỳ trường hợp sử dụng nào với cơ sở hạ tầng, công cụ và quy trình làm việc được quản lý hoàn toàn.

Đội ngũ kỹ thuật của Equinox đang mong muốn xây dựng các dịch vụ thành viên được cá nhân hóa hơn và các khuyến nghị bảo trì dự đoán cho thiết bị tập luyện của mình.

> “Sự tự tin mà chúng tôi có đối với dữ liệu của mình đã mở ra rất nhiều tiềm năng,” Eswar Veluri, phó chủ tịch điều hành kiêm giám đốc công nghệ tại Equinox cho biết. “Chúng tôi có thể khám phá các thử thách giữa các câu lạc bộ, các cột mốc đạp xe và các cuộc thi cá nhân. Có rất nhiều sự hào hứng trong toàn công ty để khám phá và mở khóa thêm nhiều trải nghiệm hơn nữa.”

---

### Girish Nazhiyath

<img src="https://d2908q01vomqb2.cloudfront.net/c5b76da3e608d34edb07244cd9b875ee86906328/2025/07/07/Girish-Nazhiyath_rev.png" align="left" width="150" style="margin-right: 20px; margin-bottom: 10px;" alt="Girish Nazhiyath" />

Girish Nazhiyath hiện đang giữ chức vụ Kiến trúc sư Giải pháp Cấp cao tại AWS. Trong vai trò hiện tại, Girish cung cấp chuyên môn về công nghệ và ngành bán lẻ cho các nhà bán lẻ trên khắp Hoa Kỳ để cho phép họ tận dụng các công nghệ và thực tiễn tốt nhất của AWS. Trước khi làm việc tại AWS, Girish có hơn 25 năm kinh nghiệm nghề nghiệp trong lĩnh vực bán lẻ với các công ty công nghệ và bán lẻ toàn cầu như Microsoft, IBM, NEC, Fujitsu/ICL, Csoft International, Marconi Commerce Systems và Gilbarco Veeder-Root, tập trung vào hệ thống cửa hàng, đa kênh (omnichannel), trải nghiệm khách hàng, thanh toán sinh trắc học và đổi mới bán lẻ. Ông đã làm việc với các nhà bán lẻ trong các lĩnh vực cửa hàng tiện lợi, tạp hóa, viễn thông, cửa hàng bách hóa lớn/bách hóa tổng hợp và bán lẻ chuyên biệt trong suốt sự nghiệp của mình, và các lĩnh vực trọng tâm của ông bao gồm cả hệ thống cửa hàng vật lý (brick-and-mortar), hệ thống Điểm dịch vụ (Point-Of-Service) trực tuyến và hệ thống quản trị/văn phòng hỗ trợ (corporate/back-office).

<br clear="left"/>
