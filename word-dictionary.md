Thiết kế 1 từ điển từ
===

<!--ts-->
* [Thiết kế 1 từ điển word](#design-a-word-dictionary)
* [Báo cáo vấn đề ](#problem-statement)
* [Yêu cầu ](#requirements)
  * [Yêu cầu lõi](#core-requirements)
  * [Yêu cầu cấp cao](#hight-level-requirements)
  * [Yêu cầu vi mô](#micro-requirements)
* [Đầu ra](#output)
   *[Tài liệu thiết kế](#design-document)
   * [Nguyên mẫu ](#prototype)
      * [Gợi ý công nghệ ngăn xếp ](#recommended-tech-stack)
      * [Hãy nhớ ](#keep-in-mind)
* [Kết quả](#outcome) 
  * [Bạn sẽ học](#youll-learn)
* [Chia sẻ và cảm ơn ](#share-and-shoutout)


<!--te-->

# Báo cáo trạng thái 

Thiết kế 1 dịch vụ cái mà phục vụ từ điển từ Tiếng Anh. Dịch vụ này hiển thị điểm cuối nhận được ý nghĩa của từ. Từ điểm được cập nhập **hàng tuần** thông qua bảng chứa các từ và ý nghĩa cái mà cần được cập nhật và bảng này có thể chứa tối đa 1000 từ. Tổng kích thước của từ điển là **1TB** và nó có **171476** từ. 

> Chú ý: Trong khi xây dựng dịch vụ này, chúng ta không được phép ử dụng bất kỳ CSDL truyền thống nào như MySQL, POstgreSQL, MongoDB... Hãy sáng tạo và sử dụng các cách khác. 

# Yêu cầu 
<!--rs-->
* Báo cáo trạng thái là cái để bạn bắt đầu, hãy sáng tạo và đào sâu vào chi tiết sản phẩm và thêm các ràng buộc và các đặc tính bạn nghĩ nó sẽ quan trọng.

<!--re-->

## Yêu cầu lõi

 - Dịch vụ có thể xử lý **5 triệu ** yêu cầu trên phút.
 - Từ điển được update **hàng tuần** thông qua bảng. 
 - Bạn không được sử dụng các CSDL truyền thống, hãy sáng tạo. 
 - Dịch vụ nên hiệu quả về kinh tế và thuận tiện.

 ##  Yêu cầu cao 
<!--hs-->
- Tạo ra các thành phần bậc cao thao tác với **tính khả dụng cao**
 - Đảm bảo rằng dữ liệu trong hệ thống của bạn là **kiên cố** cho dù bất kỳ vấn đề gì xẩy ra.
 - Định nghĩa các mà hệ thống của bạn cư xử như naò trong khi **phóng to** và **thu nhỏ** 
 - Làm cho hệ thống của bạn **hiệu quả về kinh tế** và cung cấp 1 lý do tương tự.
 - Mô tả **kế hoạch hiệu suất** như nào giúp bạn tạo đưa ra 1 quyết định thiết kế tốt. 
 - Nghĩ về cách các dịch vụ khác sẽ tương tác với dịch vụ của bạn . 
<!--he-->

##  Yêu cầu vi mô
<!--ms-->
- Đảm bảo dữ liệu trong hệ thống của bạn **không bao giờ** rơi vào trạng thái không nhất quán. 
- Đảm bảo hệ thống của bạn là **không rơi vào bế tắc**(nếu có thể )
- 
- ensure the data in your system is **never** going in an inconsistent state
- Đảm bảo thông lượng hệ thống của bạn sẽ không bị ảnh hưởng bới khóa, nếu nó xẩy ra, hãy nói nó ảnh hưởng như nào. 
<!--me-->

# Output

## Thiết kế tài liệu 
<!--ds-->

Tạo 1 **Thiết kế tài liệu** của hệ thống /đặc tính này nói rằng tất cả các quyết định thiết kế, chi phí đánh đổi, thành phần, dịch vụ, và thông tin liên lạc. Cũng chỉ rõ hệ thống của bạn xử lý ở quy mô, và cái gì cuối cùng sẽ trờ thành điểm tắc.

Đừng tạo ra các thành phần không cần thiết,cái mà chỉ làm cho thiết kế trông phức tạp hơn. MỘt thiết kế tốt **luôn luôn đơn giản và trang trọng**. Một cách tốt để nghĩ về điều này nếu như bạn tạo ra 1 tiến trình/máy/cơ sở riêng biệt cho mỗi thành phần và bạn sẽ phải tự code nó, bạn vẫn muốn làm nó?
<!--de-->

## Nguyên mẫu 
 
Để hiểu các sắc thái và nội dung bên trong của hệ thống, xây dựng 1 nguyên mẫu 
- mã của bạn triển khai cục bộ và không lo lắng về quy mô
To understand the nuances and internals of this system, build a prototype that

- code your implementation locaclly and not worry about scale

###  Gợi ý công nghệ ngăn xếp 

Đây là 1 gợi ý công nghệ ngăn xếp cho xây dựng nguyên mẫu này. 

|Which|Options|
|-----|-----|
|Language|Golang, Java, C++, Python|

###  Hãy nhớ 
Có những cạm bãy phổ biến cái mfà bạn nên nhớ trong khi xây dựng nguyên mẫu này. 
 - hãy xem số lượng từ và tổng kích thước của từ điển.


# Kết quả 

##  Bạn sẽ học được 
- Thiết kế định dạng lưu trữ. 
- Các quyết định theo hướng dữ liệu 

<!--fs-->
#  Chia sẻ và cảm ơn 

 Nếu bạn thấy hướng dẫn này hữu ích, hãy 
 - Chia sẻ nó với bạn bè và cộng sự của bạn.
 - đánh giá repo and giúp nó tiếp cận sâu hơn với thinh giả. 
 - Tặng cho tôi 1 lời cảm ơn trên Twitter [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).

Hướng dẫn này là 1 phần của  [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) - Một lớp học chuyên sâu có thể giúp bạn trở nên giỏi hơn ở thiêt kế quy mô, chịu lỗi ,và hệ thống có tính khả dụng cao
<!--fe-->