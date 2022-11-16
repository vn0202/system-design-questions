Thiết kế sale chớp nhoáng 
===

<!--ts-->
* [Thiết kế sale chớp nhoáng](#design-flash-sale)
* [Báo cáo vấn đề ](#problem-statement)
* [Các yêu cầu ](#requirements)
   * [Các yêu cầu lõi ](#core-requirements)
   * [Các yêu cầu cấp cao ](#high-level-requirements)
   * [Các yêu cầu vi mô ](#micro-requirements)
* [Đẩu ra ](#output)
   * [Tài liệu thiết kế ](#design-document)
   * [Nguyên mẫu ](#prototype)
      * [Gợi ý công nghệ ngăn xếp ](#recommended-tech-stack)
      * [Ghi nhớ](#keep-in-mind)
* [Kết quả ](#outcome)
   * [Bạn sẽ học](#youll-learn)
* [Chia sẻ và cảm ơn ](#share-and-shoutout)
<!--te-->

# Báo cáo vấn đề 
 Thiết kế flash sale cái mà hỗ trợ việc bán số lượng lớn hàng hóa trong 1 thời gian ngắn. 

Quy trình bán được hỗ trợ bởi hệ thống này là:
- flash sale thông báo cho Xphone 
- flash sale nhắm tới bán 1000 Xphones[fixed inventory]
- Người dùng có thể mua chỉ 1 Xphone trong suốt quá trình sale 
- Người dùng đợi cho flash sale bắt đầu 
- flash sale bắt đầu 
- 1000 người đầu tiên được phép thêm Xphone vào giỏ hàng của họ 
- Người dùng được cho 5p để tiến hành thanh toán 
- Nếu người dùng hoàn thành thanh tóan trong 5p, Xphone được bán cho người đó. 
- Nếu thanh tóan thất bại, Xphone được phép mua bởi người dùng khác.

Chú ý: Flash sale và hệ thống đặt vé của hệ thống có luồng giống nhau; chỉ duy thay đổi là thông lượng và quy mô mong chờ.

# Các yêu cầu 

<!--rs-->
*Báo cáo vấn đề là cái để bắt đầu, hãy sáng tạo và đào sâu vào chi tiết sản phẩm và thêm các ràng buộc và đặc tính bạn nghĩ là nó quan trọng.*
<!--re-->

## Các yêu cầu lõi 
- Cung cấp số lượng đơn hàng cố định, đảm bảo chỉ `N` người có thể thêm các danh mục vào giỏ hàng. 
- Nếu thanh toán không thành công or không được thực hiện, làm  cho các danh mục sẵn sàng cho người khác mua.
- Thông lượng của CSDL nê không bị ảnh hưởng.

##  Các yêu cầu cấp cao 
<!--hs-->
- Làm cho các thành phần cao cấp của bạn thao tác với **tính khả dụng cao**
- Đảm bảo dữ liệu hệ thống của bạn là **bền vững** cho dù vấn đề gì xảy ra
- Định  nghĩa cách hệ thống của bạn cư xử **khi mở rộng** và **thu nhỏ** quy mô.
- Làm cho hệ thống của bạn **hiệu quả về chi phí** và cung cấp 1 lý do tương tự.
- Mô tả **kế hoạch hiệu suất của bạn** cái giúp cho bạn có 1 quyết định sáng suốt.
- Nghĩ về cách mà các dịch vụ khác sẽ tương tác với dịch vụ của bạn. 

<!--he-->

##  Các yêu cầu vĩ mô
<!--ms-->
- Đảm bảo dữ liệu trong hệ thống của bạn là **không bao giờ** rơi vào trạng thái không nhất quán.
- Đảm bảo hệ thống của bạn **không có lỗi** (nếu có thể)
- Đảm bảo rằng thông lượng của hệ thống không bị ảnh hưởng bới **khóa**, nếu có hãy phát biểu nó ảnh hưởng như nào.
<!--me-->

# Đầu ra 

## Tài liệu thiết kế
<!--ds-->
Tạo 1 **tài liệu thiết kế** của hệ thống /đặc tính phát biểu rằng tất cả các quyết định thiết kế quan trọng, các đánh đổi, các thành phần và các thông tin liên lạc. Cũng chỉ rõ hệ thống của bạn sẽ xử lý như nào ở quy mô lớn, và cái gì cuối cùng sẽ trở thành điểm nghẽn. 

**Đừng** tạo ra các thành phần không cần thiết, cái chỉ làm cho hệ thống của bạn trông phức tạp. Một thiết kế tốt **luôn đơn giản và lịch sự**. Một cách tốt để nghĩ về nó là nếu bạn tạo ra 1 tiến trình/máy/cơ sở hạ tầng riêng cho mỗi thành phần và bạn sẽ phải tư viết cho nó, bạn vẫn muốn viết.
<!--de-->

## Nguyên mẫu 

Để hiểu các sắc thái và các nội dung bên trong của hệ thống này, xây dựng 1 nguyên mẫu: 
- Cho phêp 1 số lượng người cố định có thể thêm sản phẩm vào giỏ hàng của họ.
- Xử lý các trường hợp lỗi khi với luồng thanh toán bên ngòai bằng cách mô phỏng cuộc gọi mạng.


###  Gợi ý công nghệ ngăn xếp 

Đây là gợi ý công nghệ ngăn xếp cho xây dựng nguyên mẫu này: 




|Which|Options|
|-----|-----|
|Language|Golang, Java, C++|
|Database|MySQL|

###  Ghi nhớ 


Có những cạm bẫy phổ biến cái mà bạn cần ghi nhớ trong khi xây dựng nguyên mẫu này: 
- Các giao dịch phân tán là tốn kém 
- Khóa hàng quá lâu sẽ cản trở hiệu suất của CSDL


# Kết quả 

##  Bạn sẽ học 

- Khóa CSDL 
- Chia nhỏ các nhiệm vụ khó thành các nhiệm vụ nhỏ có thể quản lý và giải quyết chúng từng cái một
- Xây dựng 1 quy trình làm việc linh hoạt.



<!--fs-->
#  Chia sẻ và cảm ơn 
nếu bạn thấy hướng dẫn này hữu íc, hãy: 

- Chia sẻ hướng dẫn này với bạn của bạn và cộng sự 
- đánh giá repo này để nó tiếp cận với đông đảo thính giả hơn 
- Cho tôi một lời cảm ơn trên Twitter [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).

Hướng dẫn này là 1 phần của [Arpit's System Design Masterclass](https://arpitbhayani.me/masterclass) -Một lợp học master - giúp bạn trở lên giỏi hơn ở thiết kế hệ thống quy mô lớn, chịu lỗi và tinh khả dụng cao.
<!--fe-->