Thiết kế thông báo tin nhắn mới chưa đọc 
===

<!--ts-->
* [Thiết kế chỉ thông báo tin nhắn chưa đọc](#design-newly-unread-message-indicator)
* [Báo cáo vấn đề ](#problem-statement)
* [Các yêu cầu](#requirements)
   * [Các yêu cầu lõi](#core-requirements)
   * [Các yêu cầu cấp cao](#high-level-requirements)
   * [Các yêu cầu vi mô](#micro-requirements)
* [Đầu ra](#output)
   * [Tài liệu thiết kế ](#design-document)
   * [Nguyên mẫu ](#prototype)
      * [Gợi ý công nghệ stack](#recommended-tech-stack)
      * [Ghi nhớ](#keep-in-mind)
* [Kết quả](#outcome)
   * [Đầu ra ](#youll-learn)
* [Chia sẻ và cảm ơn ](#share-and-shoutout)
<!--te-->

# Báo cáo vấn đề

Dịch vụ/đặc tính này sẽ thông báo người dùng về sự xuất hiện của tin nhắn mới. Số lượng trong trình thông báo là tổng số các người dùng riêng người mà gửi tin nhắn tới người dùng. Trình thông báo sẽ là `0` ngay khi người dùng bấm vào nút - thừa nhận rằng cô ấy/anh ấy đã biết tin nhắn này. 

Trình thông báo không nói có bao nhiêu tin nhắn chưa đọc trong tổng số, nhưng tôt hơn, nó đơn giản chỉ thông báo rằng những tin nhắn mới vừa được nhận, ngay khi người dùng click vào nút anh ấy/ cô ấy thừa nhận sự hiện diện và bởi vậy trình báo sẽ về 0.

Một người dùng có thể có hàng nghìn tin nhắn chưa đọc nhưng số `3` trong hình ảnh dưới đây cái mà có 3 tin nhắn từ 3 người khác nhau mà cô ấy/ anh ấy vừa nhận được.

![Relog New Message Indicator](https://user-images.githubusercontent.com/4745789/139584929-5e00fd58-c731-4f91-aaa8-7383acd99ff4.png)

# Các yêu cầu 

<!--rs-->
*Báo cáo vấn đề là cái để bắt đầu, hãy sáng tạo và đào sâu vào chi tiết sản phẩm và thêm các ràng buộc và các đặc tính bạn nghĩ nó cần thiết.*
<!--re-->

## Các yêu cầu lõi 

- Thể hiện **trình thông báo** thông báo người dùng về các trình thông báo chưa đoc mới.
- Mạng xã hội có **1 triệu** các người dùng hoạt động hàng ngày.
- Thời gian hồi đáp của 1 dịch vụ nên là **thấp** nhất có thể 
- Cập nhật trình thông báo nên xảy ra trong thời gian thực 

 
##  Các yêu cầu cấp cao 
<!--hs-->
- Làm cho các thành phần cao cấp của bạn tương tác với **tính khả dụng cao**
- Đảm bảo dữ liệu trong hệ thống của bạn là **bền vững**, cho dù vấn đề gì xẩy ra.
- Định nghĩa hệ thống của bạn cư xử như thế nào trong khi **mở rộng** và **thu nhỏ** quy mô.
- Làm cho hệ thống của bạn **hiệu quả về chi phí** và cung cấp các lý do tương tự 
- Mô tả **kế hoạch hiệu suất của bạn** cái giúp bạn có quyết định thiết kế tốt 
- Nghĩ về cách các dịch vụ khác sẽ tương tác với dịch vụ của bạn

<!--he-->

##  Các  yêu cầu lõi 
<!--ms-->
- Đảm bảo dữ liệu trong hệ thống của bạn không bao giờ rơi vào trạng thái không nhất quán.
- Đảm bảo dữ liệu trong hệ thống của bạn là **không có lỗi**( nếu có thể)
- Đảm bảo thông lượng hệ thống của bạn là không bị ảnh hưởng bởi khóa, nếu có hãy phát biểu nó ảnh hưởng như nào.
<!--me-->

# Đầu ra 

## Tài liệu thiết kế 
<!--ds-->

Tạo 1 **tài liệu thiết kế** của hệ thống/đặc tính này phát biểu rằng tất cả các quyết định thiêt kế quan trọng, các chi phí đánh đổi , các thành phần, các dịch vụ và các thông tin liên lạc.Đồng thời cũng chỉ ra hệ thống của bạn sẽ xử lý như nào ở quy mô lớn và cái gì cuối cùng sẽ thành điểm nghẽn.

**Dừng** tạo ra các thành phần không cần thiết, cái mà chỉ làm cho hệ thống của bạn trông phức tạp hơn. Một thiết kế tôt luôn **đơn giản và lịch sự**. Một cách tốt để nghĩ về nó là nếu như bạn tạo ra các tiến trình/máy/cơ sở hạ tầng rieeng cho mỗi thành phần và bạn sẽ phải tự viết mã cho nó. bạn vẫn muốn làm nữa?

<!--de-->

## Nguyên mẫu 

Để hiểu các sắc thái và nội dung bên trọng của hệ thống này, hãy xây dựng nguyên mẫu 
- Mô phỏng trình thông báo tin nhắn mới chưa đọc trên máy cục bộ 
- cập nhật bộ đếm thời gian thực 



###  Gợi ý công nghệ stack 

Đây là 1 gợi ý công nghệ stack cho xây dựng nguyên mẫu này 



|Which|Options|
|-----|-----|
|Language|Golang, Java, NodeJS, C++|
|Framework|SocketIO|
|Database|Pick your favourite|

###  Ghi nhớ 

Có những cạm bẫy phổ biến bạn cần ghi nhớ khi xây dựng nguyên mẫu này:

- các tin nhắn mới chưa đọc là khác với các tin nhắn chưa đọc 
- Giữ dữ liệu lưu trữ nhanh hơn để làm cho hệ thống hoạt động ở quy mô lớn 



# Kêt qủa 

##  Bạn sẽ học 

- Thiết kế lược đồ CSDL 
- Thiết kế dịch vụ tập trung vào trải nghiệm người dùng độ trễ thời gian thấp 

<!--fs-->
# Chia sẻ và cảm ơn 

Nếu bạn thấy hướng dẫn này hữu ích, làm ơn: 

- chia sẻ nó với bạn bè và đồng nghiệp của bạn 
- Đánh giá repo này và giúp nó tiếp cận với đông đảo thính giả 
- Cho tôi 1 lời cảm ơn trên [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).
Hướng dẫn này là 1 phần của [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) - Một lớp học master nơi giúp bạn trở lên giỏi ở thiết kế hệ thống quy mô lớn, chịu lỗi và tính khả dụng cao 
<!--fe-->