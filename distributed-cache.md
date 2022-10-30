Thiết kế bộ nhớ đệm phân tán 
===

<!--ts-->
* [Thiết kế bộ nhớ đệm phân tán ](#design-a-distributed-cache)
* [Báo cáo vấn đề ](#problem-statement)
* [Các yêu cầu ](#requirements)
   * [Các yêu cầu lõi ](#core-requirements)
   * [Các yêu cầu cấp cao](#high-level-requirements)
   * [Các yêu cầu vĩ mô](#micro-requirements)
* [Đầu ra ](#output)
   * [Tài liệu thiết kế ](#design-document)
   * [Nguyên mẫu ](#prototype)
      * [Gợi ý công nghệ ngăn xếp ](#recommended-tech-stack)
      * [Ghi nhớ ](#keep-in-mind)
* [Kết quả ](#outcome)
   * [Bạn sẽ học ](#youll-learn)
* [Chia sẻ và cảm ơn ](#share-and-shoutout)
<!--te-->

# Báo cáo vấn đề 

Thiết kế 1 bộ nhớ đệm nút đơn và sau đó chia nhỏ quy mô của nó ra để phân tán. Chúng ta giữ bộ nhớ đệm này đơn giản và bởi vậy nó nên hỗ trợ các thao tác đơn giản 

 - `GET`: để nhận 1 khóa từ bộ nhớ đệm 
 - `PUT`: Để đưa khóa vào bộ nhớ đệm 
 - `DEL`: Để xóa 1 khóa từ bộ nhớ đệm
 - `TTL` :để thiêt lập 1 hạn sử dụng cho 1 khóa.

Trong khi thiết kế  bộ nhớ đệm nó rất quan trọng để chú ý rằng bộ nhớ đệm nên khả dụng cao và có thể mở rộng quy mô. Cung cấp bộ nhớ đệm đó là 1 hệ thống có thông lượng cao và đồng thời cao, phóng to  và thu nhỏ quy mô bộ nhớ đệm không có ảnh hưởng lớn đến dữ liệu và hiệu suất 


![Relog Design a Distributed Cache](https://user-images.githubusercontent.com/4745789/141650924-943da5ba-c3a0-4d86-b3f2-a300be7bea9d.png)

# Requirements

<!--rs-->
*The problem statement is something to start with, be creative and dive into the product details and add constraints and features you think would be important.*
<!--re-->

## Các yêu cầu lõi 

- Bộ nhớ đệm nên hỗ trợ `GET`, `PUT`,`DEL` và `TTL`
- Thông lượng của bộ nhớ đệm nên là tùy chọn 
- Bộ nhớ đệm nên  không bị khóa 
- Đo lường tỉ lệ truy cập và tỉ lệ bở lỡ bộ nhớ đệm .
- Bộ nhớ đệm không nên tạm dừng cho hệ thống phụ ngoại vi như hệ thống giám sát 
- Mỗi thành phần nên có khả năng chiu lỗi 
- Thu hồi bộ nhớ đệm có thể cắm và ý nghĩa của nó với hiệu suất. 
- dữ liệu quá lớn để được lưu trữ trên 1 nốt


##  Các yêu cầu cấp cao 
<!--hs-->
- Tạo ra các thành phần cao cấp thao tác với **tính khả dụng cao** 
- Đảm bảo rằng dữ liệu của bạn là **bền vững** cho dù vấn đề gì xảy ra. 
- định nghĩa cách hệ thống của bạn sẽ xử lý trong khi **phóng to** và **thu nhỏ** quy mô 
- Tạo cho hệ thống của bạn **hiệu quả về chi phí** và cung cấp 1 lý do tương tự 
- Mô tả **kế hoạch công xuất** của bạn giúp bạn có quyết định thiết kế tốt. 
- Nghĩ về cách các dịch vụ khác sẽ tương tác với dịch vụ của bạn 

<!--he-->

##  Các yêu cầu vi mô
<!--ms-->
- Đảm bảo hệ thống của bạn là **không bao giờ** rơi vào trạng thái không nhất quán 
- Đảm bảo hệ thống của bạn không bao giờ có lỗi (nếu có thể )
- Đảm bảo thông lượng của hệ thống của bạn không bị ảnh hưởng bởi khóa, nếu có hãy phát biểu nó ảnh hưởng như nào. 
<!--me-->

# Đầu ra 

## Tài liệu thiết kế 
<!--ds-->
Tạo 1 **tài liệu thiết kế** của hệ thống/đặc tính này cho rằng tất cả các quyết định thiết kế quan trọng, chi phí đánh đổi, các thành phần, các dịch vụ và các thông tin liên lạc. Cũng chỉ rõ hệ thống của bạn xử lý như nào ở quy mô và cái gì cuối cùng sẽ trở thành điểm nghẽn. 
 Đừng tạo ra các thành phần không cần thiết cái mà chỉ làm cho thiết kế của bạn trông phức tạp hơn. Một thiết kế tốt luôn đơn giản và lịch thiệp. MỘt các tốt để nghĩ về nó là nếu như  bạn tạo ra các tiến trình/máy./cơ sở hạ tầng riêng bạn sẽ phải tự viết mã cho nó và bạn vân muốn làm nó? 

<!--de-->

## Nguyên mẫu 
Để hiểu các sắc thái và nội dung bên trong của hệ thống này hãy thiết kế nguyên mẫu: 
- 1 nut bộ nhớ đệm đơn cơ bản với hỗ trợ không bị khóa đồng thời 
- Thực hiện tải thử  và độ chuẩn trễ 

###  Recommended Tech Stack

Đây là công nghệ ngăn xếp web được gợi ý cho nguyên mẫu này. 
|Which|Options|
|-----|-----|
|Language|Golang, Java, C++|

###  Ghi nhớ 
Có những cạm bẫy phổ biến cái mà bạn cần nhớ khi thiết kế nguyên mẫu này: 



- khóa bi quan sẽ cản trở thông lượng
# Kết quả 

##  Bạn sẽ học 
- Khai triển bộ nhớ đệm trong bộ nhớ 
- Khai triển không khóa 
- băm nhất quán 


<!--fs-->
#  Share and shoutout

Nếu bạn thấy trình bày này hữu ích, hãy :
- Chia sẻ hướng dẫn này với bạn của bạn và cộng sự
- Đánh giá repo này và giúp nó tiếp cận nhiều hơn với độc giả
- cho tôi 1 lời cảm ơn trên [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).

Hướng dẫn này là 1 phần  [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) -Một lớp học cao cái mà giúp bạn trở lên tốt hơn ở thiết kế quy mô ,chịu lỗi và hệ thống khả dụng cao.
