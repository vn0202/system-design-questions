Thiết kế 1 tiến trình tác vụ phân tán 
===

<!--ts-->
* [Thiết kế 1 bộ lập lịch tác vụ phân tán ](#design-a-distributed-task-scheduler)
* [Báo cáo vấn đề ](#problem-statement)
* [Các yêu cầu ](#requirements)
   * [Các yêu cầu lõi](#core-requirements)
   * [Các yêu cầu cấp cao ](#high-level-requirements)
   * [Các yêu cầu vi mô](#micro-requirements)
* [Đầu ra ](#output)
   * [Tài liệu thiết kế](#design-document)
   * [Nguyên mẫu ](#prototype)
      * [Gợi ý công nghệ stack](#recommended-tech-stack)
      * [Ghi nhớ](#keep-in-mind)
* [Kết quả](#outcome)
   * [Bạn sẽ học ](#youll-learn)
* [Chi sẻ và cảm ơn](#share-and-shoutout)
<!--te-->

# Báo cáo vấn đề

Thiết kế 1 bộ lập lịch tác vụ phân tán, nơi mà các máy khách có thể đăng ký 1 nhiệm vụ và thời gian thực thi. Nhiệm vụ cần được thực thi trong 10s kể từ thời gian thực thi theo lịch của nó. Các tác vụ có thể là 2 kiểu .
 
 - nhiệm vụ đơn lẻ.
 - Nhiệm vụ định kỳ
 
Các máy khách có thể đăng ksy tác vụ với 1 cú pháp cron và lịch trình của chúng ta cần thực thi nó theo lịch trình. Máy khách có thể gửi 1 tác vụ có tính chất 1 lần điều đó co nghĩa là một khi thực thi nó sẽ không bao giờ được thực thi lại. 

 Ứng dụng tiềm năng: 
 - Nhắc nhở trong ứng dụng lịch 
 - Phân tán Cron 
 - Gửi thông báo tiến trình tới người dùng.


# Các yêu cầu 

<!--rs-->
*Báo cáo trạng thái là những thứ để bắt đầu, hãy sáng tạo và đào sâu vào sản phẩm chi tiết và thêm các ràng buộc và đặc tính bạn nghĩ nó quan trọng*
<!--re-->

## Các yêu cầu lõi
 - Các máy khách đăng ký tác vụ với thời gian thực thi tiến trình hoặc cú pháp cron 
 - tác vụ là thực thi 1 lần hoặc định kỳ 
 - Tác vụ nên được chọn để thực thi cho 10 giây cho thời gian thực thi tiến trình của nó. 

##  Các yêu cầu cấp cao
<!--hs-->
- Tạo ra các thành phần cao cấp tương tác với **tính khả dụng cao**
- Đảm bảo răng dữ liệu của bạn trong hệ thống là **kiên cố** cho dù vấn đề gì xảy ra. 
- Định  nghĩa cách mà hệ thống của bạn sẽ cư xử như nào trong khi phóng to và thu nhỏ quy mô. 
- làm cho hệ thống của bạn hiệu quả về kinh tế và đưa ra 1 lý do tương tự. 
- Mô tả **kế hoạch hiệu suất** của bnaj cái mà giúp cho bạn đưa ra các quyết định thiết kê tốt. 
- nghĩ về cách mà hệ thống của bạn sẽ tương tác với các dịch vụ khác. 

<!--he-->

##  Các yêu cầu vi mô
<!--ms-->
- Đảm bảo dữ liệu trong  hệ thống của bạn là **không bao giờ** rơi vào trạng thái không nhất quán. 
- Đảm bảo hệ thống của bạn là **không có lỗi**(nếu có thể )
- Đảm bảo thông lượng của hệ thống của bạn là không bị ảnh hưởng bởi khóa, nếu có hãy phát biểu nó ảnh hưởng như nào. 
<!--me-->

# Đầu ra 

## Tài liệu thiểt kế 

<!--ds-->

Tạo **tài liệu thiết kế** của hệ thống /tính năng này phát biểu rằng tất cả các quyết định thiết kế quan trọng, các đánh đổi, các thành phần, các dịch vụ, và các thông tin liên lạc. Đồng thời, cũng chỉ rõ hệ thống của bạn xử lý như nào ở quy mô lớn và cái gì sẽ thực sự trở thành điểm nghẽn.

**đừng** tạo các thành phần không cần thiết cái mà chỉ làm cho thiết kế của bạn trông phức tạp hơn. 1 thiết kế tốt luôn đơn giản và trang trọng. Một cách tốt để nghĩ về nó nếu như bạn tạo ra 1 tiến trình/máy/kiên trúc hạ tầng cho mỗi thành phần và bạn sẽ phải tự viết nó, bạn vẫn muốn làm. 
<!--de-->

## Nguyên mẫu 

Để hiểu các thần thái và nội dung của hệ thống này, xây dựng 1 nguyên mẫu 
- 
To understand the nuances and internals of this system, build a prototype that

- Lập lịch trình thực thi giả như tiến trình đã cấu hình. 
- Mô phỏng các thực thi đồng thời. 


###  Công nghệ Stack gợi ý 

Đây là một công nghệ ngăn xếp được gợi ý cho xây dựng nguyên mẫu này. 

|Which|Options|
|-----|-----|
|Language|Golang, Java, C++|
|Database|MySQL|

###  Ghi nhớ 

 Có những cạm bẫy phổ biến bạn cần nhớ khi xây dựng nguyên mẫu này:

- Mỗi thành phần nên có dự đoán SLA để khái quát SLA tổng thể 10s. 
- Lập lịch tác vụ định kỳ dễ hơn bạn nghĩ.


# Kết quả 

##  Bạn sẽ học 

- Thiết kế các thành phần với dự đoán SLA. 
- Chía các mối quan tâm 
- Cách để triển khai các thực thi định kỳ trong các vô trạng thái.



<!--fs-->
#  Chia sẻ và cảm ơn. 

Nếu bạn thấy hướng dẫn này hữu ích,
- Chia sẻ nó với bạn bè và cộng sự của bạn. 
- đánh giá kho này và giúp nó tiếp cận với nhiều khán giả hơn. 
- cho tôi 1 lời cảm ơn trên  [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).

Hương dẫn này là 1 phần của [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) -Một lớp học chuyên cái mà giúp bạn gioỉ ở thiết kế hệ thống quy mô, chịu lỗi và tính khả dụng cao  .