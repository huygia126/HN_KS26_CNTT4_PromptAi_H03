# BÀI LÀM PHA 2 – HACKATHON 02

- **Mã đề:** 03
- **Họ tên:** Chu Gia Huy
- **Lớp:** CNTT4
- **Link repository Pha2:**
- **Công cụ AI đã dùng (ChatGPT/Claude/Gemini):** ChatGpt

> Pha 2 (20 phút cuối). Mỗi mục: mở cuộc trò chuyện mới, gửi nguyên văn prompt đã viết trong bai_lam_pha1.md, dán câu trả lời và link chia sẻ vào đây. Xong, kéo thả file này vào repository Pha2.

## 4.2. Trích xuất tin nhắn đăng ký khoá học ra JSON

**KET QUA AI**

```text
[
  {
    "ma_khoa": "NN01",
    "ngay_khai_giang": "2026-12-08",
    "hoc_vien_lon": 2,
    "hoc_vien_nho": 1,
    "hinh_thuc": "offline",
    "ghi_chu": null
  },
  {
    "ma_khoa": "IE55",
    "ngay_khai_giang": "2027-01-06",
    "hoc_vien_lon": 3,
    "hoc_vien_nho": 0,
    "hinh_thuc": null,
    "ghi_chu": "một học viên bị khiếm thính nhẹ"
  },
  {
    "ma_khoa": "GT01",
    "ngay_khai_giang": null,
    "hoc_vien_lon": 4,
    "hoc_vien_nho": 0,
    "hinh_thuc": "offline",
    "ghi_chu": "một học viên đi nạng"
  }
]
```

**Link trò chuyện:** https://chatgpt.com/share/6afd0297-ee88-83ec-be2b-c63acaa8877c

## 4.3. Báo giá bằng Chain-of-Thought

**KET QUA AI**

```text
### **a) Tính tổng tiền cho yêu cầu báo giá**

**Khóa học:** NP12 – Ngữ pháp nền tảng (12 buổi)\
**Học phí học viên lớn:** 2.400.000 đồng/người.

**Bước 1: Tính tiền học viên lớn**

Có 4 học viên lớn:

4 × 2.400.000 = **9.600.000 đồng**

**Bước 2: Tính tiền học viên nhỏ tuổi**

Học viên nhỏ tuổi từ 10–15 tuổi được tính 60% học phí.

- Bé 11 tuổi: 2.400.000 × 60% = 1.440.000 đồng.
- Bé 14 tuổi: 2.400.000 × 60% = 1.440.000 đồng.

Tổng tiền học viên nhỏ tuổi:

1.440.000 × 2 = **2.880.000 đồng**

Bé 8 tuổi học dự thính cùng phụ huynh nên **miễn phí**.

**Bước 3: Tính tổng tiền học phí**

9.600.000 + 2.880.000 = **12.480.000 đồng**

**Bước 4: Tính giảm giá nhóm**

Nhóm có 4 học viên lớn trở lên nên được giảm 10% trên tổng học phí.

12.480.000 × 10% = 1.248.000 đồng.

Học phí sau giảm:

12.480.000 − 1.248.000 = **11.232.000 đồng**

**Bước 5: Tính phí giáo trình**

Nhóm mua 3 bộ giáo trình, mỗi bộ 250.000 đồng.

3 × 250.000 = **750.000 đồng**

**Bước 6: Tính tổng tiền**

11.232.000 + 750.000 = **11.982.000 đồng**

**KẾT QUẢ BÁO GIÁ**

# **11.982.000 đồng**

Bằng chữ: Mười một triệu chín trăm tám mươi hai nghìn đồng.

**[RESULT:11982000 đồng]**
```

**Link trò chuyện:** https://chatgpt.com/share/6afd0305-63e0-83ec-80b9-a2287f011d3c

### b) Kiểm tra kết quả AI

đúng 100%

## 4.4. Dây chuyền xử lý khiếu nại – kết quả Trạm 1

**KET QUA AI**

```text
{\
&#x20; "loai_su_co": "huy_buoi",\
&#x20; "so_hoc_vien": 2,\
&#x20; "so_buoi_bi_huy": 4,\
&#x20; "tom_tat": "Khách hàng đăng ký khóa Giao tiếp cơ bản GT01 cho 2 học viên, học offline từ ngày 03/11/2026. Trong hai tuần qua, có 4 buổi học bị hủy mà trung tâm không thông báo trước. Khách hàng hài lòng với chất lượng giảng dạy của cô Hà và không có khiếu nại về giáo viên. Theo chính sách, mức đền bù là 250.000 đồng/học viên/buổi, tổng cộng 2.000.000 đồng. Do tổng mức đền bù vượt 1.500.000 đồng, cần được Giám đốc trung tâm phê duyệt trước khi gửi phản hồi cho khách hàng."\
}
```

**Link trò chuyện:** https://chatgpt.com/share/6afd037a-31d4-83ec-8054-27f84976a121

## 4.5. Prompt chấm bài theo Rubric

**KET QUA AI**

```text
### **BẢNG CHẤM ĐIỂM CÂU TRẢ LỜI CỦA NHÂN VIÊN TƯ VẤN**

| Tiêu chí                    | Điểm    | Minh chứng                                                                                                                                                                                                                                                                                                                                  | Đề xuất sửa                                                                                                                                                                 |
| --------------------------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **1. Đúng thông tin (50%)** | **0/5** | **Lỗi 1:** “IELTS 5.5 bên em 6.900.000đ thôi chị” → Sai học phí. Giá chuẩn là 7.500.000đ/học viên lớn. **Lỗi 2:** “Chị học 6 buổi rồi rút thì vẫn được hoàn một nửa nha chị.” → Sai chính sách. Từ buổi 6 trở đi không được hoàn học phí. **Lỗi 3:** “học xong là chắc đậu luôn ạ.” → Cam kết chắc chắn kết quả đầu ra khi không có căn cứ. | **Câu sửa:** “Dạ, khóa IELTS 5.5 (IE55) có học phí 7.500.000đ/học viên lớn. Theo chính sách trung tâm, học viên rút từ buổi học thứ 6 trở đi sẽ không được hoàn học phí ạ.” |
| **2. Đầy đủ (30%)**         | **1/3** | **Lỗi 1:** “Có gì chị nhắn em nhé!” → Chưa chủ động mời khách cung cấp hình thức học online/offline và ngày muốn khai giảng theo yêu cầu. Nhân viên đã trả lời cả hai câu hỏi nhưng chưa khai thác đủ thông tin tư vấn tiếp theo.                                                                                                           | **Câu sửa:** “Chị dự định đăng ký học online hay offline ạ? Chị muốn khai giảng vào ngày nào để em hỗ trợ tư vấn lịch học phù hợp ạ?”                                       |
| **3. Giọng điệu (20%)**     | **1/2** | **Lỗi 1:** “6.900.000đ thôi chị”, “nha chị”, “Có gì chị nhắn em nhé!” → Cách diễn đạt hơi suồng sã, thiếu tính chuyên nghiệp. **Lỗi 2:** “học xong là chắc đậu luôn ạ” → Cách tư vấn thiếu thận trọng, tạo kỳ vọng không có căn cứ.                                                                                                         | **Câu sửa:** Sử dụng cách diễn đạt lịch sự, chuyên nghiệp như: “Dạ, em xin phép cung cấp thông tin học phí và chính sách hoàn học phí của trung tâm để chị tham khảo ạ.”    |

\| **TỔNG ĐIỂM** | **2/10** | **Nhân viên mắc lỗi nghiêm trọng về học phí và chính sách hoàn tiền.** | **Cần cải thiện độ chính xác thông tin và kỹ năng tư vấn.** |

### **Câu trả lời đề xuất hoàn chỉnh**

“Dạ em chào chị ạ! Khóa IELTS 5.5 (IE55) có học phí là **7.500.000đ/học viên lớn**.

Về chính sách hoàn học phí, trung tâm quy định:

- Rút trước buổi học đầu tiên: hoàn 100%.
- Rút từ buổi 1 đến hết buổi 5: hoàn 50%.
- Từ buổi 6 trở đi: không được hoàn học phí.

Vì chị đã tham gia 6 buổi học nên theo chính sách của trung tâm, trường hợp của chị sẽ không được hoàn học phí ạ.

Chị cho em hỏi chị muốn tham gia khóa học theo hình thức online hay offline, và dự kiến ngày nào muốn khai giảng để em hỗ trợ thêm thông tin cho chị ạ?”
```

**Link trò chuyện:** https://chatgpt.com/share/6afd03ad-3154-83ec-b619-8bedfa489fb4
