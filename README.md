# Hadoop
#
###1. Hadoop giải quyết bài toán mở rộng như thế nào?
Hadoop giải quyết bài toán mở rộng (scalability) bằng cách áp dụng các kỹ thuật sau: <br>
  +) Phân tán dữ liệu: Hadoop phân tán dữ liệu trên nhiều nút trong một cụm Hadoop. Khi có thêm nút được thêm vào cụm, dữ liệu sẽ được phân bổ lại trên tất cả các nút, giúp tăng tính mở rộng của hệ thống. <br>
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
#
