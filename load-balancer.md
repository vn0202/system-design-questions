Design a Load Balancer
===

<!--ts-->
*[Thiết kế 1 cân bằng tải](#desgin-a-load-balancer)
* [Báo cáo vấn đề ](#problem-statement)
* [Yêu cầu ](#requirements)
   * [Yêu cầu lõi ](#core-requirements)
   * [Các yêu cầu bậc cao ](#high-level-requirements)
   * [Các yêu cầu vi mô](#micro-requirements)
* [Output](#output)
   * [Design Document](#design-document)
   * [Prototype](#prototype)
      * [Recommended Tech Stack](#recommended-tech-stack)
      * [Keep in mind](#keep-in-mind)
* [Đầu ra](#outcome)
   * [Bạn sẽ học ](#youll-learn)
* [Cảm ơn và chia sẻ ](#share-and-shoutout)
<!--te-->

# Báo cáo vấn đề 
Thiết kế 1 bộ cân bằng tải hoạt động như 1 [Reverse Proxy](https://en.wikipedia.org/wiki/Reverse_proxy) và cân bằng tải trên nhiều máy chủ phụ trợ cấu hình  
![Design Load Balancer](https://user-images.githubusercontent.com/4745789/138110826-1490cac9-5a02-43bd-bb14-74334742dd16.png)

# Các yêu cầu. 

<!--rs-->
* Báo cáo vấn đề là những thứ để bắt đầu, hãy sáng tạo và đào sâu vào chi tiết sản phẩm và thêm các hạn chế và đặc tính bạn nghĩ sẽ quan trọng.
<!--re-->

## Các yêu cầu lõi 
- có khả năng **chấp nhận kết nối  TCP** đầu vào và hướng nó tới 1 trong các máy chủ phụ trợ cấu hình.
- có khả năng **thêm** và **xóa** các máy chủ phụ trợ tủy ý. 
- Có thể **giám sát** tình trạng máy chủ phụ trợ.
- Có khả năng có 1 chiến lược cân bằng tải **có thể định hình** .
- Có thể **đo lường** và giám sát số liệu của cân bằng tải. 
- Nên có thể mở rộng quy mô tới **hàng triệu** các kết nối TCP đồng thời. 
 

##  Các yêu cầu cấp cao. 
<!--hs-->
- Tạo ra các thành phần cao cấp của bạn thao tác với **tính khả dụng cao**.
 - Chắc chắn rằng dữ liệu trong hệ thống của bạn là **kiên cố** cho dù điều gì xảy ra. 
 - Định nghĩa hệ thống của bạn nên cư xử như nào khi **mở rộng** và **thu nhỏ quy mô**. 
 - Tạo ra hệ thống của bạn **hiệu quả kinh tế** và cung cấp 1 lý do tương tự. 
 - Mô tả **kế hoạch hiệu suất ** cái mà giúp bạn có các quyết định thiết kế tốt. 
 - Nghĩ về cách mà các dịch vụ của bạn sẽ tương tác với dịch vục của bạn. 

<!--he-->

##  Các yêu câu vi mô
<!--ms-->
- Đảm bảo dữ liệu trong hệ thống là không bao giờ rơi vào trạng thái không nhất quán. 
- Đảm bảo hệ thống của bạn là **không có bế tắc** (nếu có thể )
- Đảm bảo rằng thông lượng của hệ thống của bạn là khong bị ảnh hưởng bởi khóa, nếu nó xảy ra, hãy nói nó sẽ ảnh hưởng như nào. 
<!--me-->

# Đầu ra. 

## Tài liệu thiết kế.
<!--ds-->
Tạo 1 **tài liệu thiết kế** của hệ thống này/đặc tính nói rằng tất cả các quyết định thiết kế quan trọng, đánh dổi, thành phần, dịch vụ, và các thông tin liên hệ. Cũng chỉ rõ hệ thống của bạn xử lý như nào ở quy mô lớn và cái gì cuối cùng sẽ trở thành điểm nghẽn. 

Đừng tạo ra các thành phần không cần thiết, cái mà chỉ làm cho thiêt kế của bạn trông phức tạp. Một thiết kế tốt là **đơn giản  và lịch sự**. MỘt cách tốt để nghĩ về nó là nếu như bạn tạo ra 1 tiến trình/nhà máy/cơ sở hạ tầng riêng biệt cho mỗi thành phần và bạn sẽ phải tự viết nó, bạn vẫn muốn làm?
<!--de-->

## Nguyên mẫu 
Để hiểu sắc thái và nội dung bên trong của hệ thống này, xây dựng 1 nguyên mẫu: 

- là 1 bộ cân bằng tải hoạt động 
- có 1 giao diện để: 
   - Thêm và xóa các máy chủ phụ trợ 
   - Xem cái máy chủ phụ trợ nào cấu hình là tốt. 
   - Trực quan hóa số liệu của bộ cân bằng tải. 
   - Thay đổi chiến lược cân bằng tải nhanh chóng. 
   - Các thay đôỉ không nên yêu cầu khởi động lại để có hiệu quả. 

###  Giới thiệu công nghệ ngăn xếp 
 Đây là 1 công nghệ ngăn xếp được gợi ý cái mà sẽ giúp bạn xây dựng  1 bộ cân băng tải của bạn 1 cách hiệu quả. 

|Which|Options|
|-----|-----|
|Language|Multi-threaded language like Golang, Java, C++|

###  Hãy nhớ
có những cạm bẫy phổ biến cái mà bạn nên nhớ trong khi xây dựng bộ cân bằng tải này. 
- Các cuộc gọi hệ thống đang chặn 
# Đầu ra

##  Bãn sẽ học 
- Cuộc gọi hệ thống 
- Nội dung bên trong của bộ cân bằng tải.
- Thực thi đồng thời bằng các sử dụng đa luồng.


<!--fs-->
#  Chia sẻ và cảm ơn
Nếu bạn thấy các hướng dẫn này hữu dụng, hãy 
- Chia sẻ hướng dẫn nafy với bạn của bạn và cộng sự.
- đánh giá repo này và giúp nó tiêp cận rộng hơn với các độc giả. 
- Cho 1 lời cảm ơn trên Twitter  [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).

 Hưóng dẫn này là 1 phần của [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) - Một lớp học master cái mà giúp bạn trở nên giỏi ở quy mô thiết kế hệ thống , khả năng chịu lỗi và khả dụng cao  
<!--fe-->