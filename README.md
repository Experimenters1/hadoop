# Hadoop
#
### 1. Hadoop giải quyết bài toán mở rộng như thế nào?
Hadoop giải quyết bài toán mở rộng (scalability) bằng cách áp dụng các kỹ thuật sau: <br>
  +) Phân tán dữ liệu: Hadoop phân tán dữ liệu trên nhiều nút trong một cụm Hadoop. Khi có thêm nút được thêm vào cụm, dữ liệu sẽ được phân bổ lại trên tất cả các nút, giúp tăng tính mở rộng của hệ thống. <br>
  ![image](https://user-images.githubusercontent.com/64000769/226306082-56e4cb1f-d406-43eb-ab7b-8a5577298c29.png)

  +) Xử lý phân tán: Hadoop sử dụng MapReduce để xử lý dữ liệu phân tán trên nhiều nút. MapReduce phân tách tác vụ xử lý thành các công việc nhỏ hơn và thực hiện chúng trên nhiều nút khác nhau, giúp tăng tính mở rộng của hệ thống. <br>
  ![image](https://user-images.githubusercontent.com/64000769/226303536-0d64645a-8b90-464e-8095-bf930c7db324.png)
<br>
 +) Hadoop YARN: YARN (Yet Another Resource Negotiator) là một kiến trúc quản lý tài nguyên trong Hadoop, cho phép tách việc quản lý tài nguyên và việc xử lý dữ liệu. YARN giúp tăng tính mở rộng của Hadoop bằng cách cung cấp khả năng xử lý các ứng dụng khác nhau trên cùng một cụm. <br>
 ![image](https://user-images.githubusercontent.com/64000769/226304133-6d0e8edd-197f-435c-b17c-2624262292e0.png)
 <br>
 +)Sử dụng các công nghệ mới: Hadoop sử dụng các công nghệ mới nhất để tăng tính mở rộng, chẳng hạn như Apache Spark, một công cụ xử lý dữ liệu phân tán với hiệu suất cao hơn MapReduce.<br>
 ![image](https://user-images.githubusercontent.com/64000769/226304508-af45b349-2c17-402e-81f0-50cae68e926d.png)
<br>
Nhờ các kỹ thuật này, Hadoop có thể mở rộng để xử lý các tập dữ liệu lớn và phức tạp hơn, đáp ứng nhu cầu của các doanh nghiệp và tổ chức.
###
### 2. Mô tả cách thức 1 client đọc dữ liệu trên HDFS
HDFS (Hadoop Distributed File System) là một hệ thống lưu trữ phân tán dành cho các ứng dụng Big Data. Để đọc dữ liệu từ HDFS, một client cần tuân thủ các bước sau: <br>
#
![image](https://user-images.githubusercontent.com/64000769/226307185-ee015b9e-d1a6-4d72-90df-d8d13d79c416.png)

1) Tạo kết nối tới HDFS: Client cần thiết lập kết nối với HDFS thông qua một giao thức như HDFS API, WebHDFS hoặc command-line interface (CLI).<br>
2) Xác định tệp cần đọc: Client cần xác định đường dẫn tới tệp tin trên HDFS mà họ muốn đọc.<br>
3) Xác định phân vùng cần đọc: Khi tệp được lưu trữ trên HDFS, nó được phân tách thành nhiều phân vùng. Client cần xác định phân vùng hoặc các phân vùng mà nó cần đọc. <br>
4) Tạo yêu cầu đọc dữ liệu: Client tạo một yêu cầu đọc dữ liệu bao gồm đường dẫn tới tệp tin, các phân vùng cần đọc và các thông số cấu hình liên quan đến việc đọc dữ liệu như buffer size.<br>
5) Gửi yêu cầu đến NameNode: Yêu cầu đọc dữ liệu được gửi đến NameNode, nơi mà nó được định tuyến đến DataNode chứa các phân vùng dữ liệu được yêu cầu.<br>
6) Đọc dữ liệu từ DataNode: DataNode sẽ trả về dữ liệu đọc được từ phân vùng yêu cầu đến Client.<br>
7) Xử lý dữ liệu: Dữ liệu đọc được từ HDFS sẽ được Client xử lý theo yêu cầu của ứng dụng.<br>
8) Đóng kết nối: Khi xử lý dữ liệu hoàn tất, Client cần đóng kết nối với HDFS.<br>
Quá trình đọc dữ liệu từ HDFS tùy thuộc vào kiểu ứng dụng và giao thức sử dụng. Tuy nhiên, quá trình trên cung cấp một khái niệm chung về cách một client có thể đọc dữ liệu từ HDFS.<br>
###
### 3. Mô tả cách thức 1 client ghi dữ liệu trên HDFS
Để ghi dữ liệu lên HDFS, một client cần thực hiện các bước sau:<br>
1)Tạo kết nối tới HDFS: Client cần thiết lập kết nối với HDFS thông qua một giao thức như HDFS API, WebHDFS hoặc command-line interface (CLI).<br>
2)Tạo tệp cần ghi: Client tạo một tệp tin mới hoặc mở một tệp tin đã tồn tại để ghi dữ liệu vào.<br>
3)Ghi dữ liệu vào tệp tin: Client sử dụng các phương thức cung cấp bởi HDFS API hoặc WebHDFS để ghi dữ liệu vào tệp tin. Trong quá trình ghi, dữ liệu sẽ được chia thành các khối và ghi lên các DataNode.<br>
4)Xác định phân vùng cần ghi: Tương tự như khi đọc dữ liệu, tệp được lưu trữ trên HDFS sẽ được chia thành nhiều phân vùng. Client cần xác định phân vùng hoặc các phân vùng mà nó muốn ghi vào.<br>
5)Gửi yêu cầu ghi dữ liệu đến NameNode: Yêu cầu ghi dữ liệu được gửi đến NameNode, nơi mà nó được định tuyến đến các DataNode chứa các phân vùng dữ liệu được yêu cầu.<br>
6)Ghi dữ liệu vào DataNode: Dữ liệu được ghi vào các DataNode và được lưu trữ theo các phân vùng.<br>
7)Đóng tệp tin: Sau khi hoàn tất việc ghi dữ liệu, Client cần đóng tệp tin để lưu lại các thay đổi.<br>
8)Đóng kết nối: Khi việc ghi dữ liệu hoàn tất và tệp tin được đóng, Client cần đóng kết nối với HDFS.<br>
Quá trình ghi dữ liệu lên HDFS cũng tùy thuộc vào kiểu ứng dụng và giao thức sử dụng. Tuy nhiên, quá trình trên cung cấp một khái niệm chung về cách một client có thể ghi dữ liệu lên HDFS.<br>

###
### 4. Cơ chế chịu lỗi của data node trong HDFS

![image](https://user-images.githubusercontent.com/64000769/226312600-e5913ba4-4889-4811-a7e5-b126e56828b6.png)
<br>
DataNode trong HDFS có nhiệm vụ lưu trữ dữ liệu và phục vụ cho việc đọc và ghi dữ liệu. Tuy nhiên, nếu DataNode gặp sự cố, các cơ chế chịu lỗi sẽ được triển khai để đảm bảo tính sẵn sàng và bảo mật của hệ thống HDFS.<br>
Dưới đây là các cơ chế chịu lỗi của DataNode trong HDFS: <br>
1)Hệ thống sao lưu: Dữ liệu trong HDFS được lưu trữ theo cơ chế sao lưu. Mỗi phân vùng dữ liệu được sao chép sang các DataNode khác nhau để đảm bảo tính sẵn sàng của dữ liệu khi có sự cố xảy ra.<br>
2)Kiểm tra tính nguyên vẹn dữ liệu: HDFS sử dụng một thuật toán kiểm tra tính nguyên vẹn dữ liệu để phát hiện và khắc phục các lỗi trong quá trình truyền tải dữ liệu. Nếu DataNode phát hiện bất kỳ lỗi nào trong quá trình truyền tải dữ liệu, nó sẽ yêu cầu các DataNode khác sao chép lại dữ liệu.<br>
3)Chuyển tiếp dữ liệu: Nếu DataNode gặp sự cố, nó sẽ thông báo cho các DataNode khác về sự cố này. Các DataNode khác sẽ chuyển tiếp các yêu cầu của Client đến các DataNode khác chứa dữ liệu thay vì gửi yêu cầu trực tiếp đến DataNode gặp sự cố.<br>
4)Xác thực: HDFS sử dụng các cơ chế xác thực để đảm bảo tính bảo mật của dữ liệu. Khi một DataNode gặp sự cố, các DataNode khác sẽ tiếp tục sử dụng các cơ chế xác thực để đảm bảo rằng dữ liệu không bị truy cập hoặc thay đổi bởi người dùng không được ủy quyền.<br>
5)Cập nhật metadata: Nếu DataNode gặp sự cố, NameNode sẽ cập nhật metadata để đảm bảo tính nhất quán của hệ thống HDFS. NameNode sẽ loại bỏ DataNode gặp sự cố khỏi danh sách các DataNode đang hoạt động và sử dụng các DataNode khác để cung cấp dịch vụ cho Client.<br>
Tóm lại, HDFS có các cơ chế chịu lỗi để đảm bảo tính sẵn sàng, bảo mật và nhất quán của dữ liệu khi DataNode gặp sự cố. Các cơ chế này giúp đảm
###

### 5. Cơ chế nhân bản dữ liệu trong HDFS
Hadoop Distributed File System (HDFS) là một hệ thống lưu trữ phân tán, có khả năng nhân bản dữ liệu để đảm bảo tính sẵn sàng và bảo mật của dữ liệu. Dưới đây là cơ chế nhân bản dữ liệu trong HDFS: <br><br>
![image](https://user-images.githubusercontent.com/64000769/226619755-93cc4fe8-944d-4dfd-963d-d4fe36707b6a.png)
<br>
1)Block Size: HDFS chia các tập tin thành các khối (block) có kích thước mặc định là 128MB. Việc chia dữ liệu thành các khối giúp dễ dàng quản lý và nhân bản dữ liệu.<br>
2)Replication Factor: HDFS nhân bản mỗi khối dữ liệu trên nhiều DataNode (mặc định là 3 DataNode). Số lượng DataNode được chọn để nhân bản được xác định bởi Replication Factor. Các bản sao này được lưu trữ trên các DataNode khác nhau trong cụm Hadoop.<br>
3)DataNode Placement: HDFS chọn các DataNode để lưu trữ các bản sao của khối dữ liệu dựa trên vị trí vật lý của các DataNode và tránh lưu trữ các bản sao trên cùng một máy chủ hoặc cùng một giá trị rack.<br>
4)DataNode Failure: Nếu một DataNode gặp sự cố, các bản sao của khối dữ liệu được lưu trữ trên DataNode khác sẽ được sử dụng để đảm bảo tính sẵn sàng và bảo mật của dữ liệu.<br>
5)Block Replication: Khi một DataNode mới được thêm vào cụm, HDFS sẽ tự động nhân bản các khối dữ liệu sang DataNode mới đó để đảm bảo rằng số lượng bản sao đáp ứng yêu cầu của Replication Factor.<br>
Cơ chế nhân bản dữ liệu trong HDFS đảm bảo tính sẵn sàng và bảo mật của dữ liệu bằng cách lưu trữ các bản sao của dữ liệu trên nhiều DataNode khác nhau. Nếu một DataNode gặp sự cố, các bản sao của dữ liệu sẽ được sử dụng để đảm bảo rằng dữ liệu vẫn có sẵn và an toàn.<br><br>

####






      
