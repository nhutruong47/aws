---
title: "Blog 3"
date: 2025-07-10
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Trí tuệ Nhân tạo: Tăng tốc quy trình làm việc AI của bạn bằng cách kết nối với SageMaker Studio từ Visual Studio Code

**bởi Durga Sury, Raj Bagwe, Sri Aakash Mandavilli, và Edward Sun vào ngày 10 tháng 7 năm 2025**
_Danh mục: Nâng cao (300), Amazon SageMaker Studio, Hướng dẫn Kỹ thuật_

---

Các nhà phát triển AI và kỹ sư học máy (ML) hiện có thể sử dụng các khả năng của Amazon SageMaker Studio trực tiếp từ Visual Studio Code (VS Code) cục bộ của họ. Với khả năng này, bạn có thể sử dụng thiết lập VS Code cục bộ tùy chỉnh của mình, bao gồm các công cụ phát triển hỗ trợ AI, các tiện ích mở rộng tùy chỉnh và các công cụ gỡ lỗi trong khi truy cập tài nguyên tính toán và dữ liệu của bạn trong SageMaker Studio. Bằng cách truy cập các tính năng phát triển mô hình quen thuộc, các nhà khoa học dữ liệu có thể duy trì quy trình làm việc đã thiết lập của họ, bảo toàn các công cụ năng suất và phát triển, huấn luyện cũng như triển khai các mô hình học máy, học sâu và AI tạo sinh một cách liền mạch.

Trong bài viết này, chúng tôi chỉ cho bạn cách kết nối từ xa VS Code cục bộ của bạn với các môi trường phát triển SageMaker Studio để sử dụng môi trường phát triển tùy chỉnh của bạn trong khi truy cập các tài nguyên tính toán của Amazon SageMaker AI.

Khả năng kết nối môi trường phát triển tích hợp (IDE) cục bộ mang lại ba lợi ích chính cho các nhà phát triển và nhà khoa học dữ liệu:

- **Môi trường phát triển quen thuộc với khả năng tính toán có thể mở rộng:** Làm việc trong môi trường IDE quen thuộc của bạn trong khi khai thác môi trường phát triển mô hình chuyên dụng của SageMaker AI. Giữ các chủ đề, phím tắt, tiện ích mở rộng, năng suất và công cụ AI ưa thích của bạn trong khi truy cập các tính năng của SageMaker AI.
- **Đơn giản hóa vận hành:** Chỉ với một vài cú nhấp chuột, bạn có thể giảm thiểu các cấu hình phức tạp và chi phí quản trị khi thiết lập quyền truy cập từ xa vào các không gian (spaces) SageMaker Studio. Việc tích hợp cung cấp quyền truy cập trực tiếp vào các không gian Studio từ IDE của bạn.
- **Bảo mật cấp doanh nghiệp:** Hưởng lợi từ các kết nối an toàn giữa IDE của bạn và SageMaker AI thông qua quản lý thông tin xác thực tự động và duy trì phiên. Ngoài ra, việc thực thi mã vẫn nằm trong ranh giới được kiểm soát của SageMaker AI.

Tính năng này thu hẹp khoảng cách giữa các sở thích phát triển cục bộ và các tài nguyên học máy dựa trên đám mây, để các nhóm có thể cải thiện năng suất của họ trong khi sử dụng các tính năng của Amazon SageMaker AI.

## Tổng quan giải pháp

Sơ đồ sau đây minh họa sự tương tác giữa IDE cục bộ của bạn và các không gian SageMaker Studio.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-1.png)

Kiến trúc giải pháp bao gồm ba thành phần chính:

- **Máy tính cục bộ:** Máy phát triển của bạn đang chạy VS Code với tiện ích mở rộng AWS Toolkit đã được cài đặt.
- **SageMaker Studio:** Một môi trường phát triển ML thống nhất, dựa trên web để xây dựng, huấn luyện, triển khai và quản lý các quy trình học máy và phân tích một cách liền mạch ở quy mô lớn bằng cách sử dụng các công cụ AWS tích hợp và quyền truy cập vào dữ liệu của bạn được bảo mật và quản trị.
- **AWS Systems Manager:** Một dịch vụ quản lý và truy cập từ xa an toàn, có thể mở rộng cho phép kết nối liền mạch giữa VS Code cục bộ của bạn và các không gian SageMaker Studio để hợp lý hóa các quy trình phát triển ML.

Luồng kết nối hỗ trợ hai tùy chọn:

- **Khởi chạy trực tiếp (deep link):** Người dùng có thể bắt đầu kết nối trực tiếp từ giao diện web SageMaker Studio bằng cách chọn Open in VS Code (Mở trong VS Code), thao tác này sẽ tự động khởi chạy phiên bản VS Code cục bộ của họ.
- **Kết nối AWS Toolkit:** Người dùng có thể kết nối thông qua tiện ích mở rộng AWS Toolkit trong VS Code bằng cách duyệt các không gian SageMaker Studio có sẵn và chọn môi trường mục tiêu của họ.

Ngoài những điều trên, người dùng cũng có thể kết nối trực tiếp với không gian của họ từ terminal của IDE bằng SSH. Để biết hướng dẫn về cách kết nối bằng SSH, hãy tham khảo tài liệu tại đây.

Sau khi kết nối, các nhà phát triển có thể:

- Sử dụng các công cụ và tiện ích mở rộng VS Code tùy chỉnh của họ
- Truy cập và sử dụng từ xa bộ lưu trữ của không gian
- Chạy khối lượng công việc AI và ML của họ trong các môi trường tính toán SageMaker
- Làm việc với các notebook trong IDE ưa thích của họ
- Duy trì các tham số bảo mật tương tự như môi trường web SageMaker Studio

## Triển khai giải pháp

### Điều kiện tiên quyết

Để thử kết nối IDE từ xa, bạn phải đáp ứng các điều kiện tiên quyết sau:

- Bạn có quyền truy cập vào một miền (domain) SageMaker Studio có kết nối internet. Đối với các miền được thiết lập ở chế độ chỉ VPC, miền của bạn phải có đường dẫn ra internet thông qua proxy hoặc cổng NAT. Nếu miền của bạn hoàn toàn bị cô lập khỏi internet, hãy xem Kết nối với VPC có mạng con không có quyền truy cập internet để thiết lập kết nối từ xa. Nếu bạn chưa có miền Studio, bạn có thể tạo một miền bằng tùy chọn thiết lập nhanh hoặc thiết lập tùy chỉnh.
- Bạn có quyền cập nhật miền SageMaker Studio hoặc vai trò thực thi của người dùng trong AWS Identity and Access Management (IAM).
- Bạn đã cài đặt VS Code ổn định mới nhất với Microsoft Remote SSH (phiên bản 0.74.0 trở lên) và tiện ích mở rộng AWS Toolkit (phiên bản v3.68.0 trở lên) trên máy cục bộ của mình. Tùy chọn, nếu bạn muốn kết nối trực tiếp với các không gian SageMaker từ VS Code, bạn cần được xác thực để truy cập các tài nguyên AWS bằng thông tin xác thực IAM hoặc AWS IAM Identity Center. Xem tài liệu quản trị viên về hỗ trợ xác thực AWS Toolkit.
- Bạn sử dụng các image SageMaker Distribution tương thích (2.7+ và 3.1+) để chạy các không gian SageMaker Studio, hoặc một image tùy chỉnh.
- Nếu bạn đang bắt đầu kết nối từ IDE, bạn đã có hồ sơ người dùng trong miền SageMaker Studio mà bạn muốn kết nối, và các không gian đã được tạo bằng giao diện người dùng Studio hoặc qua API. AWS Toolkit không cho phép tạo hoặc xóa các không gian.

### Thiết lập các quyền cần thiết

Chúng tôi đã ra mắt API StartSession cho khả năng kết nối IDE từ xa. Thêm quyền sagemaker:StartSession vào vai trò của người dùng của bạn để họ có thể kết nối từ xa với một không gian.

Đối với trải nghiệm deep-linking, người dùng bắt đầu phiên từ xa từ giao diện người dùng Studio. Do đó, vai trò thực thi mặc định của miền, hoặc vai trò thực thi của người dùng phải cho phép người dùng gọi API StartSession. Sửa đổi các quyền trên miền hoặc vai trò thực thi người dùng của bạn bằng cách thêm câu lệnh chính sách sau:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "RestrictStartSessionOnSpacesToUserProfile",
      "Effect": "Allow",
      "Action": ["sagemaker:StartSession"],
      "Resource": "arn:*:sagemaker:${aws:Region}:${aws:AccountId}:space/${sagemaker:DomainId}/*",
      "Condition": {
        "ArnLike": {
          "sagemaker:ResourceTag/sagemaker:user-profile-arn": "arn:*:sagemaker:${aws:Region}:${aws:AccountId}:user-profile/${sagemaker:DomainId}/${sagemaker:UserProfileName}"
        }
      }
    }
  ]
}
```

Nếu bạn đang khởi tạo kết nối đến các không gian SageMaker Studio trực tiếp từ VS Code, thông tin xác thực AWS của bạn phải cho phép người dùng liệt kê các không gian, bắt đầu hoặc dừng một không gian, và bắt đầu kết nối đến một không gian đang chạy. Đảm bảo rằng thông tin xác thực AWS của bạn cho phép các hành động API sau:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "sagemaker:ListSpaces",
        "sagemaker:DescribeSpace",
        "sagemaker:UpdateSpace",
        "sagemaker:ListApps",
        "sagemaker:CreateApp",
        "sagemaker:DeleteApp",
        "sagemaker:DescribeApp",
        "sagemaker:StartSession",
        "sagemaker:DescribeDomain",
        "sagemaker:AddTags"
      ],
      "Resource": "*"
    }
  ]
}
```

Chính sách IAM ban đầu này cung cấp nền tảng khởi đầu nhanh để thử nghiệm các tính năng SageMaker. Các tổ chức có thể triển khai các kiểm soát truy cập chi tiết hơn bằng cách sử dụng các ràng buộc Tên tài nguyên Amazon (ARN) hoặc kiểm soát truy cập dựa trên thuộc tính (ABAC). Với sự ra mắt của API StartSession, bạn có thể hạn chế quyền truy cập bằng cách xác định các ARN không gian trong phần tài nguyên hoặc thực hiện các thẻ điều kiện theo nhu cầu bảo mật cụ thể của bạn, như được hiển thị trong ví dụ sau.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowRemoteAccessByTag",
      "Effect": "Allow",
      "Action": ["sagemaker:StartSession"],
      "Resource": "*",
      "Condition": {
        "StringEquals": {
          "aws:ResourceTag/User": "<user-identifier>"
        }
      }
    }
  ]
}
```

### Kích hoạt kết nối từ xa và khởi chạy VS Code từ SageMaker Studio

Để kết nối với một không gian SageMaker từ xa, không gian đó phải được kích hoạt quyền truy cập từ xa.
Trước khi chạy một không gian trên giao diện người dùng Studio, bạn có thể bật Remote access (Truy cập từ xa) để kích hoạt tính năng này, như được hiển thị trong ảnh chụp màn hình sau.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/10/screenshot-enable-remote-access-outline-1.png)

Sau khi tính năng được kích hoạt, chọn Run space (Chạy không gian) để bắt đầu không gian. Sau khi không gian đang chạy, chọn Open in VS Code (Mở trong VS Code) để khởi chạy VS Code.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/10/screenshot-open-vs-code-arrow.png)

Lần đầu tiên bạn chọn tùy chọn này, trình duyệt của bạn sẽ nhắc bạn xác nhận việc mở VS Code. Chọn hộp kiểm Always allow studio (Luôn cho phép studio) để xác nhận và sau đó chọn Open Visual Studio Code (Mở Visual Studio Code).

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-4.jpeg)

Thao tác này sẽ mở VS Code, và bạn sẽ được nhắc cập nhật cấu hình SSH của mình. Chọn Update SSH config (Cập nhật cấu hình SSH) để hoàn tất kết nối. Đây cũng là thiết lập một lần và bạn sẽ không được nhắc cho các kết nối trong tương lai.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-5-300x220.jpeg)

Khi kết nối thành công, một cửa sổ mới sẽ khởi chạy được kết nối với không gian SageMaker Studio và có quyền truy cập vào bộ lưu trữ của không gian Studio.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-6.jpeg)

### Kết nối tới không gian từ VS Code

Sử dụng AWS Toolkit, bạn có thể liệt kê các không gian, bắt đầu, kết nối tới một không gian, hoặc kết nối tới một không gian đang chạy đã được kích hoạt kết nối từ xa. Nếu một không gian đang chạy không được kích hoạt kết nối từ xa, bạn có thể dừng không gian từ AWS Toolkit và sau đó chọn biểu tượng Connect (Kết nối) để tự động bật kết nối từ xa và bắt đầu không gian. Phần sau đây mô tả trải nghiệm chi tiết.

Sau khi bạn đã xác thực vào AWS, từ AWS Toolkit, truy cập Khu vực (Region) AWS nơi có miền SageMaker Studio của bạn. Bây giờ bạn sẽ thấy phần SageMaker AI. Chọn phần SageMaker AI để liệt kê các không gian trong Khu vực của bạn. Nếu bạn đang kết nối bằng IAM, bộ công cụ sẽ liệt kê các không gian trên khắp các miền và người dùng trong Khu vực của bạn. Xem [Tùy chọn] Lọc không gian theo miền hoặc người dùng cụ thể bên dưới để biết hướng dẫn xem các không gian cho một hồ sơ người dùng cụ thể. Đối với người dùng Identity Center, danh sách đã được lọc để chỉ hiển thị các không gian do bạn sở hữu.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-7.jpeg)

Sau khi bạn xác định được không gian, chọn biểu tượng kết nối như được hiển thị trong ảnh chụp màn hình bên dưới để kết nối tới không gian.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-8.jpeg)

**Tùy chọn: Lọc không gian theo miền hoặc người dùng cụ thể**

Khi kết nối với một tài khoản bằng IAM, bạn sẽ thấy danh sách các không gian trong tài khoản và khu vực. Điều này có thể gây choáng ngợp nếu tài khoản có hàng chục hoặc hàng trăm miền, người dùng và không gian. Bộ công cụ cung cấp tiện ích lọc giúp bạn nhanh chóng lọc danh sách không gian theo một hồ sơ người dùng cụ thể hoặc danh sách các hồ sơ người dùng.
Bên cạnh SageMaker AI, chọn biểu tượng bộ lọc như được hiển thị trong ảnh chụp màn hình sau.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-9.jpeg)

Bây giờ bạn sẽ thấy danh sách các hồ sơ người dùng và miền. Cuộn qua danh sách hoặc nhập tên hồ sơ người dùng hoặc miền, sau đó chọn hoặc bỏ chọn để lọc danh sách các không gian theo miền hoặc hồ sơ người dùng.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-10.jpeg)

## Các trường hợp sử dụng

Các trường hợp sử dụng sau đây minh họa cách các nhà phát triển AI và kỹ sư học máy (ML) có thể sử dụng khả năng kết nối môi trường phát triển tích hợp (IDE) cục bộ.

### Kết nối với kernel của notebook

Sau khi bạn đã kết nối với không gian, bạn có thể bắt đầu tạo và chạy các notebook và tập lệnh ngay từ môi trường phát triển cục bộ của mình. Bằng cách sử dụng phương pháp này, bạn có thể sử dụng cơ sở hạ tầng được quản lý do SageMaker cung cấp cho các tác vụ AI tiêu tốn nhiều tài nguyên trong khi viết mã trong môi trường quen thuộc. Bạn có thể chạy các ô (cells) notebook trên SageMaker Distribution hoặc các kernel image tùy chỉnh, và có thể chọn IDE tối đa hóa năng suất của bạn. Sử dụng các bước sau để tạo và kết nối notebook của bạn với một kernel từ xa –

1. Trên trình khám phá tệp VS Code của bạn, chọn biểu tượng dấu cộng (+) để tạo tệp mới, đặt tên là remote-kernel.ipynb.
2. Mở notebook và chạy một ô (ví dụ: print ("Hello from remote IDE"). VS Code sẽ hiển thị cửa sổ bật lên để cài đặt tiện ích mở rộng Python và Jupyter.
3. Chọn Install/Enable suggested extensions (Cài đặt/Kích hoạt các tiện ích mở rộng được đề xuất).
4. Sau khi các tiện ích mở rộng được cài đặt, VS Code sẽ tự động khởi chạy bộ chọn kernel. Bạn cũng có thể chọn Select Kernel (Chọn Kernel) ở bên phải để xem danh sách các kernel.
5. Đối với các bước tiếp theo, hãy làm theo hướng dẫn cho không gian mà bạn đang kết nối.

**Không gian Code Editor:**
Chọn Python environments… (Môi trường Python…) và chọn từ danh sách các môi trường Python được cung cấp. Sau khi bạn được kết nối, bạn có thể bắt đầu chạy các ô trong notebook của mình.

**Không gian JupyterLab:**
Chọn tùy chọn Existing Jupyter Server… (Máy chủ Jupyter hiện có…) để có trải nghiệm kernel tương tự như môi trường JupyterLab.
Nếu đây là lần đầu tiên kết nối với các không gian JupyterLab, bạn sẽ cần cấu hình máy chủ Jupyter để xem các kernel giống như máy chủ từ xa bằng các bước sau.

1. Chọn Enter the URL of the running Jupyter Server (Nhập URL của Máy chủ Jupyter đang chạy) và nhập http://localhost:8888/jupyterlab/default/lab làm URL và nhấn Enter.
2. Nhập tên hiển thị máy chủ tùy chỉnh, ví dụ: JupyterLab Space Default Server và nhấn Enter. Bây giờ bạn sẽ có thể xem danh sách các kernel có sẵn trên máy chủ Jupyter từ xa. Đối với các kết nối tiếp theo, tên hiển thị này sẽ có sẵn để bạn chọn khi bạn chọn tùy chọn máy chủ Jupyter hiện có.

Hình ảnh sau đây hiển thị toàn bộ quy trình làm việc. Trong ví dụ này, chúng tôi đang chạy một không gian JupyterLab với image SageMaker Distribution, vì vậy chúng tôi có thể xem danh sách các kernel có sẵn trong image.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/14/python-kernels.gif)

Bạn có thể chọn kernel bạn chọn, ví dụ: kernel Python 3, và bạn có thể bắt đầu chạy các ô notebook trên kernel từ xa. Với quyền truy cập vào các kernel được SageMaker quản lý, giờ đây bạn có thể tập trung vào phát triển mô hình thay vì quản lý cơ sở hạ tầng và thời gian chạy, trong khi sử dụng môi trường phát triển mà bạn biết và tin cậy.

## Các phương pháp hay nhất và rào cản bảo vệ (guardrails)

- Tuân thủ nguyên tắc đặc quyền tối thiểu khi cho phép người dùng kết nối từ xa với các ứng dụng không gian SageMaker Studio. SageMaker Studio hỗ trợ lan truyền thẻ (tag) tùy chỉnh, chúng tôi khuyên bạn nên gắn thẻ mỗi người dùng với một mã định danh duy nhất và sử dụng thẻ để cho phép API StartSession chỉ đối với các ứng dụng riêng tư của họ.
- Với tư cách là quản trị viên, nếu bạn muốn vô hiệu hóa tính năng này cho người dùng của mình, bạn có thể thực thi nó bằng cách sử dụng khóa điều kiện sagemaker:RemoteAccess. Sau đây là một chính sách ví dụ.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowCreateSpaceWithRemoteAccessDisabled",
      "Effect": "Allow",
      "Action": ["sagemaker:CreateSpace", "sagemaker:UpdateSpace"],
      "Resource": "*",
      "Condition": {
        "StringEquals": {
          "sagemaker:RemoteAccess": ["DISABLED"]
        }
      }
    },
    {
      "Sid": "AllowCreateSpaceWithNoRemoteAccess",
      "Effect": "Allow",
      "Action": ["sagemaker:CreateSpace", "sagemaker:UpdateSpace"],
      "Resource": "*",
      "Condition": {
        "Null": {
          "sagemaker:RemoteAccess": "true"
        }
      }
    }
  ]
}
```

- Khi kết nối từ xa với các không gian SageMaker Studio từ IDE cục bộ của bạn, hãy lưu ý đến các hạn chế về băng thông. Để có hiệu suất tối ưu, tránh sử dụng kết nối từ xa để chuyển hoặc truy cập các tập dữ liệu lớn. Thay vào đó, hãy sử dụng các phương pháp chuyển dữ liệu được xây dựng cho đám mây và xử lý dữ liệu tại chỗ để tạo điều kiện cho trải nghiệm người dùng mượt mà. Chúng tôi khuyên dùng một phiên bản (instance) có ít nhất 8 GB dung lượng lưu trữ để bắt đầu, và giao diện người dùng SageMaker Studio sẽ đưa ra ngoại lệ nếu bạn chọn một phiên bản nhỏ hơn.

## Dọn dẹp

Nếu bạn đã tạo một miền SageMaker Studio cho mục đích của bài đăng này, hãy nhớ xóa các ứng dụng, không gian, hồ sơ người dùng và miền. Để biết hướng dẫn, hãy xem Xóa một miền.
Đối với các không gian SageMaker Studio, hãy sử dụng chức năng tắt khi nhàn rỗi để tránh phát sinh chi phí cho tính toán khi không sử dụng.

## Kết luận

Tính năng kết nối IDE từ xa cho Amazon SageMaker Studio thu hẹp khoảng cách giữa môi trường phát triển cục bộ và cơ sở hạ tầng ML mạnh mẽ của SageMaker AI. Với các kết nối trực tiếp từ IDE cục bộ đến các không gian SageMaker Studio, các nhà phát triển và nhà khoa học dữ liệu giờ đây có thể:

- Duy trì môi trường phát triển ưa thích của họ trong khi sử dụng tài nguyên tính toán của SageMaker AI
- Sử dụng các tiện ích mở rộng tùy chỉnh, công cụ gỡ lỗi và quy trình làm việc quen thuộc
- Truy cập dữ liệu được quản trị và tài nguyên ML trong các ranh giới bảo mật hiện có
- Chọn giữa các phương pháp kết nối deep linking thuận tiện hoặc AWS Toolkit
- Hoạt động trong các kiểm soát bảo mật và quyền cấp doanh nghiệp

Sự tích hợp này giảm thiểu các rào cản năng suất của việc chuyển đổi ngữ cảnh trong khi tạo điều kiện truy cập an toàn vào các tài nguyên SageMaker AI. Hãy bắt đầu ngay hôm nay với kết nối IDE từ xa của SageMaker Studio để kết nối môi trường phát triển cục bộ của bạn với SageMaker Studio và trải nghiệm quy trình phát triển ML được hợp lý hóa bằng cách sử dụng các công cụ quen thuộc của bạn cùng cơ sở hạ tầng ML mạnh mẽ của SageMaker AI.

## Về các tác giả

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-12-100x100.jpeg)

**Durga Sury** là Kiến trúc sư Giải pháp Cấp cao tại Amazon SageMaker, nơi cô giúp các khách hàng doanh nghiệp xây dựng các hệ thống AI/ML an toàn và có thể mở rộng. Khi không thiết kế các giải pháp, bạn có thể thấy cô ấy tận hưởng những chuyến đi dạo đầy nắng với chú chó của mình, đắm mình trong những cuốn sách trinh thám giết người, hoặc xem các chương trình Netflix yêu thích của cô ấy.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-13.jpeg)

**Edward Sun** là Kỹ sư Phát triển Phần mềm (SDE) Cấp cao làm việc cho SageMaker Studio tại Amazon Web Services. Anh tập trung vào việc xây dựng giải pháp ML tương tác và đơn giản hóa trải nghiệm khách hàng để tích hợp SageMaker Studio với các công nghệ phổ biến trong bối cảnh kỹ thuật dữ liệu và ML. Trong thời gian rảnh rỗi, Edward là một người hâm mộ lớn của cắm trại, đi bộ đường dài và câu cá, và thích dành thời gian với gia đình.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-14-100x119.jpeg)

**Raj Bagwe** là Kiến trúc sư Giải pháp Cấp cao tại Amazon Web Services, có trụ sở tại San Francisco, California. Với hơn 6 năm làm việc tại AWS, anh giúp khách hàng điều hướng các thách thức công nghệ phức tạp và chuyên về Kiến trúc Đám mây, Bảo mật và Di chuyển. Trong thời gian rảnh rỗi, anh huấn luyện một đội robot và chơi bóng chuyền. Anh có thể được liên hệ tại tài khoản X @rajesh_bagwe.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-15-100x133.jpeg)

**Sri Aakash Mandavilli** là Kỹ sư Phần mềm trong nhóm Amazon SageMaker Studio, nơi anh đã xây dựng các sản phẩm sáng tạo từ năm 2021. Anh chuyên phát triển các giải pháp khác nhau trên toàn bộ dịch vụ Studio để nâng cao trải nghiệm phát triển học máy. Ngoài công việc, SriAakash thích duy trì sự năng động thông qua việc đi bộ đường dài, đạp xe và đi bộ đường dài.
