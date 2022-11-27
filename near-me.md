Thiết kế dịch vụ ai ở cạnh tôi
===

<!--ts-->
* [Thiết kế 1 cái gì đó tuyệt vời](#design-something-awesome)
* [Báo cáo vấn đề](#problem-statement)
* [Các yêu cầu ](#requirements)
   * [Các yêu cầu lõi](#core-requirements)
   * [Các yêu cầu cấp cao](#high-level-requirements)
   * [Các yêu cầu vi mô](#micro-requirements)
* [Đầu ra ](#output)
   * [Tài liệu thiết kế](#design-document)
   * [Nguyên mẫu ](#prototype)
      * [Gới thiệu công nghệ stack](#recommended-tech-stack)
      * [Ghi nhớ](#keep-in-mind)
* [Đầu r](#outcome)
   * [Bạn sẽ h](#youll-learn)
* [Chia sẻ và cảm ](#share-and-shoutout)
<!--te-->

# Báo cáo vấn đề 

Cung cấp `k` km như 1 đầu vào, tìm tất cả những người người mà trong phạm vi `k` từ bạn, một cách hiệu quả.


>Cốt lõi của hệ thống này có thể được sử dụng trong lưu trữ vị trí gần tôi, đánh dấu điểm gần tôi, cạnh bạn bè, phương tiện điện gần tôi, oto gần tôi, ...

# Các yêu cầu 

<!--rs-->
*Báo cáo vấn đề thường là cái để bắt đầu, hãy sáng tạo và đào sâu vào chi tiết sản phẩm và thêm các ràng buộc và đặc tính bạn nghĩ nó quan trọng.*
<!--re-->

## Các yêu cầu cốt lõi

- trả lời các truy vấn vị trí gần một cách hiệu quả.
- số người sử dụng ứng dụng là 1 triệu người.
 

##  Các yêu cầu cấp cao 
<!--hs-->
- Tạo ra các thành phần cao câp của bạn thao tác với **tính khả dụng cao**
- Đảm bảo dữ liệu trong hệ thống của bạn là **bền vững**, cho dù bất kỳ vấn đề gì xảy ra.
- Định nghĩa cách mà hệ thống của bạn sẽ cư sử trong khi **mở rộng** và **thu nhỏ** quy mô. 
- Làm cho hệ thống của bạn **hiệu quả về kinh tế** và cung cấp 1 lý do tương tự.
- MÔ tả **kế hoạch hiệu suất của bạn** cái mà giúp bạn có quyết định thiết kế tôt.
- Nghĩ về các dịch vụ khác sẽ tương tác với các dịch vụ khác.
 
<!--he-->

##  Các yêu cầu vi mô 
<!--ms-->
- Đảm bảo dữ liệu của bạn không bao giờ rơi vào trạng thái không nhất quán.
- Đảm bảo hệ thống của bạn là **không có lỗi**(nếu có thể)
- Đảm bảo rằng thông lượng của hệ thống của bạn là không bị ảnh hưởng bởi khóa, nếu có, hãy phát biểu nó ảnh hưởng như  nào.
<!--me-->

# Đầu ra 

## Tài liệu thiết kế 
<!--ds-->
Tạo ra 1 **tài liệu thiết kế** của hệ thống/đặc tính này cho rằng tất cả các thiết kế quan trọng, đánh đổi, các thành phần, các dịch vụ và thông tin liên lạc. Cũng chỉ rõ hệ thống của bạn sẽ xử lý như nào ở quy mô lớn và cái gì cuối cùng sẽ trở thành điểm nghẽn.
 **đừng** tạo ra các thành phần không cần thiết, cái chỉ làm cho thiết kế của bạn trong phức tạp. Một thiết kế tốt luôn **đơn giản và lịch sự**. Một cách  tốt nhất để nghĩ về nó là nếu bạn tạo ra các thành phần/tiến trình/máy riêng cho từng thành phần và bạn sẽ phải tự viết mã cho nó, bạn có muốn làm nó nữa không?

<!--de-->

## Nguyên mẫu 

Để hiểu các săc thái và nội dung bên trong của hệ thống này, hãy xây dựng nguyên mẫu: 
- Triển khai các thuật toán /tiếp cận cái mà bạn nghĩ tới cục bộ



###  Recommended Tech Stack

Đây là gợi ý công nghệ stack cho xây dựng nguyên mẫu này.


|Which|Options|
|-----|-----|
|Language|Golang, Java, C++|

###  Ghi nhớ 

Có những cạm bẫy phổ biến cái mà bạn cần ghi nhớ trong khi xây dựng nguyên mẫu này: 
- Bạn không thể thực thi tìm kiếm hiệu quả trong 20 chuyến bay mà không cần đi qua tất cả các diểm đến.



# Kết quả 


##  Bạn sẽ học 
- Làm việc với dữ liệu không gian 
- Thuật toán cái mà có các truy vấn vị trí địa lý mạnh mẽ.


<!--fs-->
#  Chia sẻ và cảm ơn 
Nếu bạn thấy hướng dẫn này hữu ích: 
- chia sẻ nó với bạn bè và cộng sự của bạn 
- đánh giá repo này  và giúp nó tiếp cận sâu rộng với thính giả.
- cho tôi 1 lời cảm ơn trên [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).

Hướng dẫn này là 1 phần của  [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) - Một lớp học chuyên sâu giúp bạn trở nên giỏi ở thiết kế hệ thống quy mô lớn, chịu lỗi và tính khả dụng cao.
<!--fe-->