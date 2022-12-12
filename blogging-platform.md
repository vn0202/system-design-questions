Thiết kế 1 môi trường Bliog 
===

<!--ts-->
* [Thiết kế 1 nên tảng Blogging](#degsin-a-blogging-platform)
* [Trạng thái vấn đề](#problem-statement)
* [Yêu cầu ](requirements)
   * [Yêu cầu lõi](#core-requirement)
   * [Yêu cầu mức độ cao](#hight-level-requirements)
   * [Yêu cầu vi mô](#micro-requirements)
* [Đầu ra ](#out-put)
   * [Tài liệu thiết kế ](#design-document)
   * [Nguyên mẫu](#prototype)
      * [Gợi ý công nghệ ngăn xếp](#recommendationn-tech-stack)
      * [Hãy nhớ](#keep-in-mind)
* [Kết qủa](#outcome)
  * [Bạn sẽ học ](#youll-learn)
* [chia sẻ và cảm ơn ](#share-and-shoutout)

<!--te-->

# Báo cáo vấn đề

Thiết kế 1 môi trường Xuất  bản\blogging nhiều người dùng cơ bản, cho phép người viết xuất bản và quản lý blog dưới xuất bản cá nhân của họ và người đọc đoc chúng.


# Yêu cầu 

<!--rs-->
* Báo cáo trạng vấn đề là cái để bắt đầu, hãy sáng tạo và đào sâu vào chi tiết dự án và thêm các hạn chế và đặc tính bạn nghĩ là sẽ quan trọng.
<!--re-->

## Yêu cầu lõi.

 - Người viết nên có thể **xuât bản** blog dướí sự xuất bản cá nhân 
 - Người đọc nên có thể **đọc** blog.
 - Một người dùng có thể là cả người đọc cũng như người viết.
 - Tác giả của Blog nên là 1 có thể **xóa** Blog.
 - Blog có thể **chứa ảnh**, nhưng không nên chứa video. 
 - Thời gian để truy cập Blog nên là **thấp nhất có thể**
 - Chúng ta có thể biểu diễn"**số lượng blogs**" được viết bởi mỗi người dùng trên hồ sơ của anh\cô ấy.
 - Người dùng nên có thể **tìm kiếm** 1 trang Blog cụ thể .
 - Môi trường nên có quy mô **5 triệu ** người đọc hoạt động hàng ngày.
 - Môi trường nên có quy mô cho **10,000** người viết hoạt động hằng ngày.
 - 
 
 
##  High Level Requirements
<!--hs-->
- Tạo các thành phần cao cấp thao thác với **khả năng có sẵn cao**
 - Đảm bảo rằng dữ liệu trong hệ thống của bạn là **vững chắc**, cho dù vấn đề gì xẩy ra.
 - Định nghĩa hệ thống của bạn sẽ cư xử như nào trong khi **phóng to ** và **thu nhỏ quy mô**
 - làm cho hệ thống của bạn **hiệu quả về chi phí** và cung cấp 1 lý do tương tự 
 - Mô tả **kế hoạch về công suất** như nào giúp bạn tạo ra 1 quyết định thiết kế đúng. 
 - Nghĩ tới các dịch vụ khác sẽ tương tác như nào với dịch vụ của bạn
 <!--he-->

##  Yêu cầu vi mô
<!--ms-->
- Chắc chắn rằng dữ liệu trong hệ thống của bạn **không bao giờ** rơi vào trạng thái không nhất quán.
 - Đảm bảo hệ thống của bạn là **Không bế tắc** ( nếu có)
 - Đảm bảo rằng thông lượng hệ thống của bạn sẽ không bị ảnh hưởng bởi **khóa**, nó xẩy ra, hãy nói nó ảnh hưởng như nào
<!--me-->

# Đầu ra 

## Thiết kế tài liệu 
<!--ds-->
Tạo 1 **thiết kế tài liệu** của hệ thống / đặc điểm cái nói lên tất cả các quyết định thiết kế quan trọng, sự cân bằng, các thành phần, các dịch vụ, và thông tin liên lạc. Cũng chỉ rõ hệ thống của bạn xử lý quy mô và cái gì cuối cùng sẽ thành điểm tắc nghẽn.

**Đừng** tạo ra cac thành phần không cần thiết, chỉ để thiết kế trông phức tạp.  Một thiết kế tốt sẽ **luôn luôn đơn giản và trang trọng**. Một cách tốt để nghĩ tới nó là nếu như bạn tạo 1 tiên trính/máy/cơ sở hạ tầng riêng lẻ cho mỗi thành phần và bạn sẽ phải tư viết nó, Banj vẫn muốn làm?

<!--de-->

## Nguyên mẫu 

Để hiểu săc thái và nội dung của hệ thống này, hãy xây dựng 1 nguyên mẫu của nó.

- có 1 cơ sở dữ liệu quan hệ với lược đồ có thể xử lý tất cả cá yêu cầu lõi.
- Có 1 giao diện cho người viết để :
  - xuất bản Blog 
  - quản lý Blog 
- có 1 giao diện cho người đọc để : 
  - duyệt qua tất cả các bản xuât bản và đọc chúng 
  - Tìm kiếm 1 Blog xuất bản. 



###  Gợi ý công nghệ ngăn xếp

Đây là 1 gợi ý công nghệ ngăn xếp cho xây dưng nguyên mẫu này 



|Which|Options|
|-----|-----|
|Language|Golang, Java, NodeJS|
|Database|Relational Database - MySQL, PostgreSQL|

###  Hãy nhớ 

Có các cạm bẫy thông thường cái mà bạn nên nhớ trong khi xây dựng nguyên mẫu.

- Dữ liệu không nên dư thừa trong lựọc đồ .



# Kết quả 

##  Bạn sẽ học 

- Thiết kế lược dồ cơ sở dữ liệu 
- Xây dựng 1 ứng dụng web cơ bản - 1 CRUD đơn giản 



<!--fs-->
#  Share and shoutout

Nếu bạn thấy trình bày này hữu ích, hãy :
 - Chia sẻ hướng dẫn này với bạn của bạn và cộng sự 
 - Đánh giá repo này và giúp nó tiếp cận nhiều hơn với độc giả 
 - cho tôi 1 lời cảm ơn trên  [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).

Hướng dẫn này là 1 phần  [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) -Một lớp học cao cái mà giúp bạn trở lên tốt hơn ở thiết kế quy mô ,chịu lỗi và hệ thống khả dụng cao. 
<!--fe-->