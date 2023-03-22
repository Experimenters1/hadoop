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
### 6. HDFS giải quyêt bài toán single-point-of-failure cho namenode bằng cách nào <br>
HDFS giải quyết bài toán single-point-of-failure cho NameNode bằng cách sử dụng một số kỹ thuật sau:<br>
1)Secondary NameNode: HDFS sử dụng một Secondary NameNode để sao lưu metadata từ NameNode. Trong trường hợp NameNode gặp sự cố, Secondary NameNode sẽ được sử dụng để khôi phục lại metadata và bắt đầu hoạt động như một NameNode mới.<br>
2)Hadoop High Availability (HA): Hadoop High Availability là một tính năng mới được giới thiệu trong phiên bản Hadoop 2.0.0, cung cấp một cách tiếp cận khác để giải quyết bài toán single-point-of-failure cho NameNode. Với Hadoop HA, cụm Hadoop được cấu hình với hai NameNode, một NameNode chính và một NameNode phụ. NameNode chính xử lý các yêu cầu ghi và NameNode phụ đảm nhiệm sao chép dữ liệu giữa các NameNode. Khi NameNode chính gặp sự cố, NameNode phụ sẽ lên làm chính và tiếp tục xử lý các yêu cầu ghi.<br>
3)DataNode Heartbeats: HDFS sử dụng giao thức Heartbeat để giám sát tình trạng hoạt động của DataNode. Nếu một DataNode không phản hồi trong khoảng thời gian quy định, NameNode sẽ cho rằng DataNode đó đã gặp sự cố và chuyển dữ liệu sang DataNode khác.<br>
Nhờ các kỹ thuật này, HDFS giải quyết được bài toán single-point-of-failure cho NameNode và đảm bảo tính sẵn sàng và bảo mật của dữ liệu trong cụm Hadoop.
<br>

###
### 7. Vai trò của Job tracker và Task tracker trong hadoop <br>
![image](https://user-images.githubusercontent.com/64000769/226623285-90e80f48-5c1b-4957-b350-57580bc950a0.png)
![image](https://user-images.githubusercontent.com/64000769/226623466-d5f7cf4b-0305-4621-afed-dc682042cf28.png)
![image](https://user-images.githubusercontent.com/64000769/226623675-9d66ea41-6cfd-441f-9022-ce04017e78ef.png)

Job tracker và Task tracker là hai thành phần quan trọng trong kiến trúc của Hadoop. Cả hai đều có vai trò quan trọng trong việc quản lý và thực thi các tác vụ trong Hadoop.<br>

Job tracker là thành phần trung tâm của Hadoop và có nhiệm vụ quản lý tất cả các tác vụ được gửi đến cluster. Nó nhận các yêu cầu xử lý từ người dùng thông qua giao diện dòng lệnh hoặc giao diện người dùng web, sau đó phân phối chúng đến các Task tracker để thực thi. Job tracker cũng theo dõi quá trình thực thi của các tác vụ và cập nhật trạng thái của chúng cho người dùng.<br>

Task tracker là thành phần thực thi các tác vụ trong Hadoop. Nó được cài đặt trên từng node trong cluster và chạy các tác vụ được giao cho nó bởi Job tracker. Task tracker có nhiệm vụ chia nhỏ các tác vụ thành các phần nhỏ hơn gọi là task và thực thi chúng trên các node của cluster. Sau khi task hoàn thành, Task tracker cập nhật trạng thái của chúng cho Job tracker. <br>

Tóm lại, Job tracker và Task tracker là hai thành phần cơ bản trong Hadoop và đóng vai trò quan trọng trong quản lý và thực thi các tác vụ. Job tracker quản lý tất cả các tác vụ và phân phối chúng cho Task tracker, trong khi Task tracker thực thi các tác vụ được giao cho nó và cập nhật trạng thái của chúng cho Job tracker.   <br>
####
### 8. YARN trong hadoop có vai trò gì <br>
![image](https://user-images.githubusercontent.com/64000769/226642582-1ac1d880-0293-48fe-ae38-8acf0e82f804.png)

YARN (Yet Another Resource Negotiator) là một thành phần quan trọng trong Hadoop, chịu trách nhiệm quản lý và phân phối tài nguyên cho các ứng dụng chạy trên Hadoop. Cụ thể, YARN cho phép chia tách hai phần của khả năng xử lý dữ liệu trên Hadoop, đó là phần quản lý tài nguyên và phần xử lý dữ liệu.<br>
Các thành phần chính của YARN bao gồm:<br>
1. Resource Manager: Là thành phần quản lý tài nguyên trung tâm trên một cụm Hadoop. Resource Manager quản lý và cung cấp tài nguyên cho các ứng dụng chạy trên Hadoop bằng cách quản lý Node Manager trên mỗi node của cụm.<br>
2. Node Manager: Là thành phần quản lý tài nguyên trên mỗi node của cụm Hadoop. Node<br>

###
### 9. Hadoop giải quyết bài toán chịu lỗi như thế nào? <br>
Hadoop là một framework mã nguồn mở được sử dụng để xử lý dữ liệu lớn trên các cụm máy tính phân tán. Hadoop giải quyết bài toán chịu lỗi bằng cách sử dụng một số kỹ thuật sau: <br>
1. Replication: Hadoop lưu trữ dữ liệu bằng cách phân chia nó thành các khối và lưu trữ các bản sao của từng khối trên nhiều máy chủ khác nhau. Việc lưu trữ nhiều bản sao này giúp đảm bảo rằng nếu một máy chủ bị lỗi, dữ liệu vẫn có thể được truy xuất từ các bản sao khác. <br>
2. JobTracker và TaskTracker: Hadoop có hai thành phần chính để quản lý và xử lý công việc. JobTracker giám sát các công việc và phân phối chúng cho các TaskTracker trên các nút khác nhau trong cụm. TaskTracker thực hiện các công việc và báo cáo trạng thái của chúng lại cho JobTracker. Nếu một TaskTracker bị lỗi, công việc sẽ được phân phối lại cho một TaskTracker khác.<br>
3. Heartbeat mechanism: Hadoop sử dụng một cơ chế heartbeat để giám sát trạng thái của các thành phần trong cụm. Các thành phần trong cụm gửi thông điệp heartbeat cho nhau để báo cáo trạng thái hoạt động. Nếu một thành phần không gửi heartbeat, Hadoop sẽ coi nó là lỗi và thực hiện các hành động cần thiết để khắc phục sự cố. <br><br>
Tóm lại, Hadoop sử dụng các kỹ thuật sao lưu và phân phối để đảm bảo rằng dữ liệu vẫn có thể truy xuất được nếu một phần của cụm bị lỗi. Nó cũng sử dụng các cơ chế giám sát và phân phối lại công việc để đảm bảo rằng các công việc được hoàn thành một cách hiệu quả, ngay cả khi có lỗi xảy ra trên một hoặc nhiều nút trong cụm. <br>
###
### 10. Kiến trúc của HDFS <br>
![image](https://user-images.githubusercontent.com/64000769/226765977-a9abbde5-1e0c-470c-8050-4347f95d8e80.png)
<br>
HDFS (Hadoop Distributed File System) là một phần của Hadoop, được sử dụng để lưu trữ và quản lý dữ liệu lớn trên các cụm máy tính phân tán. Kiến trúc của HDFS bao gồm các thành phần sau: <br>
1. NameNode: NameNode là thành phần trung tâm của HDFS. Nó làm nhiệm vụ quản lý metadata của hệ thống tập tin, bao gồm thông tin về tên, đường dẫn và kích thước các tệp, cũng như vị trí và trạng thái của các khối dữ liệu trong hệ thống. NameNode cũng giữ một bản sao của metadata trên đĩa cứng.<br>
2. DataNode: DataNode là thành phần lưu trữ thực sự của HDFS. Nó lưu trữ các khối dữ liệu được phân chia từ các tệp, cũng như các bản sao của các khối đó. Mỗi DataNode báo cáo trạng thái của các khối dữ liệu mà nó đang lưu trữ cho NameNode.<br>
3. Block: HDFS phân chia dữ liệu thành các khối (block) có kích thước mặc định là 128MB. Các khối này được lưu trữ trên các DataNode khác nhau trong cụm.<br>
4. Replica: HDFS sử dụng kỹ thuật sao lưu (replication) để đảm bảo tính sẵn sàng và độ tin cậy của dữ liệu. Các bản sao của các khối dữ liệu được tạo ra và được lưu trữ trên nhiều DataNode khác nhau trong cụm.<br>
5. Client: Người dùng hoặc ứng dụng sử dụng Client để truy cập và thao tác với dữ liệu trên HDFS. Client sử dụng API để tạo, đọc và ghi tệp vào HDFS.<br>
6. Rack: Rack là một tập hợp các máy chủ được kết nối với nhau thông qua một switch. HDFS sử dụng thông tin về Rack để đặt các bản sao của các khối dữ liệu trên các Rack khác nhau để đảm bảo tính khả dụng và hiệu suất của dữ liệu.<br> <br>
Tóm lại, HDFS là một hệ thống tập tin phân tán được xây dựng trên các máy chủ và lưu trữ dữ liệu dưới dạng các khối được phân tán trên nhiều DataNode. Việc sao lưu dữ liệu, quản lý metadata và định vị vị trí khối dữ liệu được thực hiện bởi NameNode, còn việc lưu trữ dữ liệu và báo cáo trạng thái của các khối dữ liệu được thực hiện <br>
###
###  11. Nguyên lý thiết kế cốt lõi của HDFS <br>
![image](https://user-images.githubusercontent.com/64000769/226833025-7218a89e-ee10-46f2-bdea-c64725df0fea.png)

HDFS (Hadoop Distributed File System) được thiết kế để lưu trữ và quản lý dữ liệu lớn trên các cụm máy tính phân tán. Các nguyên lý thiết kế cốt lõi của HDFS bao gồm:<br>
1.Phân chia dữ liệu thành các khối (block): HDFS phân chia dữ liệu thành các khối có kích thước mặc định là 128MB. Việc này giúp phân tán dữ liệu trên nhiều máy tính khác nhau trong cụm và làm tăng khả năng xử lý song song của hệ thống.<br>
2.Sao lưu dữ liệu: HDFS sử dụng kỹ thuật sao lưu (replication) để đảm bảo tính sẵn sàng và độ tin cậy của dữ liệu. Các bản sao của các khối dữ liệu được tạo ra và được lưu trữ trên nhiều DataNode khác nhau trong cụm.<br>
3.Quản lý metadata trung tâm: HDFS có một NameNode là thành phần trung tâm quản lý metadata của hệ thống tập tin, bao gồm thông tin về tên, đường dẫn và kích thước các tệp, cũng như vị trí và trạng thái của các khối dữ liệu trong hệ thống. Việc giữ metadata trung tâm giúp cho HDFS có thể xử lý các yêu cầu của người dùng về dữ liệu nhanh chóng và hiệu quả.<br>
4.Xử lý dữ liệu tập trung: HDFS xử lý dữ liệu tập trung bằng cách đưa dữ liệu đến nơi xử lý thay vì đưa code xử lý đến nơi dữ liệu. Việc xử lý tập trung này giúp giảm tải cho mạng và tăng tốc độ xử lý dữ liệu. <br>
5.Hỗ trợ xử lý dữ liệu lớn: HDFS được thiết kế để xử lý dữ liệu lớn, với số lượng khối dữ liệu và lượng dữ liệu rất lớn. HDFS có thể xử lý dữ liệu với tốc độ cao và sử dụng được cho nhiều loại ứng dụng khác nhau. <br> <br>
Tóm lại, các nguyên lý thiết kế cốt lõi của HDFS nhằm tăng tính phân tán, độ tin cậy và tính sẵn sàng của dữ liệu, giúp xử lý dữ liệu tập trung và hỗ trợ xử lý dữ liệu lớn. <br>
###
### 12. Mô thức xử lý dữ liệu MapReduce
![image](https://user-images.githubusercontent.com/64000769/226847013-02eb9a5d-5351-48fd-b4fc-bf1ac217c364.png)
<br>
MapReduce là một mô hình lập trình để xử lý dữ liệu phân tán, được phát triển bởi Google và được Hadoop triển khai lại. Mô thức xử lý dữ liệu MapReduce bao gồm hai giai đoạn chính là Map và Reduce.<br> <br>
1. Giai đoạn Map: <br>
Trong giai đoạn này, dữ liệu được đọc từ HDFS và được xử lý bởi các hàm Map. Hàm Map được định nghĩa bởi người dùng và thực hiện việc chuyển đổi dữ liệu vào một cặp khóa-giá trị (key- value pair). Các khóa-giá trị này được sử dụng để phân tán dữ liệu đến các tác vụ Reduce khác nhau. Sau khi tác vụ Map hoàn tất, các cặp khóa-giá trị được sắp xếp và gom nhóm lại theo khóa chung.<br>



















      
