Thiết kế 1 trình trung gian tin nhán có hỗ trợ SQL 
===

<!--ts-->
* [Thiết kế 1 trình trung gian tin nhắn có sự hỗ trợ SQL](#design-a-sql-backed-message-broker)
* [Báo cáo vấn đề ](#problem-statement)
* [Các yêu cầu ](#requirements)
   * [Các yêu cầu lõi ](#core-requirements)
   * [Các yêu cầu cấp cao ](#high-level-requirements)
   * [Các yêu cầu vi mô ](#micro-requirements)
* [Đầu ra ](#output)
   * [Tài liệu thiết kế ](#design-document)
   * [Nguyên mẫu ](#prototype)
      * [Gợi ý công nghệ stack](#recommended-tech-stack)
      * [Ghi nhớ](#keep-in-mind)
* [Kết quả ](#outcome)
   * [Bạn sẽ học](#youll-learn)
* [Chia sẻ và cảm ơn ](#share-and-shoutout)
<!--te-->

# Báo cáo vấn đề 

THiết kế 1 trình trung gian tin nhắn có hỗ trợ SQL cái mà cho phép khách hàng sắp xếp tin nhắn ( tối đa 4KB) và loại bỏ chúng. Trình trung gian nên hỗ trợ đa nhà sản xuất và đa người dùng ở cùng thời điểm cái mà cho phép trình trung gian hoạt động vơi thông lượng cao. Khi xử lý tin nhắn, máy khách phải xóa rõ ràng các tin nhắn từ trình trung gian. Mỗi tin nhắn có thể có các tùy chọn thời hạn gửi cái mà không được phép đọc.

> Chúng ta đang xây dựng một trình trung gian trên cơ sở dữ liệu của SQL bởi vì CSDL SQL cung cấp sẵn cho chúng ta các công cụ cần thiết để xây dựng trình trung gian mạnh mẽ. Bài tập này sẽ giúp chúng ta hiểu các thuộc tính lõi cái mà chúng ta cân trong trình trung gian của chúng ta và sau đó chúng ta bắt chước chung trong bất kỳ kho lưu trữ nào mà chúng ta chọn.

# Các yêu cầu 

<!--rs-->
*Báo cáo vấn đề là cái để bắt đâu, hãy sáng tạo và đào sâu vào chi tiết sản phẩm và thêm các ràng buộc và đặc tính bạn nghĩ nó sẽ quan trọng.*
<!--re-->

## Các yêu cầu lõi 

- Nhiều nhà cung cấp có thể đặt tin nhán trong trình trung gian ở cùng thời điểm 
- Nhiều người dùng có thể đọc tin nhắn từ trình trung gian ở cùng thời điểm. 
- Một tin nhắn được đọc và xử lý chính xác một người dùng ở cùng 1 thời điểm 
- Tin nhắn 1 khi đã bị xóa không nên đưuọc được bởi bất kỳ người khách nào khác. 
- Môi tin nhắn có thể có 1 tùy chọn thời gian hết hạn. 
- trình trung gian nên có thông lượng cao.

 

##  Các yêu cầu cấp cao 
<!--hs-->
- Làm cho các thành phần cao câp của bạn hoạt động với tính **khả dụng cao**
- Đảm bảo dữ liệu trong hệ thống của bạn là **bền vững** cho dù bất kỳ vấn đề gì xẩy ra. 
- Định nghĩa cách mà hệ thống của bạn sẽ xử lý khi **mở rộng** và **thu nhỏ** quy mô. "
- làm cho hệ thống của bạn **hiệu quả về chi phí** và cung cấp 1 lý do tương tự. 
- Mô tả **kế hoạch hiệu suất** của bạn cái mà giúp bạn có 1 quyết định thiết kế tốt. 
- Nghĩ về cách mà các dịch vụ khác sẽ tương tác với hệ thống của bạn.
- 
<!--he-->

##  Các yêu cầu vi mô 
<!--ms-->
- Đảm bảo dữ liệu trong hệ thống của bạn **không bao giơ** rơi vào trạng thái không nhất quán. 
- Đảm bảo hệ thống của bạn là **không có lỗi** (nếu có thể)
- Đảm bảo thông lượng của hệ thống của bạn không bị ảnh hưởng bởi **loocking**, nếu có, hẫy phát biểu xem nó sẽ ảnh hưởng như nào. 
<!--me-->

# Đầu ra 

## Tài liệu thiết kế 
<!--ds-->

Tạo một **tài liệu thiêt kế** của hệ thống/đặc tính này cho rằng tất cả các quyết định quan trọng, các đánh đổi, các thành phần, các dịch vụ  và các thông tin liên lạc. CŨng chỉ rõ hệ thống của bạn sẽ xử lý như nào ở quy mô lớn và cái gì cuối cùng sẽ trở thành điểm nghẽn.


**Dừng** tạo ra các thành phần không cần thiết, cái mà chỉ làm cho hệ thống của bạn trông phức tạp. Một thiết kế tốt **luôn đơn giản và lịch sự**. Một cách tốt để nghĩ về nó là nếu bạn tạo ra các máy/tiến trình/cơ sở hạ tầng riêng cho mỗi thành phần bạn sẽ phải tự viết mã, bạn vẫn muốn làm? 
<!--de-->

## Nguyên mẫu 

Để hiểu các sắc thái và nội dung của hệ thống này, hãy xây dựng nguyên mẫu: 

- là 1 trình trung gian dựa trên CSDL SQL 
- Mô phỏng nhiều người dùng và nhà sản suất và nhìn cách mà trình trung gian cư xử. 


## Gợi ý công nghệ stack 

Đây là gợi ý công nghệ stack cho xây dựng nguyên mẫu này 

|Which|Options|
|-----|-----|
|Language|Golang, Java, C++|
|Database|MySQL|

###  Ghi nhớ 

Có những cạm bẫy phổ biến cái mà bạn nên nhớ trong đầu trong khi bạn xây dựng nguyên mẫu này. 

- Khóa không hiệu quả sẽ bóp nghẹp CSDL của bạn 
- TTL có thể không là lựa chọn duy nhất 



# Kết quả 

##  Bạn sẽ học được 

- Các thuộc tính lõi của bất kỳ trình trung gian nào. 
- Các nội dung bên trong của trình trung gian 
- Các giao dịch và khóa trong CSDL quan hệ 


<!--fs-->
#  Share and shoutout


Nếu bạn thấy hướng dẫn này hữu ích, hãy 

- Chia sẻ hương dẫn này với bạn bè và cộng sự của bạn 
- Đánh giá repo này và giúp nó tiếp cận với nhiều thính giả hơn 
- Cho tôi 1 lời cảm ơn trên [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).

Hướng dẫn này là 1 phần của  [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) - Một lớp học master nơi giúp bạn trở lên giỏi ở thiết kế hệ thống quy mô lớn, chịu lỗi và tính khả dụng cao. 
<!--fe-->