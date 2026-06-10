# Experiment Report: Tác động của chất lượng dữ liệu đến AI Agent

**Student ID:** AI20K-XXXX  
**Name:** Dien ten cua ban  
**Date:** 2026-06-10

## 1. Kết quả thí nghiệm

Chạy `agent_simulation.py` với 2 bộ dữ liệu và ghi lại kết quả:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent chọn Laptop là phương án tốt nhất trong nhóm electronics vì đây là sản phẩm có giá cao nhất trong tập dữ liệu sạch. | 9 | Dữ liệu đã được lọc lỗi, category đồng nhất, nên truy vấn hoạt động ổn định và dễ kiểm tra. |
| Garbage Data (`garbage_data.csv`) | Agent có thể trả về kết quả sai, không ổn định, hoặc báo lỗi khi gặp duplicate IDs, sai kiểu dữ liệu, outliers và null values. | 3 | Dữ liệu bẩn làm logic truy vấn bị nhiễu và giảm đáng kể độ tin cậy của câu trả lời. |

## 2. Phân tích & nhận xét (Phan tich)

### Tại sao Agent trả lời sai khi dùng Garbage Data?

Dữ liệu rác làm agent trả lời sai vì nó phá vỡ các giả định cơ bản về tính sạch và tính nhất quán của dữ liệu đầu vào. Khi xuất hiện duplicate IDs, cùng một thực thể có thể bị ghi đè hoặc bị đếm lặp, dẫn đến kết quả truy xuất không còn phản ánh đúng dữ liệu gốc. Khi giá trị `price` là chuỗi thay vì số, các phép so sánh, sắp xếp hoặc lấy giá trị lớn nhất có thể lỗi hoặc cho ra kết quả không đáng tin cậy. Những outliers quá lớn cũng làm mô hình hoặc logic truy vấn ưu tiên nhầm một bản ghi bất thường thay vì lựa chọn hợp lý nhất. Ngoài ra, null values và category rỗng khiến bộ lọc theo điều kiện hoạt động không đúng, làm mất những record cần thiết hoặc trả về kết quả trống. Tóm lại, dù câu hỏi của người dùng có rõ ràng đến đâu, nếu dữ liệu đầu vào bị lỗi thì agent vẫn dễ suy luận sai, trả lời thiếu nhất quán và mất tính tin cậy.

## 3. Kết luận

**Quality Data > Quality Prompt?** Đồng ý. Một prompt tốt không thể bù đắp hoàn toàn cho dữ liệu đầu vào kém chất lượng. Khi dữ liệu sạch, đầy đủ và đồng nhất, agent sẽ có nền tảng tốt hơn để truy xuất, so sánh và suy luận. Ngược lại, dữ liệu bẩn làm tăng nguy cơ lỗi logic, sai lệch kết quả và giảm độ tin cậy của toàn bộ hệ thống.
