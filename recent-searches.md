Thiết kế tìm kiếm gần đây 
===

<!--ts-->
* [Thiết kế tìm kiếm gần đây ](#design-recent-searches)
* [Báo cáo vấn đề ](#problem-statement)
* [Các yêu cầu ](#requirements)
   * [Các yêu cầu lõi](#core-requirements)
   * [Các yêu cầu cấp cao ](#high-level-requirements)
   * [Các yêu cầu vi mô](#micro-requirements)
* [Đầu ra](#output)
   * [Tài liệu thiết kế ](#design-document)
   * [Nguyên mẫu ](#prototype)
      * [Gợi ý công nghệ stack ](#recommended-tech-stack)
      * [Ghi nhớ ](#keep-in-mind)
* [Kết quả](#outcome)
   * [Bạn sẽ học ](#youll-learn)
* [Chia sẻ  và cảm ơn ](#share-and-shoutout)
<!--te-->

# Báo cáo vấn đề 

Khi người dùng chạm vào thanh tìm kiếm chúng ta phải show ít nhất 10 kết quả tìm kiếm gần đây nhất của anh ấy. Thời gian cho dịch vụ này để đáp ứng nên nhanh nhất có thể vì người dùng không muốn chờ cho kết quả tìm kiếm gần đây load.

Thiết kế đường dãn nhập, dịch vụ lõi API, bộ nhớ đệm, ủy quyền nếu cần và quyết định trên luồng dữ liệu cao.

# Các yêu cầu 

<!--rs-->
*Báo cáo vấn đề là cái mà để bắt đầu, hãy sáng tạo và đào sâu vào chi tiết sản phẩm và thêm các ràng buộc và các đặc tính mà bạn nghĩ nó quan trọng.*
<!--re-->

## Các yêu cầu lõi  

- tìm nạp 10 kết quả duy nhất gần dây được thực hiện bởi người dùng 
- Thời gian hồi đáp cho API nên nhỏ hơn < 10ms

 
##  Các yêu cầu cấp cao 
<!--hs-->
- xây dựng các thành phần cao cấp thao tác với tính khả dụng cao 
- Đảm bảo dữ liệu trong hệ thống của bạn là **bền vững** cho dù vấn đề gì xẩy ra 
- Định nghĩa cách mà hệ thống của bạn sẽ xử lý khi phóng to và thu nhỏ quy mô 
- làm cho hệ thống của bạn **hiệu quả về chi phí** và cung cấp 1 lý do tương tự 
- mô tả **kế hoạch hiệu suất của bạn** cái mà giúp bạn có quyết định thiết kế đúng 
- Nghĩ về cách mà các dịch vụ khác sẽ tương tác với dịch vụ của bạn 

<!--he-->

##  Các yêu cầu vi mô 
<!--ms-->
- Đảm bảo dữ liệu trong hệ thống của bạn là **không bao giờ** rơi vào trạng thái không nhất quán.
- Đảm bảo hệ thống của bạn là không có lỗi (nếu có thể )
- Đảm bảo rằng thông lượng của hệ thống của bạn sẽ không bị ảnh hưởng bới khóa, nếu có hãy phát biểu nó ảnh hưởng như nào. 
<!--me-->

# Output

## Tài liệu thiết kế 
<!--ds-->
Tạo 1 **tài liệu thiết kế** của hệ thống/đặc tính này phát biểu rằng tất cả các quyết định thiết kế, các đánh đổi, các thành phần , các dịch vụ và thông tin liên lạc. Cũng chỉ rõ hệ thống của bạn sẽ xử lý như nào ở quy mô lớn và cái gì cuối cùng sẽ trở thành điểm nghẽn 

**Đừng** tạo ra các thành phần không cần thiết cái mà chỉ làm cho hệ thống của bạn trông phức tạp hơn. Một thiết kế tôt luôn **đơn giản và lịch sự**. Một cách tốt để nghĩ về nó là nếu bạn tạo ra các tiến trình/máy/cơ sở hạ tầng cho từng thành phần và bạn sẽ phải tự viết mã cho nó. Bạn vẫn muốn viết? 
<!--de-->

## Nguyên mẫu 

Để hiểu các sắc thái và nội dung bên trong hãy xây dựng nguyên mẫu: 

- Nguyên mẫu luồng thông tin tìm kiếm gần đây trên máy cục bộ 

###  Gợi ý công nghệ ngăn xếp 

Đây là gợi ý công nghệ stack cho xây dựng nguyên mẫu này


|Which|Options|
|-----|-----|
|Language|Golang, Java, C++|
|Database|decide|
|Caching|decide|

###  Ghi nhớ 
Có những cạm bẫy phổ biến cái mà bạn nên ghi nhớ trong đầu trong khi xây dựng nguyên mẫu này 

- Ủy quyền bất cứ khi nào có thể 
# Kết quả 

##  Bạn sẽ học 
- Tầm quan trọng của ủy quyền 
- Thiết kế luồng dữ liệu 
- thiết kế 1 dịch vụ với SLA < 10ms


<!--fs-->
#  Chia sẻ và cảm ơn 

- Nếu bạn thấy hướng dẫn này hữu ích, hãy 
- - chia sẻ hướng dẫn này với bạn bè và cộng sự của bạn 
- đánh giá repo này và giúp nó tiếp cận với nhiều người hơn 
- Cho tôi 1 lời cảm ơn trên [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).

Đây là 1 phần trong hướng dẫn  [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) - Một lớp học cao nơi giúp bạn sẽ trở lên giỏi ở thiết kế hệ thống quy mô lớn, chịu lỗi và tính khả dụng cao 
<!--fe-->