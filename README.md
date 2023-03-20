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





      
