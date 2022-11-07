Thiết kế 1 kho KV siêu nhanh hơn 
===

<!--ts-->
* [Thiết kế 1 kho lưu trữ siêu nhanh hơn )
* [Báo cáo vấn đề ](#problem-statement)
* [Các yêu cầu ](#requirements)
   * [Các yêu cầu cốt lõi ](#core-requirements)
   * [Các yêu cầu cấp cao](#high-level-requirements)
   * [Các yêu cầu vi mô](#micro-requirements)
* [Đầu ra](#output)
   * [Tài liệu thiết kế ](#design-document)
   * [Nguyên mẫu ](#prototype)
      * [Gợi ý công nghệ ngăn xếp ](#recommended-tech-stack)
      * [Ghi nhớ ](#keep-in-mind)
* [Kết quả ](#outcome)
   * [Bạn sẽ học ](#youll-learn)
* [Chia sẻ và cảm ơn ](#share-and-shoutout)
<!--te-->

# Báo cáo vấn đề 

Chúng tôi đã thiết kế 1  [Superfast KV Store](https://github.com/relogX/system-design-questions/blob/master/superfast-kv.md), 
nhưng chúng tôi có thể đi nhanh hơn điều này không? Hãy cố gắng thử các mô hình cái mà nhanh hiwn DB siêu nhanh này. 

Thiết kế 1 lưu trữ KV đơn vĩnh viễn cái mà hỗ trợ các thao tác  `GET`,`PUT`, và `DEL`  và nó có sử dụng phần cứng (ổ đĩa,RAM) tùy chọn. Thời gian hồi đáp cho cả 3 thao tác trên nên thấp nhất có thể và độ phức tạp của các thao tác nên là `0(1)`. Nó ổn cho lưu trữ KV này để không hỗ trợ các số lượng khóa vô hạn vì nó ràng buộc với 1 nút đơn duy nhất, nhưng đảm bảo rằng bạn tối đa hóa số khóa mà 1 nút đơn có thể giữ.

> Note:Nó là ổn nếu lưu trữ của bạn không thể hỗ trợ số lượng lớn keys.

# Các yêu cầu 

<!--rs-->
*Báo cáo vấn đề là cái để bắt đầu, hãy sáng tạo và đào sâu vào chi tiết sản phẩm và thêm các ràng buộc và các đặc tính bạn nghĩ nó quan trọng *
<!--re-->

## Các yêu cầu cốt lõi 

- Nên có thể để `GET`,`PUT`,`DEL` trên 1 phím 
- Tất cả các thao tác nên xẩy ra nhanh nhát có thể với độ phức tạp là `0(1)`
- Lưu trữ KV này không phân tán và sẽ chạy trên chỉ 1 nút đơn. 


##  Các yêu cầu cấp cao.
<!--hs-->
- Xây dựng các thành phần cao cấp của bạn thao tác với **tính khả dụng cao** 
- Đảm bảo rằng dữ liệu của bạn là **bền vững** dù vấn đề gì xảy.
- Định nghĩa cách hệ thống của bạn sẽ cư xử trong khi **mở rộng** và **thu nhỏ** quy mô. 
- Làm cho hệ thống của bạn **hiệu quả về chi phí** và cung cấp 1 lý do tương tự.
- Mô tả **kế hoạch hiệu suất của bạn** cái giúp bạn có 1 quyết định thiết kế đúng.
- Nghĩ về cách các dịch vụ khác sẽ tương tác với dịch vụ của bạn. 

<!--he-->

##  Các yêu cầu vi mô 
<!--ms-->
- Đảm bảo dữ liệu của bạn sẽ **không bao giờ** rơi vào trạng thái không nhất quán. 
- Đảm bảo hệ thống của bạn sẽ **không có lỗi** (nếu có thể)
- Đảm bảo rằng thông lượng của hệ thống của bạn sẽ không bị ảnh hưởng bởi khóa **locking**, nếu có, hãy phát biểu nó ảnh hưởng như nào.
<!--me-->

# Đầu ra 

## Tài liệu thiết kế 
<!--ds-->
Tạo 1 **tài liệu thiết kế** của hệ thống/đặc tính này phát biểu rằng tất cả các quyết định thiết kế quan trọng, các chi phí đánh đổi, các thành phần các dịch vụ và các thông tin liên lạc. Cũng chỉ cách mà hệ thống của bạn xử lý ỏ quy mô và cái gì cuối cùng sẽ trỏ thành điểm nghẽn.

**Đừng** tạo ra các thành phần không cần thiêt, cái mà chỉ làm cho thiết kế của bạn trông phức tạp hơn. Một thiêt kế tốt **luôn đơn giản và lịch sự**. Một cách tốt để nghĩ về nó là nếu bạn tạo ra các tiến trình/máy/cơ sở hạ tầng riêng lẻ và bạn phải tự viết mã cho nó. Bạn vẫn muốn làm? 
<!--de-->

## Nguyên mẫu 

Để hiểu các  sắc thái và nội dung bên trong của hệ thống, xây dựng 1 nguyên mẫu: 
- Khai triển thiêt kế của bạn và đo lường hiệu năng của `GET`,`PUT` và `DEL`



###  Gợi ý công nghệ stack
Đây là gợi ý công nghệ stack cho xây dựng nguyên mẫu này:

|Which|Options|
|-----|-----|
|Language|Golang, Java, C++, Python|

###  Ghi nhớ 

Có những cạm bẫy phổ biến bạn cần nhớ khi xây dựng nguyên mẫu này: 

- Công cụ lưu trữ cuả bạn luôn luôn ràng buộc với 1 nút đơn.
- Nó ổn cho công cụ của bạn không hỗ trợ số lượng lớn keys


# Kết quả 

##  Bạn sẽ học 

- Thiết kế 1 công cụ lưu trữ.
- Sử dụng tất cá các phân phối ổ cứng của bạn. 



<!--fs-->
#  Chia sẻ và cảm ơn 
Nếu bạn thấy hướng dẫn này hữu ích, hãy: 
- Chia sẻ nó với bạn bè và cộng sự của bạn.
- Đánh giá repo này để giúp nó tiếp cận với đônh đảo thính giả 
- CHo tôi 1 lời cảm ơn trên [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).

Hướng dẫn này là 1 phần của  [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) -  Một lớp học tài năng nơi giúp bạn trở nên xuất sắc  ở thiết kế hệ thống quy mô lớn, chịu lỗi và tính khả dụng cao .
<!--fe-->