# Paper 19 Summary

## Citation

Tên bài: BEIR: A Heterogeneous Benchmark for Zero-shot Evaluation of Information Retrieval Models
Tác giả: Nandan Thakur, Nils Reimers, Andreas Rücklé, Abhishek Srivastava, Iryna Gurevych (UKP Lab, Technische Universität Darmstadt)
Năm: 2021
Nguồn: Proceedings of the Neural Information Processing Systems Track on Datasets and Benchmarks 1 (NeurIPS 2021 Datasets and Benchmarks, Round 2) — có bình duyệt
DOI/Link: https://datasets-benchmarks-proceedings.neurips.cc/paper/2021/hash/65b9eea6e1cc6bb9f0cd2a47751a186f-Abstract-round2.html (bản mở: https://arxiv.org/abs/2104.08663)

## Problem

**Tóm tắt tổng quan.** BEIR là benchmark đánh giá khả năng tổng quát zero-shot (ngoài phân phối huấn luyện) của các mô hình truy xuất thông tin, gồm 18 bộ dữ liệu thuộc 9 loại tác vụ và nhiều miền. Bài đánh giá 10 hệ thống thuộc 5 kiến trúc: từ vựng, sparse, dense, late-interaction và rerank. Kết luận chính: BM25 là baseline rất bền vững; rerank (BM25 + cross-encoder) và late-interaction (ColBERT) tổng quát tốt nhất nhưng tốn kém; các mô hình dense hiệu quả về tính toán nhưng thường kém BM25 khi gặp miền mới.

**Bối cảnh và động lực.** Các mô hình truy xuất neural thường được huấn luyện và đánh giá trên cùng một bộ dữ liệu lớn (MS MARCO, NQ), nơi chúng vượt BM25 rõ rệt. Trong thực tế, nhiều hệ thống phải chạy zero-shot vì không có dữ liệu huấn luyện trong miền. Các benchmark trước (MultiReQA, KILT) hẹp về tác vụ hoặc miền (chủ yếu Wikipedia), nên chưa trả lời được câu hỏi mô hình nào tổng quát tốt.

## Method

1. **Chọn dữ liệu theo bốn tiêu chí:** đa dạng tác vụ (kiểm chứng sự thật, dự đoán trích dẫn, câu hỏi trùng lặp, truy xuất lập luận, tin tức, QA, tweet, y sinh, thực thể); đa dạng miền; đủ khó; đa dạng cách chú thích.
2. **Định dạng thống nhất** (corpus, queries, qrels) và thư viện Python mã nguồn mở (`pip install beir`).
3. **Chỉ số chung:** nDCG@10 (phù hợp cả nhãn nhị phân lẫn nhãn phân mức).
4. **Mô hình đánh giá:** BM25 (Anserini); sparse: DeepCT, SPARTA, docT5query; dense: DPR, ANCE, TAS-B, GenQ (thích nghi miền bằng truy vấn tổng hợp); late-interaction: ColBERT; rerank: BM25 lấy top-100 rồi cross-encoder MiniLM chấm lại. Mọi văn bản bị cắt ở 512 word piece đầu.
5. **Phân tích hiệu năng** (độ trễ, kích thước chỉ mục trên 1 triệu văn bản DBPedia) và **phân tích thiên lệch chú thích** (Hole@10 trên TREC-COVID, chú thích bổ sung 980 cặp).

```mermaid
flowchart LR
    D[18 bộ dữ liệu, 9 tác vụ] --> F[Định dạng chung: corpus / queries / qrels]
    F --> L[Từ vựng: BM25]
    F --> S[Sparse: DeepCT, SPARTA, docT5query]
    F --> DE[Dense: DPR, ANCE, TAS-B, GenQ]
    F --> LI[Late-interaction: ColBERT]
    F --> RR[Rerank: BM25 top-100 → cross-encoder]
    L & S & DE & LI & RR --> M[nDCG@10, Recall@100, độ trễ, kích thước chỉ mục]
```

## Dataset

18 bộ tiếng Anh: TREC-COVID, NFCorpus, BioASQ, NQ, HotpotQA, FiQA-2018, Signal-1M, TREC-NEWS, Robust04, ArguAna, Touché-2020, CQADupStack, Quora, DBPedia, SCIDOCS, FEVER, Climate-FEVER, SciFact. Kho văn bản từ 3,6 nghìn đến 15 triệu tài liệu; độ dài truy vấn trung bình từ 3 đến 192 từ. Không có bộ dữ liệu pháp lý.

## Evaluation

nDCG@10 (chính), Recall@100 (phụ lục); độ trễ truy xuất trên GPU/CPU; kích thước chỉ mục; tỷ lệ Hole@10 (kết quả top-10 chưa được chú thích).

## Results

- **Trên MS MARCO (trong miền):** BM25 0,228 thấp hơn các mô hình neural 7–18 điểm, nhưng trên BEIR lại là baseline mạnh.
- **So với BM25 (trung bình trên BEIR):** BM25 + CE +11%; ColBERT +2,5%; docT5query +1,6%; TAS-B −2,8%; GenQ −3,6%; ANCE −7,4%; SPARTA −20,3%; DeepCT −27,9%; DPR −47,7%.
- BM25 + CE vượt BM25 trên 16/18 bộ (chỉ thua ArguAna và Touché-2020); docT5query vượt trên 11/18; ColBERT trên 9/18.
- Dense kém khi dịch chuyển miền (ví dụ BioASQ: BM25 0,465, TAS-B 0,383, DPR 0,127). TAS-B ưa văn bản ngắn (trung vị 10 từ so với 160 từ của ANCE trên TREC-COVID).
- **Hiệu năng (1 triệu tài liệu):** BM25 + CE 450 ms (GPU) / 6.100 ms (CPU); ColBERT 350 ms với chỉ mục 20 GB; TAS-B 14 ms (GPU) với chỉ mục 3 GB; BM25 20 ms (CPU) với chỉ mục 0,4 GB.
- **Thiên lệch chú thích:** Hole@10 của BM25 là 6,4% nhưng của TAS-B là 31,8%. Sau khi chú thích bổ sung, ANCE trên TREC-COVID tăng từ 0,654 lên 0,735, trong khi BM25 chỉ tăng từ 0,656 lên 0,668 — tức nhiều bộ dữ liệu thiên vị phương pháp từ vựng.

**Điểm mạnh.**

- Benchmark rộng, công khai, định dạng chuẩn, thành tiêu chuẩn đánh giá truy xuất zero-shot.
- So sánh công bằng nhiều kiến trúc kèm chi phí (độ trễ, bộ nhớ) — rất hữu ích cho quyết định triển khai.
- Chỉ ra và định lượng thiên lệch chú thích theo hướng từ vựng.

## Limitations

**(a) Bài báo thừa nhận:** nhiều bộ dữ liệu có thiên lệch từ vựng do cách tạo nhóm ứng viên chú thích, gây bất lợi cho phương pháp không dựa trên từ vựng; cần bộ dữ liệu với chiến lược pooling đa dạng hơn.

**(b) Quan sát:** chỉ tiếng Anh; văn bản cắt ở 512 word piece; không đánh giá truy xuất lai (BM25 + dense) hay các mô hình embedding đa ngôn ngữ đời mới; dữ liệu đã cũ so với thế hệ mô hình hiện tại. Bài **không** đánh giá chất lượng câu trả lời sinh ra sau truy xuất.

## Relevance to our topic

BEIR là bằng chứng có bình duyệt cho lựa chọn kiến trúc của Sys_3_4: (1) truy xuất từ vựng (BM25/IDF) bền vững khi chuyển miền, nhanh và nhẹ — phù hợp Strict Engine chạy trên CPU với độ trễ mili-giây; (2) rerank bằng cross-encoder cải thiện chất lượng nhưng tốn hàng trăm mili-giây — hợp lý cho Friendly Engine vốn đã có ngân sách độ trễ cao hơn; (3) embedding dense chưa tinh chỉnh có thể kém BM25 ở miền chuyên biệt — cần kiểm chứng BGE-M3 trên dữ liệu thủ tục thay vì mặc định tin tưởng.

**Kết luận.** BEIR cho thấy hiệu năng trong miền không dự báo được khả năng tổng quát: BM25 vẫn là baseline mạnh, rerank và late-interaction tổng quát tốt nhất nhưng đắt, còn dense nhanh nhưng dễ kém khi đổi miền. Tác giả kêu gọi xây dựng bộ dữ liệu ít thiên lệch hơn và mô hình truy xuất bền vững hơn.

## Possible improvement

- Đánh giá Strict Engine và Friendly Engine trên cùng một tập truy vấn bằng nDCG@10 và Recall@100 theo cách của BEIR, kèm độ trễ và kích thước chỉ mục.
- Khi tạo nhãn cho bộ đánh giá của nhóm, gộp ứng viên từ cả hai engine (pooling đa dạng) để tránh thiên lệch về phía phương pháp từ vựng như bài cảnh báo.
