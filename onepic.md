Thiết kê 1 bức ảnh 
===

<!--ts-->
* [Thiết kế 1 bức ảnh](#design-onepic)
* [Báo cáo vấn đề ](#problem-statement)
* [Các yêu cầu ](#requirements)
   * [Các yêu cầu lõi ](#core-requirements)
   * [Các yêu cầu cấp cao ](#high-level-requirements)
   * [Các yêu cầu vi mô](#micro-requirements)
* [Đầu ra ](#output)
   * [Tài liệu thiết kế](#design-document)
   * [Nguyên mẫu ](#prototype)
      * [Công nghệ  Stack](#recommended-tech-stack)
      * [Ghi nhớ](#keep-in-mind)
* [Kết quả ](#outcome)
   * [Bạn sẽ học](#youll-learn)
* [Chia sẻ và cảm ơn](#share-and-shoutout)
<!--te-->

# Báo cáo vấn đề 

OnePic là 1 sản phẩm cái mà nó làm cho dễ dàng để sử dụng 1 bức ảnh ở mọi nơi. Sản phẩm để cho bạn có 1 URL duy nhất cái mà bất kỳ website nào sử dụng  dưới `img` tag thể hiện hình ảnh trên trang. Sản phẩm cũng đê cho bạn cập nhật nhiều bức ảnh và thiết lập 1 trong số chúng là active.



```
<img src="https://onepic.relog.in/arpit" />
```

The OnePic URL for user `arpit` will be `https://onepic.relog.in/arpit` which when put under `img` tag renders the one active profile picture of that user. This URL will be used by all other social media to render `arpit`'s profile picture. This way when `arpit` marks some other of his profile picture as active, it will take its effect on all the websites automatically, without needing him to go and update the picture on each site individually.

![Relog OnePic](https://user-images.githubusercontent.com/4745789/139574973-6bd4202d-4256-44a1-bbbd-271f9c3b745b.png)

# Các yêu cầu 

<!--rs-->
*Báo cáo vấn đề là cái để bắt đầu,  hãy sáng tạo và đào sâu vào chi tiết sản phẩm và thêm các ràng buộc và các đặc tính bạn nghĩ nó sẽ quan trọng*
<!--re-->

## Các yêu cầu lõi 

- Người dùng quản lý **nhiều** ảnh cá hồ sơ và đánh dấu 1 cái là **active** 
- Một url duy nhất được sử dụng bởi tất cả các website để **thể hiện** ảnh hồ sơ của người dùng 
- **50000** bức ảnh upload trên phút 
- Đọc với viết tỷ lệ: **1000000:1**


##  Các yêu cầu cấp cao 
<!--hs-->
- Làm cho các thành phần cấp cao của hệ thống của bạn tương tác với **tính khả dụng cao**
- Đảm bảo dữ liệu trong hệ thống của bạn là **bền vững** cho dù bất kỳ vấn đề gì xảy ra.
- Định nghĩa cách mà hệ thống của bạn sẽ cư xử trong khi **mở rộng** và **thu nhỏ** quy mô.
- Làm cho hệ thống của bạn **hiệu quả về chi phí** và cung cấp 1 lý do tương tự 
- Mô tả **kế hoạch hiệu suất** cái mà giúp bạn có quyết định thiết kế tốt.
- Nghĩ về cách các dịch vụ khác sẽ tương tác với dịch vụ của bạn 
<!--he-->

##  Các yêu cầu vi mô
<!--ms-->
- đảm bảo dữ liệu trong hệ thống của bạn là không bao giờ rơi vào trạng thái không nhất quán 
- Đảm bảo hệ thống của bạn là **không có lỗi** (nếu có thể)
- Đảm bảo rằng thông lượng của hệ thống không bị ảnh hưởng bởi khóa, nếu có hẫy phát biểu nó ảnh hưởng như nào.
<!--me-->

# Đầu ra 

## Tài liệu thiết kế 
<!--ds-->

Tạo ra 1 **tài liệu thiết kế** của hệ thống/đặc tính này phát biểu rẳng tẩt cả các quyêt định thiết kế quan trọng, các đánh đổi, các thành phần, các dịch vụ và thông tin liên lạc. Cũng chỉ rõ hệ thống của bạn sẽ xử lý như nào ở quy mô lớn và cái gì cuối cùng sẽ thành điểm nghẽn.

**Đừng** tạo ra các thành phần không cần thiết, cái mà chỉ làm cho thiết kế của bạn trông phức tạp. Một thiết kê tốt luôn **đơn giản và lịch sự**. Một cách tốt để nghĩ về nó là nếu bạn thiết kế các tiến trình/các máy/các cơ sở hạ tầng cho từng thành phần và bạn sẽ phải tự viết mã cho nó.Bạn vẫn muốn làm ?

<!--de-->

## Nguyên mẫu 

Để hiểu các sắc thái và nội dung của hệ thống này, hẫy xây dựng nguyên mẫu: 

- xây dựng 1 máy chủ trang tĩnh đơn giản cái mà phục vu người dùng cập nhật ảnh 
- CRUD để quản lý ảnh hồ sơ và đánh dấu cái active 
- thể hiện ảnh hồ sơ đang hoạt động bất kể khi nào bức ảnh được yêu cầu thông qua URL 
- 



###  Gợi ý công nghệ stack 

Đây là 1 gợi ý công nghệ stack cho xây dựng nguyên mẫu này 



|Which|Options|
|-----|-----|
|Language|Golang, Java, NodeJS, C++|
|Database|Pick your favourite|

###  Ghi nhớ 

Có những cạm bẫy phổ biến cái mà bạn nên nhớ trong khi xây dựng nguyên mẫu này :

- phục vụ ảnh thông qua API máy chủ thì dễ hơn tưởng tượng.



# Kết qủa 


##  Bạn sẽ học 

- máy chủ file tĩnh 
- Đọc các hệ thống lớn phục vụ file tĩnh 
- thiết kế lược đồ CSDL

<!--fs-->
#  Chia sẻ và cảm ơn 

Nếu bạn tìm thấy hướng dẫn này hữu ích, hãy:

- Chia sẻ nó với bạn bè và cộng sự của bạn 
- Đánh giá repo này và giúp nó tiếp cận với đông đảo thính giả 
- Cho tôi 1 lời cảm ơn trên  [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).

Hướng dẫn này là 1 phần của [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) - Một lớp học chuyên gia giúp bạn trở nên giỏi ở  thiết kế hệ thống quy mô lớn, chịu lỗi và tính khả dụng cao 
<!--fe-->