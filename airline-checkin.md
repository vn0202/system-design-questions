Design Airline Check-in System
===

<!--ts-->
* [Thiết kế hệ thống thủ tục hàng không](#desgin-airLine-check-in-system)
* [Báo cáo vấn đề ](#problem-statement)
* [Yêu cầu](#requirements)
   * [Yêu cầu cốt lõi](#core-requirements)
   * [Yêu cầu cấp cao](#high-level-requirements)
   * [Yêu cầu vi mô](#micro-requirements)

* [Đầu ra](#output)
   * [Thiết kế tài kiệu ](#design-document)
   * [Nguyên mẫu ](#prototype)
      * [Gợi ý công nghệ ngăn xếp ](#recommended-tech-stack)
      * [Ghi nhớ trong đầu ](#keep-in-mind)
* [Kết qủa](#outcome)
   * [Bạn sẽ học ](#youll-learn)
* [Chi sẻ và cảm ơn ](#share-and-shoutout)
<!--te-->

# Báo cáo vấn đề 

Khi ban đặt vé của bạn với 1 hãng hàng không, bạn được yêu cầu để hoàn thiện thanh toán và xác nhận ghế của bạn. Một việc đăt chỗ được hoàn tất, bạn có thể tùy chọn thực hiện thủ tục trên trang web và xác nhận chỗ ngồi của bạn hoặc chỉ trước khi bạn khơi hành thực hiện các thử tục vật lý ở sân bay 

Trong báo cáo vấn đề, hãy thiết kế trang web thủ tục trong hệ thống, nơi các hành khách đăng nhập vào hệ thống với PNR, thực thi chọn chỗ ngồi và nhận thẻ lên máy bay. Nếu hành khách cố gắng đặt 1 chỗ ngồi, chỗ đã đưọc đặt  và giao cho 1 hành khách thể hiện 1 thông báo lỗi yêu cầu hành khách chọn lại  chỗ ngồi 

![Relog Airline Check-in System](https://user-images.githubusercontent.com/4745789/138721841-3fc02879-7075-491a-9dcf-74011dba11e6.png)

# Yêu cầu 

<!--rs-->
* Báo cáo vấn đề là cái để bắt đầu, hãy sáng tạo và đào sâu vào chi tiết dự án và thêm các hạn chế và đặc điểm bạn nghĩ sẽ quan trọng.*
<!--re-->

## Yêu cầu cốt lõi 

- **Một chỗ ngồi** có thể dược giao cho chỉ 1 khách hàng  và một khi được gán, chỗ ngồi không được chuyển nhượng 
- giả sử tất cả **100 người** lên máy bay đang cố gắng chọn 1 chỗ ngồi trong cùng lúc. 
- Thủ tục nên là **nhanh** nhất có thể. 
- Khi 1 hành khách đang đặt vé nó không nên dẫn tới người khác phải chờ



##  Yêu cầu cao cấp 
<!--hs-->
- Làm các thành phần cao cấp của bạn thao tác với tính khả dụng cao. 
 - Đảm bảo rằng dữ liệu trong hệ thống của bạn là kiên cố cho dù có vấn đề gì xẩy ra. 
 - đinh nghĩa hệ thống của bạn nên cư xử như naò khi **mở rộng** và **thu nhỏ quy mô**
 - xây dựng hệ thống của bạn ** hiệu quả kinh tế** và cung cấp 1 lý do tương tự 
 - Mô tả **kế hoạch công suất** như nào giúp bạn có 1 quyết định thiết kế tốt. 
 - Nghĩ về các dịch vụ khác sẽ tương tác với dịch vụ của bạn 

<!--he-->

##  Yêu cầu vi mô 
<!--ms-->
- Bảo đảm dữ liệu trong hệ thống của bạn **không bao giờ** xảy ra trạng thái không nhất quán. 
 - Bảo đảm hệ thống của bạn là **không có bế tắc** ( nếu có thể )
 - Đảm bảo rằng thông lượng của hệ thống của bạn sẽ không bị ảnh hưởng bởi **khóa**, nếu xảy ra, hãy nói nó sẽ ảnh hưởng như nào 
<!--me-->

# Đầu ra 

## Thiết kế tài liệu 
<!--ds-->
Tạo 1 **thiết kế tài kiệu** của hệ thống / đặc tính này nói lên tất cả các quyết định thiết quan trọng, sự đánh đổi, thành phần, dịch vụ và thông tin lien lạc. Cũng chỉ rõ hệ thống của bạn xử lý ở quy mô như nào và cái gì cuối cùng sẽ trở thành điểm thắt. 

Đừng tạo ra các thành phần không cần thiết, cái mà chỉ tạo ra các thiết kế trông phức tạp. Một thiết kê tốt **luôn là thiết kế đơn giản và lịch sự** . Một các tốt để nghĩ về nó như là bạn tạo ra 1 tiến trình/máy/kiến trúc riêng biệt cho mỗi thành phần và bạn sẽ phải tự code nó, bạn vẫn sẽ làm chứ?
<!--de-->

## Nguyên mẫu 

Để hiểu sắc thái của hệ thống này và nội dung của hệ thống này, xây dựng 1 nguyên mẫu đó . 

- Thiết kế 1 lược đồ CSDL cho hệ thống thủ tục hàng không 
- Xây dựng 1 giao diện đơn giản cho phép hành khách để 
  - xem các ghế có sẵn 
  - xem các ghế không còn 
  - chọn chỗ ngồi theo sở thích của họ 
  - Môt khi đặt thành công, in ra thẻ lên máy bay của họ 

- Mô phỏng nhiều hành khách cố gắng đặt cùng 1 vé và sử lý đông thời, 
- 

###  Gợi ý công nghệ ngăn xếp 

Đây là 1 gợi ý công nghệ ngăn xếp cho xây dựng nguyên mẫu này 


|Which|Options|
|-----|-----|
|Language|Golang, Java, C++|
|Database|Relational Database - MySQL, PostgreSQL|

###  Hãy nhớ

Có những cạm bẫy phổ biến cái mà bạn beeb nhớ trong khi xây dựng nguyên mẫu này 

- Có 1 khóa chính để với bảng của bạn nếu không toàn bộ bảng có thể bị khóa 


# Kết quả

##  Bạn sẽ học 

- Khóa cơ sở dữ liệu .
- Thiết kế lược đồ CSDL 


<!--fs-->
#  Share and shoutout

Nếu bạn nhận thấy hướng dẫn này hữu ích, hãy 
 - chia sẻ hướng dẫn này với bạn của bạn và cộng sự 
 - đánh giá repo này và giúp nó tiếp cận rộng hơn với thính giả. 
 - Gửi tôi 1 lời cảm ơn trên Twitter [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).

Hướng dẫn này là 1 phần của [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) -Một lớp tổng thể có thể giúp bạn trở nên giỏi hơn trong thiết kế có thể mở rộng ,khả năng chịu lỗi cao và có tính khả dụng cao. 

<!--fe-->