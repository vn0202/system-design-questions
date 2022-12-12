Thiết kế bình luận trực tiếp dựa trên văn bản 
===

<!--ts-->
* [Thiết kế bình luận trực tiếp dựa trên văn bản ](#design-text-based-live-commentary)
* [Báo cáo trạng thái ](#problem-statement)
* [Các yêu cầu ](#requirements)
   * [Các yêu cầu lõi](#core-requirements)
   * [Các yêu cầu cấp cao ](#high-level-requirements)
   * [Các yêu cầu vĩ mô ](#micro-requirements)
* [Đầu ra ](#output)
   * [Tài liệu thiết kế ](#design-document)
   * [Nguyên mẫu ](#prototype)
      * [Gợi ý công nghệ stack ](#recommended-tech-stack)
      * [ghi nhớ ](#keep-in-mind)
* [Kết qủa ](#outcome)
   * [Bạn sẽ học ](#youll-learn)
* [Chia sẻ và cảm ơn](#share-and-shoutout)
<!--te-->

# Báo cáo vấn đề 

Thiết kế 1 dịch vụ cái mà phục vụ bình luận dựa trên văn bản cho 1 trận đấu bóng chày trực tiếp. Bình luận phải là từng pha bóng được viết bởi các bình luận viên chuyên nghiệp và dịch vụ phải phục vụ các bình luận viên thông qua website tới bất kỳ ai muốn đọc nó.


Các thành phần quan trọng trong hệ thống này: 

- Luồng của dữ liệu để cung cấp 1 trải nghiệm tuyệt vời.
- Đưa ra các quyết định thiết kế cho dữ liệu, bộ nhớ đệm 
- Quyết đinh dựa trên hai quy trình: một cho người đọc và một cho bình luận viên 

# Các yêu cầu 

<!--rs-->

*Báo cáo vấn đề là cái để bắt đầu, hãy sáng tạo và đào sâu vào chi tiết sản phẩm và thêm các ràng buôc và đặc tính bạn nghĩ nó quan trọng với hệ thống của bạn.*

<!--re-->

## Các yêu cầu lõi 
- Bình luận sẽ được cập nhật bởi các chuyên gia bình luận 
- 5  triệu người sẽ đọc các bình luận ở bất kì thời điểm nào 
- Thời gian để phục vụ bình luận nên lâu nhất có thể 


##  Các yêu cầu cấp cao 
<!--hs-->
- Xây dựng các thành phần cấp cao của bạn thao tác với **tính khả dụng cao**
- Đảm bảo dữ liệu trong hệ thống của bạn là **bền vững** cho dù vấn đề gì xẩy ra.
- định nghĩa cách hệ thống của bạn xử lý trong khi **mở rộng** và **thu nhỏ** quy mô 
- làm cho hệ thống của bạn **hiệu quả về chi phí** và cung cấp 1 lý do tương tự 
- Mô tả **kế hoach hiệu suất** cái mà giúp bạn có 1 quyết định thiết kế tôt.
- Nghĩ về cách các dịch vụ khác sẽ tương tác với dịch vụ của bạn
- 
<!--he-->

##  Các yêu cầu vĩ mô 
<!--ms-->
- Đảm  bảo dữ liệu trong hệ thống của bạn là **không bao giờ** rơi vào trạng thái không nhất quán 
- Đảm bảo hệ thống của bạn là **không có lỗi**( nếu có thể )
- Đảm bảo thông lượng của hệ thống của bạn là không bị ảnh hưởng bới **locking**, nếu có hãy phát biểu nó ảnh hưởng như nào 

<!--me-->

# Đầu ra 

## Tài liệu thiết kế 
<!--ds-->
Tạo 1 **tài liệu thiết kê** của hệ thống/đặc tính này cho rằng tất cả các quyết định thiết kế quan trọng, chi phí, thành phần,dịch vụ và thông tin liên lạc. Cũng chỉ rõ hệ thống của bạn xử lý ở quy mô và cái gì cuối cùng sẽ trở thành điểm nghẽn.

Đừng tạo ra các thành phần không cần thiết, cái mà chỉ làm cho thiết kế của bạn trông phức tạp hơn. MỘt thiết kế tốt **luôn đơn giản và lịch sự**. Một cách tốt để nghĩ về nó là nếu bạn taọ các tiến trình/máy/cơ sở hạ tầng riêng lẻ cho các thành phần và bạn sẽ phải tự viết mã, bạn vấn muốn viết ?
<!--de-->

## Nguyên mẫu 

Để hiểu các sắc thái và các nội dụng bên trong của hệ thống này, hãy xây dựng 1 nguyên mẫu: 


- triển khai toàn bộ quy trình hoạt động bình luận cục bộ 

###  Gợi ý công nghệ stack 

Đây là gợi ý công nghệ stack cho xây dựng nguyên mẫu này: 



|Which|Options|
|-----|-----|
|Language|Golang, Java, C++|
|Database|MySQL|
|Cache|Redis|

###  Ghi nhớ 
Có những cạm bẫy phổ biến khi xây dựng nguyên mẫu này: 
- Mỗi tài nguyên bạn quyết định nên có thể sử dụng 1 cách hiệu quả 
- Không thiết kế quá kỹ giải pháp 



# Kết quả 

##  Bạn sẽ học 
- Tạo ra thiết kế CSDL tốt và các quyết định tốt 
- nhận hiệu suất tối ưu từ thiết kế của bạn 
- cách không để không quá kỹ sư :>



<!--fs-->
#  Chia sẻ và cảm ơn 
Nêu bạn thấy hướng dẫn này hữu ích,hãy: 
- chia sẻ nó với bạn bè của bạn và các cộng sự của bạn 
- đánh giá repo này và giúp nó tiếp cận với đông đảo thính giả 
- cho tôi 1 lời cảm ơn trên  Twitter [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).


Hướng dẫn này là 1 phần của  [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) -Một lớp học chuyên gia nơi giúp bạn trở lên giỏi ở thiết kế hệ thống quy mô lớn, chịu lỗi và tính khả dụng cao  
<!--fe-->