[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=24112869&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** 26ai.giangdt@vinuni.edu.vn
**Name:** Dương Trường Giang

---

## Mo ta

(Mo ta ngan gon bai lab va nhung gi ban da lam)

Lab Day 10: Data Pipeline & Data Observability
1. Data Pipeline

Tôi đã tạo một Auto-trigger ETL Pipeline sử dụng Python. 
Pipeline này tự động thực hiện 4 bước: Extract -> Validate -> Transform -> Load.

Dữ liệu đầu vào:

raw_data.json

 (3000 records).

Kết quả:

processed_data.csv

 với 2700 records (loại bỏ 300 records lỗi).

2. Data Observability

Thí nghiệm mô phỏng AI Agent:

Scenario 1: Dữ liệu sạch (Clean Data) -> Agent trả lời đúng

Scenario 2: Dữ liệu rác (Garbage Data) -> Agent trả lời sai (ví dụ: "Nuclear Reactor at $999999")

Kết luận: Data Quality quan trọng hơn Quality Prompt. Dù prompt có hay đến đâu mà dữ liệu rác thì Agent vẫn sai.

---

## Cách chạy (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# Mo ta cach ban chay thi nghiem Clean vs Garbage data
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

(Tom tat ket qua: bao nhieu records da xu ly, bao nhieu bi loai, v.v.)
