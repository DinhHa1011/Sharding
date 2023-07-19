### Sharding là gì?
- Sharding là một nội dung rất quan trọng để giúp hệ thống giữ dữ liệu trong các resources (tài nguyên) khác nhau theo quy trình sharding
- Từ "Shard" nghĩa là "a small part of a whole" (một phần nhỏ của một tổng thể).
- Hence sharding có nghĩa là chia một phần lớn hơn thành một phần nhỏ hơn
- Trong DBMS, Sharding là một kiểu của Database partitioning trong đó một cơ sở dữ liệu lớn được chia hoặc phân vùng thành dữ liệu nhỏ và các node khác nhau
- Những shard này không chỉ nhỏ hơn, mà cũng nhanh hơn và dễ quản lý hơn
### Cần cho Sharding?
- Xem một cơ sở dữ liệu lớn mà việc sharding chưa được thực hiện
- Cho ví dụ, lấy cơ sở dữ liệu của một trường đại học, nơi mà tất cả bản ghi của sinh viên (present và past) trong toàn trường đại học được duy trì trong một cơ sở dữ liệu duy nhất. Khi đó. nó sẽ chứa số lượng rất rất lớn data, gọi là khoảng 100.000 bản ghi.
- Bây giờ khi cần tìm 1 học sinh từ Database này, mỗi lần phải thực hiện khoảng 100.000 giao dịch để tìm học sinh, điều này thì rất rất tốn kém. Bây giờ hãy xem xét các hồ sơ đai học giống nhau, được chia thành các phần dữ liệu nhỏ hơn dựa trên các năm.
- Bây giờ mỗi phân đoạn dữ liệu chỉ chứa 1000-5000 bản ghi sinh viên. Vì vậy không chỉ database trở nên dễ quản lý hơn nhiều, mà chi phí giao dịch mỗi thời gian cũng giảm đi một yếu tố rất lớn, đó là đạt được bằng Sharding. Do đó đây là lý do tại sao Sharding là cần thiết
### Sharding làm việc như thế nào?
- Trong một hệ thống shard, dữ liệu được phân vùng thành các shard dựa trên một 
tiêu chí định trước. Ví dụ, một sharding scheme có thể phân chia dữ liệu dựa trên địa lý, user ID, hoặc khoảng thời gian. Một dữ liệu được phân vùng, nó đươc phân phối trên nhiều server hoặc nodes. Mỗi server hoặc node chịu trách nhiệm lưu trữ và xử lý một tập hợp con của dữ liệu
- Truy vấn data từ shard database, hệ thống cần biết nơi shard chứa dữ liệu cần thiết. Điều này đạt được khi sử dụng một shard key, nơi mà một mã định danh duy nhất được sử dụng để map data vào shard tương ứng của nó. Khi một query nhận, hệ thống sử dụng shard key để xác định phân đoạn nào chứa dữ liệu cần thiết và sau đó gửi truy vấn đến server hoặc node.
### Tính năng của Sharding
- Sharding làm Database nhỏ
- Sharding làm Database nhanh
- Sharding làm Database dễ quàn lý hơn
- Sharding đôi khi có thể là một hoạt động phức tạp
- Sharding giảm chi phí giao dịch của Database
- Mỗi shard đọc và viết data riêng của nó
- Nhiều database NoSQL cung cấp tính năng auto-sharding
- Lỗi của một shard không ảnh hưởng đến việc xử lý dữ liệu của các phân đoạn khác
### Lợi ích của Sharding:
- Khả năng mở rộng được cải thiện: Sharding cho phép hệ thống mở rộng quy mô theo chiều ngang bằng cách add nhiều server hoặc nodes khi dữ liệu phát triển. Điều này cải thiện khả năng xử lý dữ liệu lớn của data và requesst
- Tăng hiệu suất: Sharding phân phối dữ liệu trên nhiều server hoặc node, giúp cải thiện hiệu suất của hệ thống bằng cách giảm tải trên mỗi server hoặc node. Điều này dẫn đến thời gian phản hồi nhanh hơn và thông lượng tốt hơn
- Khả năng chịu lỗi: Sharding cung cấp một mức độ chịu lỗi vì hệ thống có thể tiếp tục hoạt động ngay cả khi một hoặc nhiều server hoặc node bị lỗi. Điều này là do dữ liệu được sao chép trên nhiều server hoặc node, và nếu một cái fail, những người khác có thể tiếp tục phục vụ các yêu cầu
- Giảm chi phí: Sharding cho phép hệ thống mở rộng theo chiều ngang, điều này có thể tiết kiệm chi phí hơn so với mở rộng theo chiều dọc bằng cách nâng cấp phần cứng. Điều này là do việc mở rộng quy mô theo chiều ngang có thể được thực hiện bằng cách sử dụng phần cứng commodity, thường rẻ hơn so với high-end server.
