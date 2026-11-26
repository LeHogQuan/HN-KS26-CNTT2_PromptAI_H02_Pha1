# BÀI LÀM PHA 2 – HACKATHON 02

- **Mã đề:** 04
- **Họ tên:** Lê Hồng Quân
- **Lớp:** CNTT2
- **Link repository Pha2:**
- **Công cụ AI đã dùng (ChatGPT/Claude/Gemini):**ChatGPT

> Pha 2 (20 phút cuối). Mỗi mục: mở cuộc trò chuyện mới, gửi nguyên văn prompt đã viết trong bai_lam_pha1.md, dán câu trả lời và link chia sẻ vào đây. Xong, kéo thả file này vào repository Pha2.

## 4.2. Trích xuất tin nhắn đặt vé xe ra JSON

**KET QUA AI**

```text
[
  {
    "ma_tuyen": "SGDL",
    "ngay_di": "2026-12-22",
    "ve_nguoi_lon": 2,
    "ve_tre_em": 1,
    "loai_cho": "giuong",
    "ghi_chu": null
  },
  {
    "ma_tuyen": "SGNT",
    "ngay_di": "2027-01-02",
    "ve_nguoi_lon": null,
    "ve_tre_em": null,
    "loai_cho": null,
    "ghi_chu": "3 vé, trong đó có 1 người mang thai 6 tháng"
  },
  {
    "ma_tuyen": "SGCT",
    "ngay_di": null,
    "ve_nguoi_lon": 4,
    "ve_tre_em": 0,
    "loai_cho": "ghe",
    "ghi_chu": "bà nội đi xe lăn"
  }
]
```

**Link trò chuyện:** https://chatgpt.com/share/6b079deb-9dc4-83ec-a012-c8da115821b2

## 4.3. Báo giá bằng Chain-of-Thought

**KET QUA AI**

```text
B1: Xác định tuyến xe và giá vé người lớn
- Tuyến SGDL: 320.000 đồng/vé
- Số người lớn: 8 người
- Tiền vé người lớn = 8 × 320.000 = 2.560.000 đồng
B2: Tính tiền vé trẻ em
- Trẻ 6, 7 và 9 tuổi đều tính 75% giá vé người lớn
- Giá vé trẻ em = 320.000 × 75% = 240.000 đồng
- Tiền vé 3 trẻ em = 3 × 240.000 = 720.000 đồng
B3: Tính tiền vé trẻ dưới 5 tuổi
- Có 1 bé 2 tuổi ngồi cùng người lớn nên được miễn phí
- Tiền vé = 0 đồng
B4: Tính tổng tiền vé trước giảm giá

- 2.560.000 + 720.000 + 0 = 3.280.000 đồng

B5: Tính tiền vé sau giảm giá
- Đoàn có 8 người lớn, đủ điều kiện giảm 5%
- Số tiền được giảm = 3.280.000 × 5% = 164.000 đồng
- Tiền vé sau giảm = 3.280.000 - 164.000 = 3.116.000 đồng
B6: Tính phụ thu và tổng tiền thanh toán
- Phụ thu hành lý = 2 × 100.000 = 200.000 đồng
- Tổng tiền thanh toán = 3.116.000 + 200.000 = 3.316.000 đồng
[RESULT: 3.316.000 đồng]
```

**Link trò chuyện:**https://chatgpt.com/share/6b079ff3-dbc0-83ec-ba57-d978778f4dc9

### b) Kiểm tra kết quả AI

(Ghi kết luận AI đúng hay sai; nếu sai, ghi bước sai đầu tiên và kết quả đúng của bước đó – xoá dòng này)

## 4.4. Dây chuyền xử lý khiếu nại – kết quả Trạm 1

**KET QUA AI**

```text
{
  "loai_su_co": "sai_loai_xe",
  "so_khach": 3,
  "so_chang_bi_doi": 2,
  "tom_tat": "Đặt giường nằm nhưng cả chặng đi và về đều bị đổi sang xe ghế ngồi"
}
```

**Link trò chuyện:**https://chatgpt.com/share/6b079e9a-c658-83ec-bebc-ad950077ca27

## 4.5. Prompt chấm bài theo Rubric

**KET QUA AI**

```text

| Tiêu chí | Điểm | Minh chứng | Đề xuất sửa |
|---|---:|---|---|
| 1. Đúng thông tin (50%) | 1/5 | Câu bị lỗi: "Vé đi Nha Trang bên em 350.000đ nha chị" - Sai giá vé, giá chuẩn là 380.000đ/vé người lớn. Câu bị lỗi: "Chị đổi trước 12 tiếng thì đổi free nha chị" - Sai chính sách, đổi trước 12 giờ thuộc mức từ 6 đến dưới 24 giờ, phải trả phí 20% giá vé (76.000đ) | "Vé đi Nha Trang có giá 380.000đ/vé người lớn. Đổi trước 24 giờ miễn phí, từ 6 đến dưới 24 giờ phí 20% giá vé, dưới 6 giờ không được đổi" |
| 2. Đầy đủ (30%) | 0/3 | Chưa trả lời đầy đủ chính sách đổi vé và chưa mời khách cung cấp ngày đi, số vé để đặt chỗ | "Chị vui lòng cung cấp ngày đi và số vé để em hỗ trợ đặt chỗ ạ" |
| 3. Giọng điệu (20%) | 0,5/2 | Câu bị lỗi: "xe xịn lắm luôn", "Cần gì chị nhắn em liền!" - Sử dụng từ ngữ suồng sã, thiếu tính chuyên nghiệp | "Dạ, em sẵn sàng hỗ trợ chị nếu chị cần thêm thông tin ạ" |
| **Tổng điểm** | **1,5/10** | | |

```

**Link trò chuyện:**https://chatgpt.com/share/6b079fb8-f164-83ec-a0ef-9ae38854e300
