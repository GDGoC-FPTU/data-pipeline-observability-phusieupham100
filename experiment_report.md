# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-2A202600283
**Student email** : phungphu02@gmail.com
**Name:** Phung Huu Phu
**Date:** 2026-04-15

---

## 1. Kết quả thí nghiệm

Chạy `agent_simulation.py` với 2 bộ dữ liệu và ghi lại kết quả:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Kết quả hợp lý, dữ liệu sạch nên Agent tìm đúng sản phẩm electronics giá cao nhất. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | Bị outlier giá quá lớn và dữ liệu độc hại dẫn đến gợi ý phi thực tế. |

---

## 2. Phân tích & nhận xét (Phan tich & nhan xet)

### Tại sao Agent trả lời sai khi dùng Garbage Data? (Tai sao Agent tra loi sai)

Agent trong bài này sử dụng luật rất đơn giản: lọc category electronics rồi chọn record có giá cao nhất.
Khi dữ liệu bị "poisoned", record outlier "Nuclear Reactor" có giá 999999 áp đảo toàn bộ record hợp lý khác,
nên Agent luôn ưu tiên kết quả sai. Ngoài ra, duplicate ID làm giảm độ tin cậy của kho dữ liệu vì một ID có thể đại
diện cho nhiều sản phẩm khác nhau. Wrong data type (ví dụ "ten dollars") có thể gây lỗi trong quá trình so sánh hoặc
tính toán. Null values ở cột quan trọng cũng làm mất ngữ cảnh truy vấn. Tổng hợp các vấn đề này cho thấy nếu không làm
sạch dữ liệu, prompt có tốt đến đâu thì output vẫn dễ bị nhiễu và mất tính ứng dụng thực tế.

---

## 3. Kết luận

**Quality Data > Quality Prompt?** (Đồng ý hay không? Giải thích ngắn gọn.)

Đồng ý. Prompt giúp định hướng câu trả lời, nhưng chất lượng dữ liệu mới là nền tảng để Agent suy luận đúng.
Nếu dữ liệu đầu vào sai, thiếu, hoặc bị poison thì Agent sẽ học và trả lời theo thông tin sai. Vì vậy, data quality
là điều kiện tiên quyết để có AI output đáng tin cậy.
