# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** quyenne3704@gmail.com
**Student ID:** AI-20K-2A202600676
**Name:** Đào Duy Quyền

## Mô tả

Đây là bài lab xây dựng một pipeline ETL đơn giản bằng Python. Chương trình đọc dữ liệu từ file JSON, kiểm tra chất lượng dữ liệu, biến đổi dữ liệu theo yêu cầu của bài, sau đó lưu kết quả ra file CSV. Mục tiêu của bài là luyện cách xử lý dữ liệu có kiểm soát và quan sát được chất lượng đầu ra của pipeline.

## What this project does

- Đọc dữ liệu gốc từ `raw_data.json`
- Loại bỏ record không hợp lệ
- Tạo cột `discounted_price`
- Chuẩn hóa `category` sang Title Case
- Thêm cột `processed_at` để theo dõi thời điểm xử lý
- Xuất dữ liệu cuối cùng ra `processed_data.csv`

## How to Run

### 1. Cài đặt thư viện cần thiết

```bash
pip install pandas pytest
```

### 2. Chạy ETL pipeline

```bash
python solution.py
```

Sau khi chạy xong, file `processed_data.csv` sẽ được tạo ra trong thư mục gốc của project. Output trên terminal cũng sẽ cho biết số record hợp lệ và số record bị loại.

### 3. Chạy kiểm tra tự động

```bash
python -m pytest tests/test_autograder.py -v
```

Lệnh này dùng để kiểm tra toàn bộ các yêu cầu của bài lab, bao gồm:

- script có chạy được không
- validation có loại dữ liệu lỗi không
- transformation có đúng không
- log có hiển thị số liệu xử lý không
- file báo cáo và cấu trúc repo có đầy đủ không

## Cấu trúc thư mục

```text
solution.py          # Script ETL chính
raw_data.json         # Dữ liệu đầu vào
processed_data.csv    # Kết quả sau xử lý
experiment_report.md  # Báo cáo thí nghiệm
README.md             # Tài liệu hướng dẫn
tests/                # Bộ test tự động
```

## Kết quả mong đợi

Với bộ dữ liệu mẫu hiện có, pipeline sẽ giữ lại các record hợp lệ, loại bỏ record có `price <= 0` hoặc `category` rỗng, rồi tạo ra file CSV cuối cùng có đủ các cột cần thiết. Khi hoàn thành đúng yêu cầu, repo sẽ sẵn sàng để nộp qua GitHub Classroom và chạy chấm tự động.
