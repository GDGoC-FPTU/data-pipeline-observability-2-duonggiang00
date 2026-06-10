# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600990
**Name:** Dương Trường Giang
**Date:** 11/06/2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Based on my data, the best choice is Laptop at $1200. | 10 | |
| Garbage Data (`garbage_data.csv`) | Based on my data, the best choice is Nuclear Reactor at $999999. | 1 | |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi sử dụng dữ liệu "Garbage Data", Agent đưa ra câu trả lời sai vì dữ liệu bị nhiễu (corrupted).
Các vấn đề cụ thể bao gồm:

1. **Dữ liệu rác (Garbage Values):** Trong tập dữ liệu rác có chứa các giá trị không hợp lệ như "Poisoned", "-1", "0", và null values.
   - Các giá trị "-1" và "0" làm sai lệch dữ liệu nhập vào mô hình, khiến Agent nghĩ rằng có sản phẩm với giá tiền cực thấp hoặc bằng 0.
   - Các nhãn "Poisoned" làm hỏng vector embeddings, khiến Agent không thể nhận diện đúng category sản phẩm.

2. **Dữ liệu trùng lặp (Duplicate Data):** Tập dữ liệu rác có dữ liệu trùng lặp nhiều lần, làm sai lệch phân phối dữ liệu.
   - Điều này khiến Agent nghĩ rằng các sản phẩm "Poisoned" là phổ biến, trong khi thực tế chúng chỉ là dữ liệu rác được lặp lại.

3. **Dữ liệu không hợp lệ (Invalid Data):** Các sản phẩm với giá trị null hoặc dữ liệu rác làm sai lệch các tính năng thống kê như min, max, mean.
   - Khi Agent tìm kiếm sản phẩm có giá cao nhất, nó có thể chọn nhầm các sản phẩm "Poisoned" vì chúng có giá trị được lặp lại nhiều lần.

Kết quả là, Agent đưa ra câu trả lời sai vì dữ liệu được truyền vào mô hình không chính xác và không phản ánh đúng thực tế. Điều này cho thấy tầm quan trọng của việc tiến hành xử lý dữ liệu (data preprocessing) trước khi sử dụng dữ liệu cho các mô hình AI.

---

## 3. Kết luận

**Quality Data > Quality Prompt?** (Dong y hay khong? Giai thich ngan gon.)

(Viet ket luan cua ban o day)
Đồng ý. Dữ liệu chất lượng cao là nền tảng để mô hình AI hoạt động hiệu quả, trong khi prompt chỉ là công cụ để tương tác với dữ liệu. Nếu dữ liệu bị nhiễu hoặc không chính xác, mô hình sẽ đưa ra kết quả sai, bất kể prompt có tốt đến đâu.