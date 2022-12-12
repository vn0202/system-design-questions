Thiết kế gắn thẻ ảnh 
===

<!--ts-->
* [Thiết kế gắn thẻ ảnh](#design-photo-tagging)
* [Báo cáo vấn đề ](#problem-statement)
* [Các yêu cầu ](#requirements)
   * [Các yêu cầu lõi ](#core-requirements)
   * [Các yêu cầu cấp cao](#high-level-requirements)
   * [Các yêu cầu vi mô](#micro-requirements)
* [Đẩu ra ](#output)
   * [Tài liệu thiết kế ](#design-document)
   * [Nguyên mẫu ](#prototype)
      * [Gợi ý công nghệ stack](#recommended-tech-stack)
      * [Ghi nhớ](#keep-in-mind)
* [Kết qủa ](#outcome)
   * [Bạn sẽ học ](#youll-learn)
* [Chia sẻ và cảm ơn](#share-and-shoutout)
<!--te-->

# Báo cáo vấn đề 

Thiết kế 1 đặc tính cái mà cho phép  người dùng để gắn thẻ người dùng khác trong bức ảnh họ upload. Người dùng có thể tùy chọn 1 vùng chữ nhật của bức ảnh và gắn nó vơi cá nhân. Theo mặc định, 1 vùng hình vuông nhỏ được chọn làm vùng quan tâm. 


![Relog Tgging Photos with People](https://user-images.githubusercontent.com/4745789/139575791-ff4f4b01-f853-482f-9291-66731559da98.png)

# Các yêu cầu 

## Các yêu cầu lõi 

- Cho phép mọi người để gắn thẻ người khác trong bức ảnh 
- Vùng luôn là hình chữ nhật và người dùng có thể chọn vùng đấy to nhỏ như thế nào. 

##  Các yêu cầu cấp cao 
<!--hs-->

- Làm cho các thành phần cấp cao của hệ thống của bạn tương tác với **tinh khả dụng cao** 
- Đảm bảo rằng dữ liệu trong hệ thống của bạn là **bền vững** cho dù vấn đề gì xảy ra. 
- ĐỊnh nghĩa cách mà hệ thống của bạn sẽ xử lý khi **mở rộng** và **thu nhỏ** quy mô. 
- Làm cho hệ thống của bạn **hiệu quả về chi phí** và cung cấp 1 lý do tương tự. 
- Mô tả **kế hoạch hiệu suất của bạn** cái mà giúp bạn có quyết định thiết kế tốt. 
- Nghĩ về cách mà các dịch vụ khác sẽ tương tác với dịch vu của bạn 

<!--he-->

##  Các yêu cầu vi mô 
<!--ms-->

- Đảm bảo dữ liệu trong hệ thống của bạn **không bao giờ** rơi vào trạng thái không nhất quán. 
- Đảm bảo dữ hệ thống của bạn là **không có lỗi** (nếu có thể)
- Đảm bảo rằng thông lượng của hệ thống không bị ảnh hưởng bởi **khóa**, nếu có hãy phát biểu nó ảnh hưởng như nào.
<!--me-->

# Đầu ra 

## Tải liệu thiết kế 
<!--ds-->

Tạo 1 **tài liệu thiêt kế** của hệ thống/đặc tính này phát biểu rằng tất cả các quyết định thiết kế quan trọng, chi phí, các dịch vụ, các thành phần và thông tin liên lạc. CŨng chỉ rõ hệ thống của bạn sẽ xử lý như  nào ở quy mô lớn và cái gì cuối cùng sẽ trở thành điểm nghẽn. 


**Đừng** tạo ra các thành phần không cần thiết, cái mà chỉ làm cho hệ thống của bạn trông phức tạp. Một các tốt để nghĩ về nó là nếu bạn tạo ra các máy/tiến trình/cơ sở riêng cho từng thành phần và bạn sẽ phải tự viết mã cho nó. bạn vẫn muốn làm? 
<!--de-->

## Nguyên mẫu 

Để hiểu các sắc thái và nội dung của hệ thống này, hãy xây dựng 1 nguyên mẫu: 

- Thiết kế lược đồ dữ liệu để lưu người đưuọc tag trong bức ảnh. 
- Thể hiện những người được tag trên các tài nguyên ảnh khác. 


###  Gợi ý công nghệ stack 
 

Đây là 1 gợi ý công nghệ stack cho xây dựng nguyên mẫu này 

'


|Which|Options|
|-----|-----|
|Language|Golang, Java, NodeJS, C++|
|Database|Pick your favourite|

###  Ghi nhớ 

Có những cạm bẫy phổ biến cái mà bạn cần ghi nhớ khi xây dựng nguyên mẫu này: 

- Thiêt bị có các độ phân giải khác nhau. 

# Kết quả 

##  Bạn sẽ học 

- 

- Miêu tả dữ liệu 
- Thiết kế lược đồ dữ liệu 

<!--fs-->
#  Chia sẻ và cảm ơn 

Nếu bạn thấy hướng dẫn này hữu ích, hãy : 

- Chia sẻ nó với bạn bè và cộng sự của bạn 
- Đánh giá repo này và giúp nó tiếp cận với đông đảo thính giả 
- Cho tôi 1 lời cảm ơn trên  Twitter [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).

Hướng dẫn này là 1 phần của  [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) - Một lớp học master nơi giúp bạn giỏi ở thiết kế hệ thống quy mô lớn, chịu lỗi và tính khả dụng cao 
<!--fe-->