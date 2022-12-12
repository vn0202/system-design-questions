Thiết kế 1 trình báo chỉ số trực tuyến ngoại tuyên 
===

<!--ts-->
* [Thiết kế 1 trình báo chỉ số trực tuyến ngoại tuyến](#design-an-online-offline-indicator)
* [Báo cáo vấn đề](#problem-statement)
* [Các yêu cầu ](#requirements)
   * [Các yêu cầu lõi ](#core-requirements)
   * [Các yêu cầu cấp cao ](#high-level-requirements)
   * [Các yêu cầu vi mô](#micro-requirements)
* [Đầu ra ](#output)
   * [Tài liệu thiết kế ](#design-document)
   * [Nguyên mẫu ](#prototype)
      * [Gợi ý công nghệ stack ](#recommended-tech-stack)
      * [Ghi nhớ](#keep-in-mind)
* [Kết quả](#outcome)
   * [Bạn sẽ học ](#youll-learn)
* [Chia sẻ và cảm ơn ](#share-and-shoutout)
<!--te-->

# Báo cáo vấn đề 

Tưởng tượng bạn đang xây dụng 1 ứng dụng chat trong đó người dùng có thể chat với bất kỳ người dùng nào, cung cấp họ kết nối. Cho 1 người dùng khởi tạo  chat, nó luôn luôn hữu ích nếu chúng ta thể hiện xem ai đang online


Trong hướng dẫn này, hãy thiết kế 1 hệ thông cái mà chỉ rõ những ai đang online bây giờ. Báo cáo vấn đề vi mô là cái đơn giản như câu trả lời cho câu hỏi - Cung cấp 1 người dùng, trả về cô ấy/ anh ấy đang online hay không 

![Designing Online Offline Indicator](https://user-images.githubusercontent.com/4745789/138017480-1f7c30ce-50f2-4a50-99b5-1cf7f0778caa.png)

# Các yêu cầu 


<!--rs-->
*Báo cáo vấn đề là cái để bắt đầu, hãy sáng tạo và đào sâu vào chi tiết sản phẩm và thêm các đặc tính sản phẩm và thêm các ràng buộc bạn nghĩ nó quan trọng*
<!--re-->

## Các yêu cầu lõi 

- Nên cập nhật trạng thái  online của người dùng trong **10 giây** của người dùng online
- Có thể **lineant** khi đánh dấu người dùng ngoại tuyến.
- Nên mở rộng quy mô **5 trịệu** người dùng hoạt động mỗi giây 
- Người dùng nên nhìn thấy chính xác trạng thái của bất kỳ người dùng nào **cuối cùng**

 

##  Các yêu cầu cấp cao 
<!--hs-->

- Làm cho các thành phần cấp cao hệ thống của bạn tương tác với **tính khả dụng cao**
- Đảm bảo dữ liệu trong hệ thống của bạn là **bền vững**, cho dù vấn đề gì xẩy ra. 
- Định nghĩa cách mà hệ thống của bạn sẽ cư xử trong khi **mở rộng** và **thu nhỏ** quy mô.
- Làm cho hệ thống của bạn **hiệu qủa về chi phí** và cung cấp 1 lý do tương tự 
- Mô tả kê hoạch hiệu suất của bạn, cái mà giúp bạn có 1 quyêt định thiêt kế đúng đắn.
- Nghĩ về cách mà các dịch vụ khác sẽ tương tác với dịch vụ của bạn 

<!--he-->

##  Các yêu cầu vi mô 
<!--ms-->

- Đảm bảo dữ liệu trong hệ thống của bạn là **không bao giờ** rơi vào trạng thái không nhất quán.
- Đảm bảo hệ thống của bạn là **không có lỗi** (nếu có thể )
- Đảm bảo rằng thông lượng hệ thống của bạn không bị ảnh hưởng bởi khóa và nếu có hãy phát biểu nó ảnh hưởng như nào
<!--me-->

# Đầu ra 

## Tài liệu thiết kế 
<!--ds-->
 Tạo 1 **tài liệu thiết kê** của hệ thống/đặc tính này phát biểu rằng tất cả các quyết định thiết kế quan trọng, các đánh đổi, các thành phần, các dịch vụ và các thông tin liên lạc. Cũng chỉ rõ hệ thống của bạn sẽ xử lsy như nào ở quy mô lớn và cái gì cuối cùng sẽ trở thành điểm nghẽn. 

**Đừng** tạo ra các thành phần không cần thiết, cái mà chỉ làm cho thiết kế của bạn trông phức tạp. Một thiết kế tốt luôn **đơn giản và lích sự**. Một cách tốt để nghĩ về nó là nếu bạn tạo ra các máy/tiến trình/ cơ sở hạ tầng riêng cho từng thành phần và bạn sẽ phải viết mã cho nó. Bạn vẫn muốn viết? 
<!--de-->

## Nguyên mẫu 

Để hiểu các sắc thái và nội dung của hệ thống nãy, hãy xây dựng nguyên mẫu: 
- Hiển thị danh sách người dùng 
- Thể hiện nếu 1 người dùng cụ thể đang hoạt động hay ofline 
- Danh sách người dùng là được nhóm để người dùng online được thể hiện đầu tiên và sau đó là các người dùng offline
- Nếu người dùng offline, cũng hiển thị **offline cách đây x phút** 
- 



###  Gợi ý công nghệ stack 

Đây là gợi ý công nghệ stack cho xây dựng nguyên mẫu này 


|Which|Options|
|-----|-----|
|Language|NodeJS, or any language that supports SocketIO|
|Database|MySQL, MongoDB, or any one that you like|
|Library|SocketIO, for realtime status update|

###  Ghi nhớ 

Có những cạm bẫy phổ biến bạn cần ghi nhớ khi xây dựng nguyên mẫu này: 

- Các cuộc gọi IO trong NodeJS là bất đồng bộ 
- Nếu bạn đang pát trạng thái người dùng đừng làm nó với tất cả nguời dùng 



# Kết quả 

##  Bạn sẽ học 

- Định danh khi  người dùng **online**
-  Tìm xem người dùng đã **offline**
- Thiết kế lược đồ CSDL và quyết định dữ liệu nào được lưu để hiệu quả 
- Xây dựng trải nghiệm người dùng realtime bằng cách sử dụng SocketIO 


<!--fs-->
#  Chia sẻ và cảm ơn 
 
Nếu bạn thấy hướng dẫn này hữu ích, hãy 

- chia sẻ nó với bạn bè và cộng sự của bạn 
- Đánh giá repo này  và giúp nó tiếp cận với nhiều người hơn 
- Cho tôi 1 lời cảm ơn  on Twitter [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).

Hướng dẫn này là 1 phần của [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) - Một lớp học chuyên sâu nơi giúp bạn trở lên giỏi ở thiết kế hệ thống lớn chịu lỗi và tính khả dụng  cao .
<!--fe-->