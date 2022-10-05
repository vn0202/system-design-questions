Design an Image Service
===

<!--ts-->
* [Thiết kế 1 dịch vụ ảnh ](#design-an-image-service)
* [Báo cáo vấn đề ](#problem-statement)
* [Các yêu cầu ](#requirements)
   * [Các yêu cầu lõi ](#core-requirements)
   * [Các yêu cầu cấp cao ](#high-level-requirements)
   * [Các yêu cầu vi mô](#micro-requirements)
* [Đầu ra](#output)
   * [Tài liệu thiết kế](#design-document)
   * [Nguyên mẫu ](#prototype)
      * [Gợi ý công nghê ngăn xếp](#recommended-tech-stack)
      * [Ghi nhớ](#keep-in-mind)
* [Kết quả ](#outcome)
   * [Bạn sẽ học ](#youll-learn)
* [Chia sẻ và cảm ơn ](#share-and-shoutout)
<!--te-->

# Problem Statement

Thiết kế 1 dịch vụ ảnh cái mà có thể upload ảnh, sắp xếp và tôi ưu ở quy mô 5 triệu ảnh được upload mỗi giờ. Tối ưu ảnh sẽ được dành riêng  các thiết bị yêu cầu nó. 

![Relog Image Service](https://user-images.githubusercontent.com/4745789/139569887-2247a841-f78d-4546-a331-ec4d891f453a.png)

# Các yêu cầu

<!--rs-->
*Báo cáo vấn đề là cái để bắt đầu, hãy sáng tạo và đào sâu vào chi tiết sản phẩm và thêm các ràng buộc và đặc tính bạn nghĩ sẽ quan trọng.*
<!--re-->

## Yêu cầu lõi 
 - Tải **5 triệu ảnh** mỗi giờ từ nhiều máy khách và thiết bị 
 - Sắp xếp ảnh **hiệu quả** để hiển thị thiết bi 
 - Cung cấp **các phân tích** xoay quanh các bức ảnh đưọc yêu cầu như thế nào từ các hệ thống.
 - Mức tiêu thụ phụ trợ phải gần tối ưu.


##  Các yêu cầu cao cấp 
<!--hs-->
- Tạo các thành phần cao cấp thao tác với **tinh khả dụng cao**
- Đảm bảo các dữ liệu trong hệ thống của bạn là **kiên cố** cho dù vấn đề gì xảy ra,
- xác định cách mà hệ thống của bạn sẽ cư xử khi **mở rộng** hay **thu nhỏ**
- nghĩ về cách mà các dịch vụ khác sẽ tương tác với dịch vụ của bạn.
<!--he-->

##  Yêu cầu vi mô 
<!--ms-->
- Đảm bảo rẳng dữ liệu của bạn sẽ không bao giờ rơi vào trạng thái không nhất quán. 
- Đảm bảo hệ thống của bạn sẽ không có bế tắc (nếu có thể)
- Đảm bảo hệ rằng thông lượng của hệ thống sẽ không bị ảnh hưởng bởi **khóa** nếu xảy ra, hãy nói nó sẽ ảnh hưởng như nào. 
<!--me-->

# Output

## Design Document
<!--ds-->
Tạo 1 **tài liệu thiết kế** của hệ thống/đặc tính này nói rằng tất cả các quyết định thiết kế quan trọng, đánh đổi, thành phần, dịch vụ, và thông tin liên lạc . Đồng thời cũng chỉ rõ hệ thống của bạn xử lý như nào ở quy mô lớn và cuối cùng điều gì sẽ trở thành điểm nghẽn. 
Dừng tạo ra các thành phần không cần thiết, cái mà chỉ để trông thiết kế của bạn phức tạp hơn. Một thiết kế tốt luôn là đơn giản và trang trọng. Một các tốt là nghĩ về nó nếu như bạn tạo ta 1 tiến trình/máy/cơ sở hạ tầng riêng cho mỗi thành phần, bạn sẽ phải tự viết nó. bạn vẫn sẽ làm? 
<!--de-->

## Prototype

Để hiểu các sắc thái và nội dung của hệ thống này, hãy xây dựng một nguyên mẫu
- viết một trình tải lên hình ảnh tải lên hình ảnh và lưu trữ cục bộ trên một trong các thư mục cục bộ của bạn
- tạo một URL công khai cho hình ảnh mà qua đó hình ảnh có thể được kéo trong thẻ `img`
- ghi lại các số liệu mỗi khi một hình ảnh được yêu cầu
###  Recommended Tech Stack

Đây là một ngăn xếp công nghệ được khuyến nghị để xây dựng nguyên mẫu này
|Which|Options|
|-----|-----|
|Language|Golang, Java, C++|

###  Keep in mind

Đây là những cạm bẫy phổ biến mà bạn nên ghi nhớ trong khi xây dựng nguyên mẫu này
- cung cấp hình ảnh từ máy chủ API tùy chỉnh của bạn rất đơn giản
# Outcome

##  You'll learn

- phục vụ các tệp tĩnh
- tải lên hình ảnh trên quy mô lớn
- sử dụng CDN để lưu vào bộ nhớ cache tải xử lý từ các khu vực địa lý khác nhau

<!--fs-->
#  Share and shoutout

If you find this assignment helpful, please
 - share this assignment with your friends and peers
 - star this repository and help it reach a wider audience
 - give me a shoutout on Twitter [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).

This assignment is part of [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) - A masterclass that helps you become great at designing scalable, fault-tolerant, and highly available systems.
<!--fe-->