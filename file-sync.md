Thiết kế một dịch vụ đồng bộ file từ xa 
===

<!--ts-->
* [Thiết kế 1 dịch vụ quản lý file từ xa ](#design-a-remote-file-sync-service)
* [Báo cáo vấn đề ](#problem-statement)
* [Các yêu cầu ](#requirements)
   * [Các yêu cầu lõi ](#core-requirements)
   * [Các yêu cầu cấp cao ](#high-level-requirements)
   * [Các yêu cầu vi mô](#micro-requirements)
* [Đầu ra ](#output)
   * [Tài liệu thiết kế ](#design-document)
   * [Nguyên mẫu ](#prototype)
      * [Gợi ý công nghệ trên ngăn stack ](#recommended-tech-stack)
      * [ghi nhớ ](#keep-in-mind)
* [Kết quả ](#outcome)
   * [Bạn sẽ học ](#youll-learn)
* [Chia sẻ và cảm ơn ](#share-and-shoutout)
<!--te-->

# Báo cáo trạng thái 

Thiết kế 1 dịch vụ đồng bộ file cái mà người dùng có thể upload 1 file tới cloud và nó nhận đồng bộ cùng với tất cả các thiết bị của họ. 



>Lõi của hệ thống này là tìm các ứng dung của nó trong các ứng dụng tin nhắn. 

# Các yêu cầu 


<!--rs-->

*Báo cáo vấn đề là cái để bắt đầu, hãy sáng tạo và đào sâu vào trong chi tiết sản phẩm và thêm các ràng buộc và các đặc tính bạn nghĩ nó sẽ quan trọng.*
<!--re-->

## Các yêu cầu lõi.
- Đồng bộ tất cả các file cùng với tất cả các thiết bị của người dùng. 
- 1 file có thể có dung lượng cao nhất 4GB 
- Việc upload và tải nên hiệu quả và có thể tiếp tục 
- Băng thông của người dùng là quan trọng, vì vậy hãy hiệu quả. 


##  Các yêu cầu cấp cao 
<!--hs-->
- Tạo ra các thành phần cấp cao thao tác với tính khả dụng cao. 
- Đảm bảo rằng dữ liệu trong hệ thống của bạn là *bền vững** cho dù vấn đề gì xảy ra. 
- Định nghĩa cách hệ thống của bạn sẽ xử lý khi **mở rộng** và **thu nhỏ** quy mô.
- làm cho hệ thống của bạn **hiệu quả về chi phí** và cung cấp lý do tương tự. 
- Mô tả **kế hoạch hiệu suất của bạn** cái mà giúp bạn có quyết định thiết đúng đắn. 
- Nghĩ về cách hệ thống của bạn sẽ tương tác với các dịch vụ khác. 
<!--he-->

##  Các yêu cầu lõi.

<!--ms-->
- Đảm bảo dữ liệu trong  hệ thống của bạn **không bao giờ** rơi vào trạng thái không nhất quán. 
- Đảm bảo hệ thống của bạn là **không bao giờ có lỗi**( nếu có thể )
- Đảm bảo rằng thông lượng của hệ thống của bạn là không bị ảnh hưởng bới **khóa**, nếu có hãy phát biểu nó ảnh hưởng như nào. 
<!--me-->

# Đầu ra 

## Tài liệu 
<!--ds-->
Thiết kế **tài liệu thiết kế** của hệ thống/đặc tính này phát biểu rằng tất cả các quyết định thiết kế quan trọng, sự đánh đổi, thành phần, dịch vụ và các thông tin liên lạc. Cũng chỉ cách mà hệ thống của bạn sẽ xử lý ở quy mô và cái gì cuối cùng sẽ trở thành điểm nghẽn.

**Đừng** thiết kế các thành phần không quan trọng, cái mà chỉ làm cho hệ thống của ban trông phức tạp. Một thiết kế tốt **luôn luôn đơn giản và lịch sự**. Một cách tốt để nghĩ về nó là nếu bạn tạo ra các máy /tiến trình/ cơ sở hạ tầng cho mỗi thành phần  và bạn phải tự code nó, bạn vẫn muốn làm chứ.
<!--de-->

## Nguyên mẫu 
Để hiểu các sắc thái và nội dung của hệ thống này, hãy xây dựng 1 nguyên mẫu. 
- thực hiện liên tục upload và download 
- Xác định và chia sẻ hiệu quả thay đổi với các thiết bị khác. 


###  Gới thiệu công  nghệ ngăn xếp 
Đây là gợi ý công nghệ stack cho xây dựng nguyên mẫu này. 



|Which|Options|
|-----|-----|
|Language|Golang, Java, C++|

###  Hãy ghi nhớ.

Có những cạm bẫy phổ biến bạn cần nhớ khi xây dựng nguyên mẫu này: 
Chuyển dịch file $G trong 1 lần gọi dễ gián đoạn 



# Kết quả 

##  Bạn sẽ học: 

- Thiết kế tải lên và tải xuống liên tục 
- Các thay đổi và cập nhật tương tác hiệu quả giữa các máy khách. 

<!--fs-->
#  Chia sẻ và cảm ơn.
Nếu bạn thấy hướng dẫn này co ích, hãy: 
- chia sẻ nó với dồng nghiệp và bạn bè của bạn. 
- Đánh giá repo này và giúp nó tiếp cận với đông đảo thính giả 
- Cho tôi 1 lời cảm ơn trên Twitter [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).

Hướng dẫn này là 1 phần của  [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) -  Một lớp học master nơi giúp bạn trở nên tốt hơn ở thiết kế hệ thống quy mô lớn, chịu lỗi và có tính khả dụng cao  
<!--fe-->