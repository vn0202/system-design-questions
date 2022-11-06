Thiết kế 1 CSDL thời gian thực
===

<!--ts-->
* [Thiết kế 1 cơ sở dữ liệu thời gian thực](#design-a-realtime-database)
* [Báo cáo vấn đề ](#problem-statement)
* [Các yêu cầu](#requirements)
   * [Yêu cầu cốt lõi](#core-requirements)
   * [Các yêu cầu cấp cao](#high-level-requirements)
   * [Các yêu cầu vi mô](#micro-requirements)
* [Đầu ra](#output)
   * [Tài liệu thiết kế ](#design-document)
   * [Nguyên mẫu](#prototype)
      * [Gợi ý công nghệ ngăn xếp](#recommended-tech-stack)
      * [Hãy ghi nhớ](#keep-in-mind)
* [Kết qủa ](#outcome)
   * [Bạn sẽ học ](#youll-learn)
* [Chia sẻ và cảm ơn ](#share-and-shoutout)
<!--te-->

# Báo cáo vấn đề

Thiết kế 1 CSDL KV thời gian thực hiện đại cái mà gửi các cập nhật thời gian thực tới tất cả các người dùng được kết nối với nó. Người dùng đăng ký tới các bảng và bất cứ khi nào 1 KV được thêm, sửa hay xóa các thay đổi được thông báo tới tất cả các người dùng, cập nhật các ứng dụng / view trong thời gian thực

![Relog - Realtime Database](https://user-images.githubusercontent.com/4745789/139183521-43e7a5c8-a629-4f85-9584-21dd873d0ade.png)

# Các yêu cầu 

<!--rs-->
*Báo cáo vấn đề là cái để bắt đầu, hãy sáng tạo và đào sâu vào chi tiết sản phẩm và thêm các rằng buộc và các đặc tính bạn nghĩ nó quan trọng
<!--re-->

## Các yêu cầu lõi

 - Cập nhật được thực hiện bởi 1 người dùng trong 1 bảng được thông báo tới tất cả các người dùng đăng ký nó
 - Một bảng có tối đa **100** người đăng ký
 - Có **1 triệu** bảng .
 - Một người dùng có thể đăng ký **1** bảng ở 1 thời điểm.
 
 - one user can subscribe to **1** table at one time

##  Các yêu cầu cấp cao
<!--hs-->
- Tạo các thành phần cấp cao của bạn tương tác với **tính khả dụng cao** 
- Đảm bảo dữ liệu của bạn là **kiên cố** cho dù vấn đề gì xảy ra.
- Định nghĩa cách hệ thống của bạn sử lý trong khi **phóng to** và **thu nhỏ** quy mô.
- Làm cho hệ thống của bạn **hiệu quả về chi phí** và cung cấp 1 do tương tự 
- Mô tả **kế hoạch hiệu suất của bạnơ** cái mà giúp bạn có 1 quyết định thiết kế đúng đắn.
- Nghĩ về các dịch vụ khác tương tác với dịch vụ của bạn.
- make your high-level components operate with **high availability**

<!--he-->

##  Các yêu cầu vi mô
<!--ms-->
- đảm bảo dữ liệu trong hệ thống của bạn không bao giờ rơi vào trạng thái không nhất quán.
- Đảm bảo hệ thống của bạn là **không có lỗi** (nếu có thể )
- Đảm bảo rằng thông lượng của hệ thống của bạn sẽ không bị ảnh hưởng bởi **locking**, nếu có, hãy phát biểu nó ảnh hưởng như thế nào.
<!--me-->

# Đầu ra 

## Tài liệu thiết kế.
<!--ds-->
 Tạo một **tài liệu thiết kế** của hệ thống/đặc tính này phát biểu rằng tất cả các quyết định thiết kế quan trọng, các chi phí, các thành phần, các dịch vụ và các thông tin liên lạc. Cũng chỉ cách mà hệ thống xử lý ở quy mô và cái gì cuối cùng sẽ trở thành điểm nghẽn.

**Đừng** tạo ra các thành phần không cần thiết, cái chỉ làm cho thiết kế của bạn trông phức tạp hơn. MỘt thiết kế tốt là **luông đơn giản và lịch sự**. Cách tốt nhất để nghĩ về nó là nếu bạn tạo ra cá tiến trình/máy/ cơ sở hạ tầng riêng lẻ và bạn sẽ phải tự code nó . bạn  vẫn muốn làm ?
<!--de-->

## Nguyên mẫu 

Để hiểu các sắc thái và nội dung bên trong của hệ thống, hãy xây dựng nguyên mẫu: 
 - Một giao diện để đăng ký 1 bảng và thực thi các thao tác CRUD 
 - Sử dụng lưu trữ KV cái mà được xây dựng như 1 phần của [Design SQL backed KV Store](sql-kv.md)
 - Mô phỏng các đăng ký đa người dùng tới bảng thông qua các phiên trình duyệt khác nhau 


###  Gợi ý công nghệ ngăn xếp 

Đây là 2 gợi ý công nghệ stack cho xây dựng nguyên mẫu này.

|Which|Options|
|-----|-----|
|Language|NodeJS, Golang or any that supports SocketIO|
|Framework|SocketIO|
|Database|KV store built by you, or any database of your liking|

###  hãy ghi nhớ 
Có những cạm bẫy phổ biến bạn cần nhớ khi xây dựng nguyên mẫu này : 
- 

These are the common pitfalls that you should keep in mind while you are building this prototype

- fan-outs take time
- Không cấp bản cập nhật trước khi duy trì nó

# Kết qủa 

##  Bạn sẽ học 

- Giao tiếp thực bằng cách sử dụng SocketIO
- Mở rộng sockets tới hàng triệu người đồng thời. 
- xây dựng CSDL thời gian thực với trải nghiệm người dùng tuyệt vời 


<!--fs-->
#  Chia sẻ và cảm ơn 
Nếu bạn thấy hướng dẫn này hữu ích, làm owmn: 
- Chia sẻ nó với bạn và cộng sự của bạn 
- đánh giá respo này để nó có thể tiếp cận với nhiều thính giả hơn 
- Cho tôi 1 lời cảm ơn trên Twitter  [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).

Hướng dẫn này là 1 phần của  [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) -Một lớp học chuyên sâu giúp bạn trở lên tốt hơn thiết kế 1 hệ thống quy mô, chịu lỗi và tính khả dụng cao  
<!--fe-->