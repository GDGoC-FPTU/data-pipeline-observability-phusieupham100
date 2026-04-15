[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23573927&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** 26ai.phuph@vinuni.edu.vn
**Student ID:** AI20K-2A202600283
**Name:** Phu Phung


---

## Mô tả

Bài lab này xây dựng một ETL pipeline có khả năng kiểm soát chất lượng dữ liệu và quan sát qua logging.
Pipeline đọc dữ liệu JSON, loại bỏ record không hợp lệ (giá <= 0 hoặc category rỗng), sau đó transform dữ liệu
bằng cách thêm cột `discounted_price`, chuẩn hóa `category` về Title Case, và gắn timestamp `processed_at`.
Cuối cùng dữ liệu được lưu thành `processed_data.csv` để sử dụng cho bước mô phỏng AI Agent.

---

## Cách chạy (How to Run)

### Prerequisites
```bash
pip install pandas pytest
```

### Chạy ETL Pipeline
```bash
python solution.py
```

### Chạy Agent Simulation (Stress Test)
```bash
python generate_garbage.py
python agent_simulation.py
```

---

## Cấu trúc thư mục

```
├── solution.py              # Script ETL pipeline
├── processed_data.csv       # Output của pipeline
├── experiment_report.md     # Báo cáo thí nghiệm
└── README.md                # File này
```

---

## Kết quả

- Tổng số record extract từ `raw_data.json`: 5
- Số record hợp lệ sau validation: 3
- Số record bị loại: 2
- File output tạo thành công: `processed_data.csv`
- Stress test cho thấy Agent với clean data trả lời hợp lý ("Laptop"), nhưng với garbage data bị ảnh hưởng bởi outlier và trả lời sai ("Nuclear Reactor")
