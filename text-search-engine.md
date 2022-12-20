Thiết kế 1 công cụ tìm kiếm dựa trên văn bản 
===

<!--ts-->
* [Thiết kế 1 công cụ tìm kiếm dựa trên văn bản ](#design-a-text-based-search-engine)
* [Báo cáo vấn đề ](#problem-statement)
* [Các yêu cầu ](#requirements)
   * [Các yêu cầu lõi ](#core-requirements)
   * [Các yêu cầu vi mô](#micro-requirements)
* [Đầu ra](#output)
   * [Tài liệu thiết kế ](#design-document)
   * [Nguyên mẫu ](#prototype)
      * [Gợi ý công nghệ stack ](#recommended-tech-stack)
* [Kết quả](#outcome)
   * [Bạn sẽ học ](#youll-learn)
* [Chia sẻ và cảm ơn ](#share-and-shoutout)
<!--te-->

# Báo cáo vấn đề 

Thiết kế 1 công cụ tìm kiếm dựa trên văn bản đơn giản cái mf phục vụ các kết quả liên quan mà không cần công cụ tìm kiếm như ElasticSearch. ý tưởng là  để hiểu các nội dung bên trong của Công cụ tìm kiếm và các phép toán đằng sau TF-IDF. Mở rộng công cụ tìm kiếm của bạn để hỗ trợ các biểu thức boolean, lỗi đánh máy, ngữ âm và bất kỳ cái gì cái mà bạn thấy thích.  


# Các yêu cầu 

<!--rs-->
*Báo cáo vấn đề là cái để bắt đầu, hãy sáng tạo và đào sâu vào chi tiết sản phẩm và thêm các ràng buộc và các đặc tính bạn nghĩ nó sẽ quan trọng.*
<!--re-->

## Các yêu cầu lõi 

- Xây dựng 1 công cụ tìm kiếm dựa trên văn bản đơn giản cái mà trả về kết quả liên quan. 
- Làm cho công cụ manh mẽ nhất có thể

## Các yêu cầu vi mô 
<!--ms-->
- Đảm bảo dữ liệu trong hệ thống của bạn không bao giờ rơi vào trạng thái không nhất quán 
 - Đảm bảo hệ thống của bạn là **không có lỗi** (nếu có thể) 
 - Đảm bảo thông lượng của hệ thống của bạn không bị ảnh hưởng bởi **locking**, nếu có hãy phát biểu nó ảnh hưởng như nào. 
<!--me-->

# Đầu ra 

## Tài liệu thiết kế 
<!--ds-->
Tạo 1 **tài liệu thiểt kế** của hệ thống này/đặc tính này cho rằng tất cả các quyết định thiết kế quan trọng, các đánh đổi, các thành phần, các dịch vụ và thông tin liên lạc. Cũng chỉ rõ hệ thống của bạn sẽ xử lý như nào ở quy mô lớn và cái gì cuối cùng sẽ trở thành điểm nghẽn. 

**Đừng** tạo ra các thành phần không cần thiết, cái mà chỉ làm cho hệ thống của bạn trông phức tạp. MỘt thiết kế tốt luôn **đơn giản và tao nhã**. Một cách tốt để nghĩ về điều đó là nếu bạn tạo ra các tiến trình/máy/cơ sở hạ tầng cho mỗi thành phần và bạn sẽ phải viết mã cho nó, bạn vẫn muốn làm ?
<!--de-->

## Nguyên mẫu 


Để hiểu các sắc thái và nội dung bên trong của hệ thống này, hãy xây dựng 1 nguyên mẫu: 

- Xây dựng 1 công cụ tìm kiếm trên 100Mb dữ liệu bằng các sử dụng ngôn  ngữ yêu thich của bạn .

###  Gợi ý công nghệ stack 

Đây là gợi công nghệ stack cho xây dựng nguyên mẫu này: 

|Which|Options|
|-----|-----|
|Language|Golang, Java, C++|

# Kết quả 

##  Bạn sẽ học 

- Xây dựng 1 công cụ tìm kiếm dựa trên văn bản đơn giản 
- Thuật toán đằng sau tf-idf 
- basics of NLP - stemming, lemmatization, and phonetics
- Cơ bản của NLF - stemming, bổ đề và ngữ âm 
<!--fs-->
#  Chia sẻ và cảm ơn 

Nếu bạn thấy hướng dẫn này hữu ích, hãy 
- Chia sẻ nó với bạn bè và cộng sự của bạn 
- Đánh giá repo này và giúp nó tiếp cận với đông đảo khán giả 
- Cho tôi 1 lời cảm ơn trên [@arpit_bhayani](https://twitter.com/@arpit_bhayani), or on LinkedIn at [@arpitbhayani](https://www.linkedin.com/in/arpitbhayani/).

Hướng dẫn này là 1 phần của (https://arpitbhayani.me/masterclass) - Một lớp học chuyên sâu nơi giúp bạn trở lê giỏi ở thiết kế hệ thống quy mô lớn, chịu lỗi và tính khả dụng cao 
<!--fe-->