# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-XXXX
**Name:** (Dien ten cua ban)
**Date:** (Dien ngay thuc hien)

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

Khi su dung du lieu "Garbage Data", Agent dua ra cau tra loi sai vi du lieu bi nhiem ban (corrupted).
Cac van de cu the bao gom:

1. **Du lieu rac (Garbage Values):** Trong tap du lieu rac co chua cac gia tri khong hop le nhu "Poisoned", "-1", "0", va null values.
   - Cac gia tri "-1" va "0" lam sai chech du lieu nhap vao mo hình, khien Agent nghi rang co san pham voi gia tien cuc thap hoac bang 0.
   - Cac nhan xet "Poisoned" lam hu vector embeddings, khien Agent khong the nhan dien dung category san pham.

2. **Du lieu trung lap (Duplicate Data):** Tap du lieu rac co du lieu trung lap nhieu lan, lam sai chech phan phoi du lieu.
   - Dieu nay khien Agent nghi rang cac san pham "Poisoned" la pho bien, trong khi thuc te chung chi la du lieu rac duoc lap lai.

3. **Du lieu khong hop le (Invalid Data):** Cac san pham voi gia tri null hoac du lieu rac lam sai lech cac tinh nang thong ke nhu min, max, mean.
   - Khi Agent tim kiem san pham co gia cao nhat, no co the chon nham cac san pham "Poisoned" vi chung co gia tri duoc lap lai nhieu lan.

Ket qua la, Agent dua ra cau tra loi sai vi du lieu duoc truyen vao mo hình khong chinh xac va khong phan anh dung thuc te. Dieu nay cho thay tam quan trong cua viec tien hanh xu ly du lieu (data preprocessing) truoc khi su dung du lieu cho cac mo hình AI.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** (Dong y hay khong? Giai thich ngan gon.)

(Viet ket luan cua ban o day)
Đồng ý. Dữ liệu chất lượng cao là nền tảng để mô hình AI hoạt động hiệu quả, trong khi prompt chỉ là công cụ để tương tác với dữ liệu. Nếu dữ liệu bị nhiễu hoặc không chính xác, mô hình sẽ đưa ra kết quả sai, bất kể prompt có tốt đến đâu.