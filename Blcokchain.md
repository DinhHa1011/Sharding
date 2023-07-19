### Blockchain overview
- Blcokchain là một database phân tán (phi tập trung) mà trong đó các dữ liệu được lưu trữ dưới dạng block. Body của block mang theo các transactions trên dữ liệu (như state machine). Block được kết nối với nhau theo dạng linked list (danh sách liên kết) dưới dạng mã hóa SHA256. Mã hóa của một block bao gồm cả địa chỉ của block trước và body của chính nó nên khi một block được add vào, nó không thể thay đổi cũng như tái sắp xếp
- Blockchain nó như history thường thấy trong Git. Mỗi commit là một block => dễ dàng xem được commit cũ cũng như track xem ai làm gì trên source code của mình
- Blockchain không nằm một nơi như Git mà nằm trên các node và nó ngang hàng với nhau
### Nguyên lý hoạt động của blockchain
#### 1. Nguyên lý mã hóa
- Trong hệ thống ngân hàng, biết các giao dịch và số dư tài khoản của riêng mình thì trên blockchain của bitcoin bạn có thể xem các giao dịch của tất cả mọi người.
- Mạng lưới bitcoin là mạng lưới phân tán không cần bên thứ 3 đóng vai trò trung gian xử lý giao dịch. Hệ thống blockchain được thiết kế theo cách không yêu cầu sự tin cậy và đảm bảo bởi độ tin cậy có được thông qua các hàm mã hóa toán học đặc biệt
- Để có thể thực hiện các giao dịch trên blockchain, bạn cần một phần mềm sẽ cho phép bạn lưu trữ và trao đổi các đồng bitcoin của bạn gọi là ví điện tử. Ví điện tử này sẽ được bảo vệ bằng một phương pháp mã hóa đặc biệt đó là sử dụng một cặp khóa bảo mật duy nhất: khóa riêng tư (private key) và khóa công khai (public key)
#### 2. Quy tắc của blcokchain
- Mỗi nút trong blockchain đều đang lưu giữ một bản sao của sổ kế toán. Do vậy, mỗi nút đều biết số dư tài khoản của bạn là bao nhiêu. Hệ thống blockchain chỉ ghi lại mỗi giao dịch được yêu cầu chứ không hề theo dõi số dư tài khoản của bạn.
- Để biết số dư trên ví điện tử của mình thì bạn cần xác thực và xác nhận tất cả các giao dịch đã diễn ra trên mạng lưới mà có liên quan tới ví điện tử của bạn.
- Việc xác minh “số dư” này được thực hiện nhờ các tính toán dựa vào liên kết đến các giao dịch trước đó. Nhìn vào hình trên, để gửi 10btc cho John, Mary cần tạo yêu cầu giao dịch bao gồm các liên kết đến các giao dịch đã diễn ra trước đó với tổng số dư bằng hoặc vượt quá 10 btc.
- Các liên kết này được xem như là giá trị đầu vào, các nút trong mạng lưới sẽ xác minh xem tổng số tiền của các giao dịch này bằng hoặc vượt quá 10 btc không. Tất cả điều này được thực hiện tự động trong ví điện tử của Mary và được kiểm tra bởi các nút trên mạng lưới Bitcoin, Mary chỉ gửi một giao dịch 10 bitcoin tới ví của John bằng khóa công khai của John.
- Vậy, làm thế nào hệ thống có thể tin tưởng các giao dịch đầu vào này và xác thực tính hợp lệ của chúng?
- Thực tế là các nút sẽ kiểm tra tất cả các giao dịch có liên quan đến ví tiền điện tử bạn sử dụng trước đó để gửi Bitcoin (BTC) thông qua việc tham chiếu các lịch sử giao dịch. Có một bản ghi sẽ lưu trữ số BTC chưa được dùng và được các nút mạng lưu giữ giúp đơn giản hóa và tăng tốc quá trình xác minh. Vì thế, các ví tiền điện tử tránh được tình trạng chi tiêu đúp giao dịch.
  => “Như vậy sở hữu Bitcoin có nghĩa là có các giao dịch được lưu trong sổ kế toán liên hệ đến địa chỉ ví của bạn mà chưa được sử dụng làm giao dịch đầu vào.”
- Mã nguồn trên mạng lưới Bitcoin là nguồn mở, có nghĩa là bất kỳ ai có máy tính kết nối được internet đều có thể tham gia vào mạng lưới và thực hiện giao dịch.
- Tuy nhiên, nếu có bất kỳ một lỗi nào trong mã nguồn được sử dụng để phát thông báo yêu cầu giao dịch thì các Bitcoin liên quan sẽ bị mất vĩnh viễn.
#### 3. Nguyên lý tạo khối
