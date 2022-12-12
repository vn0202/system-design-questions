Thiết kế đếm số lần xuất hiện ở quy mô 
===

<!--ts-->
* [Thiết kế đếm số lần hiện thị ở quy mô ](#design-counting-impressions-at-scale)
* [Báo cáo vân đề ](#problem-statement)
* [Các yêu cầu ](#requirements)
   * [Các yêu cẩu lõi ](#core-requirements)
   * [Các yêu cầu cấp cao ](#high-level-requirements)
   * [Các yêu cầu vi mô ](#micro-requirements)
* [Đầu ra ](#output)
   * [Tài liệu thiết kế ](#design-document)
* [Kết quả ](#outcome)
   * [Bạn sẽ học ](#youll-learn)
* [Chia sẻ và cảm ơn ](#share-and-shoutout)
<!--te-->

# Báo  cáo vấn đề 
 Bất cứ khi nào 1 ad được hiển thị tới bạn trên bất kỳ website, nó được đếm như 1 lần xuất hiện. Hiểu đơn giản, bất kỳ khi nào những thứ được thể hiện tới bạn nó được xem như 1 lần xuất hiện trong phần phụ trợ. Chúng ta phải xây dựng 1 hệ thống để đếm số lần xuất hiện của 1 quảng cáo ở mức quy mô. 
Đếm các lần xuất hiện không giới hạn ơt quảng cáo kinh doanh,nó tìm thấy các ứng dụng của nó trong mạng xã hội để đếm số lượt xem của 1 bài báo, của nền tảng video - số lượng lượt xem video, kỹ thuật tìm kiếm -  sô lần 1 trang được thể hiện trong kết quả tìm kiếm 
Chúng ta phải xây dựng  hệ thống cái mà giúp chúng ta trả lời các câu này 1 các hiệu quả. 

> Số lượng các cá nhân truy cập  trong lần 'n' của đơn vị thời gian cuối  

Đây là 'n' sẽ được cung cấp như 1 đầu vào trong mỗi truy vấn đơn cái mà sẽ được kich hoạt trên hệ thống. 

# Các yêu cầu 

<!--rs-->
*Báo cáo vấn đề là thứ đẻ bắt đầu, hãy sáng tạo và đào sâu vào sản phẩm chi tiết  và thêm các ràng buộc và các đặc tính mà bạn nghĩ là nó quan trọng
<!--re-->

## Các yêu cầu lõi 

 - cần 1 câu trả lời thực hoặc gần thực cho câu hỏi - số lượt tham quan trong 1 vùng thời gian 
 -  Giá trị không nên được tổng hợp lại ( giờ, ngày, tuần )
 - vùng thời gian sẽ được cung cấp nhanh chóng 
 - bộ đếm có thể là 1 số gần đúng. 
 - hoàn thành tính toán nên gói trong vài giây 
 - thiết kế nên được lưu trữ hiệu quả 


##  Các yêu cầu cấp cao 
<!--hs-->
 - Taọ các thành phần cao cấp thao tác với **tinh khả dụng cao**
 - đảm bảo dữ liệu của bạn trong hệ thống là **bền vững** cho dù vấn đề gì xảy ra. 
 - định nghĩa các hệ thống của bạn xử lý trong khi **phóng to** và **thu nhỏ quy mô**
 - xây dựng hệ thống của bạn hiệu quả về kinh tế  và cung cấp 1 lý do tương tự 
 - mô tả kế hoạch hiệu xuât của bạn  như nào cái mà giúp bạn đưa ra quyết định thiết kế tốt. 
 - nghĩ về các dịch vụ khác tương tác với dịch vụ của bạn như nào. 
<!--he-->

##  Yêu cầu vi mô 
<!--ms-->
 - đảm bảo dữ liệu trong hệ thống của bạn không bao giờ rơi vào trạng thái không tương thích 
 - đảm bảo hệ thống của bạn **không có lỗi** ( nếu có thể)
- Đảm bảo hệ thống của bạn không bị ảnh hưởng bới **khóa** nếu có hãy phát biểu nó ảnh hưởng như nảo.
<!--me-->

# Đầu ra 

## Tài liệu thiết kế 
<!--ds-->
Tạo 1 **tài liệu thiết kế** của hệ thống/đặc tính này cho rằng tất cả các quyết định thiết kế quan trọng,chi phí, thành phần, dịch vụ và thông tin liên lạc. Cũng chỉ rõ hệ thống của bạn sẽ sử lý như nào ở quy mô và cái gì cuối cùng sẽ trở thành điểm nghẽn.
Đừng tạo các thành phần không cần thiết cài mà chỉ làm cho thiết kế của bạn trông phức tap. Một thiết kế tốt **luôn đơn giản và lịch sự** . Một các tốt để nghĩ về nó là nếu bạn tạo các tiến trình/máy/cơ sở hạ tầng rieeng lẻ, và bạn sẽ phải tựu viết nó, bạn có muốn làm không?

<!--de-->

# Kết quả 

##  Bạn sẽ học 

- Thuật toán xấp xỉ cho đếm lần xuất hiện 
- Đếm hiệu quả tối ưu thời gian và không gian 


<!--fs-->
#  Chia sẻ và cảm ơn 
Nếu bạn thấy hướng dẫn này hữu ích, hãy: 
- Chia sẻ với bạn của bạn và các cộng sự 
- đánh giá repo này  và giúp nó tiếp cận sâu rộng với khán giả. 
- cho tôi 1 lời cảm ơn trên [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).

Hướng dẫn này là 1 phần của [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) - Một lớp học chuyên gia giúp ban trở lên giỏi hơn ở thiết kế hệ thống quy mô lớn, chiu lỗi và tính khả dụng cao 
<!--fe-->