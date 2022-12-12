Thiết kế dịch vụ Hashtag 
===

<!--ts-->
* [Thiết kế dịch vụ HashTag](#design-the-hashtag-service)
* [Báo cáo vấn đề](#problem-statement)
* [Các yêu cầu ](#requirements)
   * [Các yêu cầu lõi](#core-requirements)
   * [các yêu cầu cấp cao ](#high-level-requirements)
   * [Các yêu cầu vi mô](#micro-requirements)
* [Đầu ra ](#output)
   * [Thiết kế tài liệu](#design-document)
   * [Nguyên mẫu ](#prototype)
      * [Gợi ý công nghệ stack ](#recommended-tech-stack)
      * [Ghi nhớ](#keep-in-mind)
* [Kết quả ](#outcome)
   * [Bạn sẽ học ](#youll-learn)
* [Chia sẻ và cảm ơn ](#share-and-shoutout)
<!--te-->

# Báo cáo vấn đề 

Nói rằng bạn sở hữu 1 mạng xã hội, mọi nguời upload ảnh và với mỗi người upload có thể cung cấp 1 danh sách HashTag như một phần của caption. Xây dựng 1 service để quản lý hashtag cùng với nó giúp chúng ta thể hiện 1 trang HashTag cái mà thể hiện: 


 - HashTag 
 - Tổng số ảnh được đăng với Hashtag 
 - Top 50 bức ảnh với HashTag đó 

Dịch vụ này phải xử lý 5 triệu bức ảnh upload mỗi giờ và mỗi bức ảnh có 8 hashtags


![Relog The HashTag Service](https://user-images.githubusercontent.com/4745789/139570503-5b213da5-3a74-4187-9843-c3f718abe0e4.png)

# Các yêu cầu 


<!--rs-->
*Báo cáo vấn đề là cái để bắt đầu, hãy sáng tạo và đào sâu vào chi tiết sản phẩm và thêm các ràng buộc và các đặc tinh bạn nghĩ nó cần thiết*
<!--re-->

## Các yêu cầu lõi 

- **trích xuất** và **quản lý** HashTags từ tất cả các bức ảnh được upload
- **5 triệu*** bức ảnh upload mỗi giờ.
- Thúc đẩy hiệu quả HashTag cái mà thể hiện: 
    
  - HashTag 
  - số bức ảnh với HashTag đó 
  - Top 50 bức ảnh với HashTag đó 


##  Các yêu cầu cấp cao 
<!--hs-->
- Tạo ra các thành phần cao cấp xử lý với **tính khả dụng cao**
- Đảm bảo dữ liệu trong hệ thống của bạn là **bền vững** cho dù vấn đề gì xẩy ra.
- Định nghĩa cách nà hệ thống của bạn sẽ cư xử khi **phóng to** và **thu nhỏ** quy mô 
- Làm cho hệ thống của bạn **hiệu quả về kinh tế** và cung cấp 1 lý do tương tự. 
- Mô tả **kế hoạch hiệu suất của bạn** cái mà giúp bạn có 1 quyết định tốt.
- Nghĩ về cách mà các dịch vụ khác tương tác với dịch vụ của bạn 

<!--he-->

##  Các yêu cầu vi mô 
<!--ms-->
- Đảm bảo dữ liệu trong hệ thống của bạn sẽ  **không bao giờ** rơi vào trạng thái không nhất quán .
- Đảm bảo hệ thống của bạn **không  có lỗi **(nếu có thể )
- Đảm bảo rằng thông lượng của hệ thống là không bị ảnh hưởng bởi khóa và nếu có hãy mô tả nó ảnh hưởng như nào. 

<!--me-->

# Đầu ra 

## Tài liệu thiết kế 
<!--ds-->
Tạo 1 **tài liệu thiêt kế** của hệ thông /đặc tính này phát biểu rằng tất cả các quyết định thiết kế quan trọng, các chi phí, thành phần và thông tin liên lạc . Cũng chỉ rõ cách hệ thống của bạn xử lý ở quy mô và cái gì cuối cùng  sẽ trỏ thành điểm nghẽn.

**Đừng** tạo ra các thành phần không cần thiết, cái mà chỉ làm cho thiết kế của bạn trông phức tạp. MỘt thiêt kế tốt **luôn đơn giản và lịch sự**. Một cách tốt để nghĩ về là nếu bạn tạo ra mỗi tiến trình/máy/cơ sở riêng cho mỗi thành phần, và bạn sẽ phải tự viết nó. Bạn vẫn muốn làm chứ?
<!--de-->

## Nguyên mẫu 

Để hiểu các sắc thái và nội dung của hệ thống này, xây dựng 1 nguyên mẫu 

- Xây dựng 1 nguyên mẫu nhỏ cái mà upload các bức ảnh upload 
 
  - phân tách các hashtags
  - lưu chúng trong 1 CSDL 
  - Cập nhật số lương bức ảnh cho mỗi hashtag

###  Gợi ý công nghệ stack
 Đây là gợi ý công nghệ stack cho xây dựng nguyên mẫu này 


|Which|Options|
|-----|-----|
|Language|Golang, Java, C++|
|Database|pick your favourite|

###  Ghi nhớ 
Có những cạm bẫy phổ biến mà bạn cần ghi nhớ trong khi xây dựng nguyên mẫu này:
- Số lượng bài viết trên CSDL sẽ bùng nổ trên quy mô lớn
- Count++ là không phải nguyên tử theo mặc định 



# Kết quả  

##  Bạn sẽ học 
- quản lý bộ đếm ở quy mô
- Thiết kế kiến trúc đôi lỏng lẻo 
- Thiết kế dịch vụ hiệu quả trong khi nhớ các trải nghiệm người dùng 


<!--fs-->
#  Chia sẻ và cảm ơn 
Nếu bạn thấy hướng dẫn này hữu ích, hãy 
- chia sẻ với bạn bè và cộng sự của bạn 
- Đánh giá repo này và giúp nó tiếp cận với đông đảo thính giả hơn 
- Cho tôi 1 lời cảm ơn trên [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).

Hướng dẫn này là 1 phần  [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) - Một lớp học chuyên gia nơi giúp bạn trở nên giỏi hơn ở thiết kế hệ thống quy mô, chịu lỗi và tính khả dụng cao.
<!--fe-->