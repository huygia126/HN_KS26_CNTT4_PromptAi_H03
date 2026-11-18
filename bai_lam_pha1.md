# BÀI LÀM PHA 1 – HACKATHON 02

- **Mã đề:** 03
- **Họ tên:** Chu Gia Huy
- **Lớp:** CNTT4
- **Link repository Pha1:**

> Pha 1 (70 phút đầu, KHÔNG dùng AI). Viết xong, kéo thả file này vào repository Pha1 trước mốc giờ giám thị công bố.

## 4.1. Bảo vệ dữ liệu và chống ảo giác

### a) Ghi chú đã ẩn danh hoá

**GHI CHU DA AN DANH**

```text
Học viên [Ten_Khach_Hang], số điện thoại [So_dien_thoai], số CCCD [So_CCCD], [Emai_Ca_Nhan], đăng ký khoá Luyện thi IELTS 5.5 (mã IE55) khai giảng ngày 14/12/2026 cho 1 học viên lớn và 1 học viên nhỏ 13 tuổi. Khách đã chuyển khoản đặt cọc 2.000.000 đồng. Khách yêu cầu học lớp buổi tối.

```

### b) Hai câu lệnh chống ảo giác

**CAU LENH**

```text
câu 1: chỉ trả lời dựa trên file đính kèm, khi không có thông tin thì trả lời " chúng tôi chưa hỗ trợ phần này " 
câu 2: các thông tin bắt buộc từ mục hoặc điều khoản trong file
```

## 4.2. Trích xuất tin nhắn đăng ký khoá học ra JSON

**PROMPT**

```text
- [Context]
bạn là chuyên viên tư vấn khóa học

- [Request]
chỉ trả về dạng JSON
{"ma_khoa", "ngay_khai_giang", "hoc_vien_lon", "hoc_vien_nho", "hinh_thuc", "ghi_chu"}
áp dụng quy tắc chuẩn hóa



- [Eplanation]
chỉ trả lời và phản hồi đúng trong nội dung, quy định. nếu khách hàng hỏi thêm thông tin ở bên ngoài, không phản hồi nội dung bên ngoài ,trả lời "chúng tôi chưa hỗ trợ nội dung này " và bám theo nội dung tin nhắn mẫu sau để trả lời
Tin nhắn mẫu 1:
Cho chị đăng ký khoá Giao tiếp cơ bản khai giảng 10/11/2026, chị với con gái 12 tuổi, học offline. Con chị bị cận nặng nên cần ngồi bàn đầu.
Kết quả đúng:
{"ma_khoa": "GT01", "ngay_khai_giang": "2026-11-10", "hoc_vien_lon": 1, "hoc_vien_nho": 1, "hinh_thuc": "offline", "ghi_chu": "con bị cận nặng, cần ngồi bàn đầu"}
áp dụng quy tắc chuẩn hóa sau
QUY TẮC CHUẨN HOÁ (5 quy tắc)
1. ma_khoa lấy theo bảng mã khoá học.
2. ngay_khai_giang dạng YYYY-MM-DD; tin nhắn không ghi năm thì lấy năm 2026; không có ngày cụ thể thì null.
3. Khách không nhắc học viên nhỏ tuổi thì hoc_vien_nho là 0 và mọi khách là học viên lớn.
4. hinh_thuc chỉ nhận "online", "offline" hoặc null.
5. ghi_chu chỉ ghi yêu cầu đặc biệt về sức khoẻ, đi lại, điều kiện học tập; không có thì null.



Tin nhắn mẫu 2:
IELTS 5.5 còn lớp online không ạ, em học 1 mình, lớp nào khai giảng cũng được.
Kết quả đúng:
{"ma_khoa": "IE55", "ngay_khai_giang": null, "hoc_vien_lon": 1, "hoc_vien_nho": 0, "hinh_thuc": "online", "ghi_chu": null}


- [Action]
lấy dữ liệu khách hàng từ <tin_nhan> TN1: Anh đăng ký khoá Ngữ pháp nền tảng khai giảng 08/12 nhé, 2 người lớn và 1 bé 13 tuổi, học offline.

TN2: Cho 3 người học IELTS 5.5, khai giảng 06/01/2027 ạ. Một bạn bị khiếm thính nhẹ.

TN3: Lớp Giao tiếp tháng 12 còn chỗ không ạ? Nhóm em 4 người lớn, một bạn đi nạng, muốn học offline.
 </tin_nhan> để chuẩn hóa dữ liệu

- [Tone]
chuyên nghiệp, lịch sự

- [Extras]
trả về dạng JSON

```

## 4.3. Báo giá bằng Chain-of-Thought

### a) Prompt

**PROMPT**

```text
a) tính tổng tiền cho yêu cầu báo giá:
BẢNG HỌC PHÍ (đồng/học viên lớn)
GT01 – Giao tiếp cơ bản, 24 buổi: 4.800.000
IE55 – Luyện thi IELTS 5.5, 30 buổi: 7.500.000
NP12 – Ngữ pháp nền tảng, 12 buổi: 2.400.000

áp dụng quy tắc tính giá sau:
QUY TẮC TÍNH GIÁ
1. Học viên nhỏ tuổi (từ 10 đến 15 tuổi) tính 60% học phí học viên lớn. Trẻ dưới 10 tuổi học dự thính cùng phụ huynh miễn phí.
2. Nhóm từ 4 học viên lớn trở lên được giảm 10% trên tiền học phí (học viên lớn + học viên nhỏ tuổi).
3. Phí giáo trình bản in: 250.000 đồng/bộ. Phí giáo trình không được giảm giá.
4. Tổng tiền = tiền học phí sau giảm + phí giáo trình.

hãy suy luận từng bước theo thứ tự tiền học viên lớn -> tiền học viên nhỏ tuổi -> tiền học phí -> giảm giá nhóm -> phí giáo trình -> tổng tiền dòng cuối có dạng [RESULT:<tổng tiền> đồng]. 

áp dụng yêu cầu báo giá:
YÊU CẦU BÁO GIÁ
Nhóm đăng ký khoá NP12 gồm 4 học viên lớn, 2 học viên nhỏ tuổi (11 tuổi và 14 tuổi) và 1 bé 8 tuổi học dự thính. Nhóm mua 3 bộ giáo trình bản in.




```

## 4.4. Dây chuyền xử lý khiếu nại (Prompt Chaining)

### a) Prompt Trạm 1

**PROMPT**

```text
- EMAIL KHIẾU NẠI CỦA KHÁCH

Tôi đăng ký khoá Giao tiếp cơ bản GT01 cho 2 học viên (tôi và em trai), học offline từ 03/11/2026. Hai tuần qua có 4 buổi học bị huỷ mà trung tâm không báo trước, chúng tôi đến lớp mới biết. Cô giáo Hà dạy rất dễ hiểu, tôi không có gì phàn nàn về giáo viên. Tôi đề nghị trung tâm giải quyết thỏa đáng.

======================================================
CHÍNH SÁCH ĐỀN BÙ CỦA SKYENGLISH
======================================================

- huy_buoi: buổi học bị huỷ không báo trước: hoàn 250.000 đồng/học viên cho mỗi buổi bị huỷ.
- hoc_lieu: thiếu hoặc sai giáo trình: tặng giáo trình mới trị giá 250.000 đồng/học viên.
- giao_vien: khiếu nại về thái độ, chất lượng giáo viên: tặng voucher 300.000 đồng/học viên.
- khac: chuyển bộ phận Chăm sóc học viên xem xét, chưa đề xuất mức đền bù.
- Tổng mức đền bù trên 1.500.000 đồng phải được Giám đốc trung tâm duyệt trước khi gửi khách

qua nội dung trên, hãy trả cho tôi đầu ra trả về một đối tượng JSON có 4 trường:{"loai_su_co": một trong "huy_buoi" | "hoc_lieu" | "giao_vien" | "khac", "so_hoc_vien", "so_buoi_bi_huy", "tom_tat"}

```

### b) Hai điều cần kiểm tra ở JSON đầu ra của Trạm 1

1. kiểm tra lại xem đầu ra của trạm 1 đã trả về đúng đối tượng JSON chưa 
2. kiểm tra lại xem đầu ra của trạm 1 đã trả về đúng 4 trường đã nêu chưa

### c) Câu lệnh viết tiếp

**CAU LENH**

```text
hãy viết tiếp nội dung ở phần bị ngắt, không viết lại nội dung đã có
```

## 4.5. Prompt chấm bài theo Rubric

**PROMPT**

```text
CÂU HỎI CỦA KHÁCH
Khoá IELTS 5.5 học phí bao nhiêu? Nếu tôi đã học 6 buổi rồi muốn rút thì có được hoàn tiền không?
CÂU TRẢ LỜI CỦA NHÂN VIÊN TƯ VẤN TẬP SỰ (Dạ chào chị ạ! IELTS 5.5 bên em 6.900.000đ thôi chị, học xong là chắc đậu luôn ạ. Chị học 6 buổi rồi rút thì vẫn được hoàn một nửa nha chị. Có gì chị nhắn em nhé!)

- hãy chấm điểm câu trả lời dựa trên 3 tiêu chí

THÔNG TIN CHUẨN CỦA CÔNG TY
- Học phí khoá IE55: 7.500.000 đồng/học viên lớn.
- Chính sách hoàn học phí: rút trước buổi học đầu tiên hoàn 100%; rút sau buổi 1 đến hết buổi 5 hoàn 50%; từ buổi 6 trở đi không hoàn.

RUBRIC CHẤM (thang 10)
- Đúng thông tin (50%): giá và chính sách hoàn học phí đúng với thông tin chuẩn.
- Đầy đủ (30%): trả lời đủ cả hai câu hỏi của khách và mời khách cho biết hình thức học (online/offline) và ngày muốn khai giảng.
- Giọng điệu (20%): lịch sự, chuyên nghiệp, không dùng từ ngữ suồng sã.

- mỗi lỗi trừ điểm có đủ câu: câu bị lỗi(trích nguyên văn),lý do sai ,câu sửa đề xuất
· Kết quả là bảng Markdown 4 cột Tiêu chí | Điểm | Minh chứng | Đề xuất sửa; dòng
cuối là tổng điểm trên thang 10.

```

## 4.6. Hoàn thiện System Prompt

> Phần Vai trò và Chuẩn đầu ra đã cho sẵn. Viết tiếp phần Quy tắc ràng buộc và Xử lý ngoại lệ.

```text
[Vai trò]
Bạn là "Trợ lý SkyEnglish", nhân viên tư vấn trên website của trung tâm tiếng Anh SkyEnglish, giúp khách chọn và đăng ký một trong 3 khoá: GT01 (Giao tiếp cơ bản), IE55 (Luyện thi IELTS 5.5), NP12 (Ngữ pháp nền tảng).

[Quy tắc ràng buộc]
1. chỉ tư vấn 3 khóa học của công ty
2.không hứa giảm giá ngoài giá bảng 
3.không hỏi số cccd , số thẻ ngân hàng  

[Chuẩn đầu ra]
Trả lời bằng tiếng Việt, lịch sự, tối đa 120 từ. Học phí trình bày dạng gạch đầu dòng. Kết thúc bằng một câu hỏi về nhu cầu tiếp theo của khách.

[Xử lý ngoại lệ]
- Khách hỏi ngoài phạm vi: trả lời thẳng:" công ty chúng tôi không hỗ trợ thông tin này "
- Khách cung cấp thiếu thông tin: trả lời là "vui lòng cung cấp đủ thông tin" 
```
