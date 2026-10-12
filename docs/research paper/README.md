# Thư Mục Nghiên Cứu Khoa Học (Research Papers) – System 3 & System 4

> **Toàn văn PDF của 33 bài báo** dùng làm nền tảng lý thuyết và cơ sở đối sánh cho dự án Trợ lý Thủ tục Hành chính Công (System 3 Strict Engine + System 4 Friendly Engine). 29 bài đã công bố tại hội nghị/tạp chí có bình duyệt; 4 bài là preprint/báo cáo kỹ thuật được giữ lại có chủ đích (LegalBench-RAG, CRAG, Qwen2.5 Technical Report, Constitutional AI).
> Bản tóm tắt học thuật của từng bài nằm ở `02_related_work/paper_summaries/paper_XX.md` (số XX là số thứ tự trong `02_related_work/paper_list.md`, khác số thứ tự thư mục bên dưới).

> 12 preprint chưa bình duyệt trước đây đã được thay thế và chuyển nguyên trạng vào `_archived_preprints/` để tham khảo.

---

## Cấu trúc thư mục (8 nhóm nghiên cứu)

```
research paper/
├── 01_Public_Sector_LLM_Safety_Privacy/   # An toàn, quyền riêng tư và độ tin cậy LLM trong khu vực công (4 bài)
│   ├── 01_Lukas_2023_PII_Leakage_Language_Models/   → paper_05
│   ├── 02_Greshake_2023_Indirect_Prompt_Injection/   → paper_06
│   ├── 03_Dahl_2024_Large_Legal_Fictions/   → paper_32
│   ├── 04_Rebedea_2023_NeMo_Guardrails/   → paper_33
├── 02_Legal_Regulatory_RAG/   # RAG cho pháp lý và quy định (4 bài)
│   ├── 05_vanderMeer_2026_LegalCheck_Municipal_Advice/   → paper_07
│   ├── 06_Pipitone_2024_LegalBench-RAG/   → paper_08
│   ├── 07_Magesh_2025_Hallucination-Free_Legal_AI_Tools/   → paper_09
│   ├── 08_Kalra_2024_HyPA-RAG_Legal_Policy/   → paper_10
├── 03_Fact-Checking_Verifiers/   # Kiểm chứng sự thật và đo ảo giác (5 bài)
│   ├── 09_Dhuliawala_2023_Chain-of-Verification_CoVe/   → paper_13
│   ├── 10_Asai_2024_Self-RAG_Reflection_Critique/   → paper_14
│   ├── 11_Gou_2024_CRITIC_Self-Correct_Tool_Interactive/   → paper_15
│   ├── 12_Niu_2024_RAGTruth_Hallucination_Corpus/   → paper_16
│   ├── 13_Min_2023_FActScore_Atomic_Factuality/   → paper_17
├── 04_Hybrid_Dual-System_Retrieval/   # Truy hồi lai (5 bài)
│   ├── 14_Yan_2024_CRAG_Corrective_RAG/   → paper_18
│   ├── 15_Thakur_2021_BEIR_Zero-shot_IR_Benchmark/   → paper_19
│   ├── 16_Baban_2025_Multi-Agent_Hybrid_Retrieval_KDD/   → paper_20
│   ├── 17_GIST_2025_LQ-RAG_Legal_Query_Feedback/   → paper_11
│   ├── 17_Louis_2022_BSARD_Statutory_Article_Retrieval/   → paper_12
├── 05_Local_SLMs_Edge_AI/   # Mô hình mở, tinh chỉnh hiệu quả (3 bài)
│   ├── 18_Dettmers_2023_QLoRA_Efficient_Finetuning/   → paper_21
│   ├── 19_Qwen_2024_Qwen2.5_Technical_Report/   → paper_22
│   ├── 20_Pareja_2024_Guide_SFT_Small_LLMs/   → paper_23
├── 06_Vietnamese_Legal_and_Public_Admin_AI/   # Pháp lý và hành chính tiếng Việt (4 bài)
│   ├── 21_ViGPTQA_2023_Vietnamese_Legal_QA/   → paper_01
│   ├── 23_Hien_2025_Integrating_IR_LLM_Vietnamese_Legal/   → paper_02
│   ├── 24_Truong_2024_Vietnamese_LLMs_Finetune_Evaluation/   → paper_03
│   ├── 25_Nguyen_2025_ViEn_CrossLingual_Legal_Retrieval/   → paper_04
├── 07_Production_Engineering_and_Serving/   # Hạ tầng phục vụ (4 bài)
│   ├── 26_Fu_2023_GPTCache_Semantic_Cache_LLM/   → paper_24
│   ├── 27_Ong_2024_RouteLLM_Learning_Route_LLMs/   → paper_25
│   ├── 28_Kwon_2023_vLLM_PagedAttention_Memory_Management/   → paper_26
│   ├── 29_Blecher_2023_Nougat_Neural_Optical_Understanding/   → paper_27
├── 08_Universal_Domain_and_Auto_Evaluation/   # Căn chỉnh, pipeline và đánh giá tự động (4 bài)
│   ├── 30_Bai_2022_Constitutional_AI_Harmlessness/   → paper_28
│   ├── 31_Khattab_2024_DSPy_Compiling_Declarative_Pipelines/   → paper_29
│   ├── 32_Qin_2024_ToolLLM_Mastering_APIs/   → paper_30
│   ├── 33_Es_2024_RAGAS_Automated_Evaluation_RAG/   → paper_31
└── _archived_preprints/   # 12 preprint đã thay thế (không dùng trong tổng quan)
```

---

## Bảng tra cứu 33 bài báo

| Thư mục | Tóm tắt | Bài báo | Nguồn công bố | Bình duyệt | Áp dụng vào dự án |
|---|:---:|---|---|:---:|---|
| `01` | [paper_05](../../02_related_work/paper_summaries/paper_05.md) | **Lukas et al. (PII leakage)** | IEEE S&P 2023 | Có | Cơ sở cho che PII và chạy on-prem trong tầng policy |
| `02` | [paper_06](../../02_related_work/paper_summaries/paper_06.md) | **Greshake et al. (Indirect PI)** | AISec '23 (ACM CCS) | Có | Cơ sở cho lớp chống prompt injection và cách ly ngữ cảnh truy hồi |
| `03` | [paper_32](../../02_related_work/paper_summaries/paper_32.md) | **Dahl et al. (Large Legal Fictions)** | Journal of Legal Analysis 2024 | Có | Bằng chứng không để LLM tự trả lời từ kiến thức tham số; cần clarify và verifier |
| `04` | [paper_33](../../02_related_work/paper_summaries/paper_33.md) | **NeMo Guardrails** | EMNLP 2023 Demo | Có | Tham chiếu gần nhất cho tầng policy của Sys_3_4 |
| `05` | [paper_07](../../02_related_work/paper_summaries/paper_07.md) | **LegalCheck** | ICAIL 2026 (short) | Có | Ví dụ triển khai thực tế ở chính quyền địa phương có người kiểm duyệt |
| `06` | [paper_08](../../02_related_work/paper_summaries/paper_08.md) | **LegalBench-RAG** | arXiv preprint (giữ lại) | Preprint | Gợi ý đánh giá truy hồi ở mức đoạn/trường |
| `07` | [paper_09](../../02_related_work/paper_summaries/paper_09.md) | **Magesh et al.** | JELS 2025 | Có | Bằng chứng RAG không loại bỏ ảo giác pháp lý → cần verifier |
| `08` | [paper_10](../../02_related_work/paper_summaries/paper_10.md) | **HyPA-RAG** | NAACL 2025 Industry | Có | Ý tưởng điều chỉnh top-k theo độ phức tạp câu hỏi |
| `09` | [paper_13](../../02_related_work/paper_summaries/paper_13.md) | **CoVe** | Findings ACL 2024 | Có | Ý tưởng kiểm chứng từng điểm sau sinh (verify_point) |
| `10` | [paper_14](../../02_related_work/paper_summaries/paper_14.md) | **Self-RAG** | ICLR 2024 (oral) | Có | Đối chứng giữa tự phê bình học được và verifier tất định |
| `11` | [paper_15](../../02_related_work/paper_summaries/paper_15.md) | **CRITIC** | ICLR 2024 | Có | Củng cố việc kiểm chứng phải dựa vào nguồn ngoài (CSDL thủ tục), không tự phán |
| `12` | [paper_16](../../02_related_work/paper_summaries/paper_16.md) | **RAGTruth** | ACL 2024 | Có | Mô hình đánh giá ảo giác cho Friendly Engine; data-to-text tương tự bảng lệ phí |
| `13` | [paper_17](../../02_related_work/paper_summaries/paper_17.md) | **FActScore** | EMNLP 2023 | Có | Thước đo phân rã sự kiện cho đánh giá câu trả lời thủ tục |
| `14` | [paper_18](../../02_related_work/paper_summaries/paper_18.md) | **CRAG** | arXiv preprint (giữ lại) | Preprint | Ý tưởng chấm độ tin cậy truy hồi trước khi sinh |
| `15` | [paper_19](../../02_related_work/paper_summaries/paper_19.md) | **BEIR** | NeurIPS 2021 D&B | Có | Cơ sở cho thiết kế truy hồi lai + reranker |
| `16` | [paper_20](../../02_related_work/paper_summaries/paper_20.md) | **Baban et al.** | GenAIRecP @ KDD 2025 | Có | Tham khảo cân bằng sparse/dense; RRF trong Sys_3_4 |
| `17` | [paper_11](../../02_related_work/paper_summaries/paper_11.md) | **LQ-RAG** | IEEE Access 2025 | Có | Vòng phản hồi viết lại truy vấn; cảnh báo chi phí độ trễ |
| `17` | [paper_12](../../02_related_work/paper_summaries/paper_12.md) | **BSARD** | ACL 2022 | Có | Cơ sở so sánh BM25 với dense và truy hồi lai cho văn bản quy phạm |
| `18` | [paper_21](../../02_related_work/paper_summaries/paper_21.md) | **QLoRA** | NeurIPS 2023 | Có | Khả thi tinh chỉnh Qwen2.5 trên GPU on-prem |
| `19` | [paper_22](../../02_related_work/paper_summaries/paper_22.md) | **Qwen2.5** | Technical report (giữ lại) | Preprint | Tài liệu chính thức của mô hình dùng trong Friendly Engine |
| `20` | [paper_23](../../02_related_work/paper_summaries/paper_23.md) | **Pareja et al.** | ICLR 2025 | Có | Hướng dẫn nếu nhóm tinh chỉnh Qwen2.5 cho thủ tục hành chính |
| `21` | [paper_01](../../02_related_work/paper_summaries/paper_01.md) | **ViGPTQA** | EMNLP 2023 Industry | Có | Khẳng định cần ngữ cảnh truy hồi khi hỏi đáp pháp luật tiếng Việt; định hướng chọn LLM hỗ trợ tốt tiếng Việt |
| `23` | [paper_02](../../02_related_work/paper_summaries/paper_02.md) | **Hien et al.** | IC3K/KMIS 2025 | Có | Công trình gần nhất về RAG pháp luật Việt Nam; bài học trích dẫn điều khoản |
| `24` | [paper_03](../../02_related_work/paper_summaries/paper_03.md) | **Truong et al. (URA-LLaMa)** | Findings NAACL 2024 | Có | Cơ sở chọn và đánh giá LLM cho tiếng Việt (Qwen2.5 trong Sys_3_4) |
| `25` | [paper_04](../../02_related_work/paper_summaries/paper_04.md) | **Nguyen et al.** | NAACL 2025 (short) | Có | Trực tiếp liên quan BGE-M3 trong Friendly Engine; tinh chỉnh embedding cho văn bản pháp luật |
| `26` | [paper_24](../../02_related_work/paper_summaries/paper_24.md) | **GPTCache** | NLP-OSS 2023 (EMNLP) | Có | Cảnh báo rủi ro trả nhầm thủ tục tương tự khi dùng cache |
| `27` | [paper_25](../../02_related_work/paper_summaries/paper_25.md) | **RouteLLM** | ICLR 2025 | Có | Cơ sở cho định tuyến Strict/Friendly Engine |
| `28` | [paper_26](../../02_related_work/paper_summaries/paper_26.md) | **vLLM** | SOSP 2023 | Có | Nền tảng phục vụ Qwen2.5 on-prem (vLLM) |
| `29` | [paper_27](../../02_related_work/paper_summaries/paper_27.md) | **Nougat** | ICLR 2024 | Có | Tham khảo trích xuất bảng biểu từ văn bản thủ tục |
| `30` | [paper_28](../../02_related_work/paper_summaries/paper_28.md) | **Constitutional AI** | arXiv preprint (giữ lại) | Preprint | Tinh thần nguyên tắc tường minh trong tầng policy |
| `31` | [paper_29](../../02_related_work/paper_summaries/paper_29.md) | **DSPy** | ICLR 2024 | Có | Tối ưu prompt/demo cho các bước Friendly Engine |
| `32` | [paper_30](../../02_related_work/paper_summaries/paper_30.md) | **ToolLLM** | ICLR 2024 | Có | Chọn thủ tục/công cụ đúng từ kho lớn; giới hạn hành động của LLM |
| `33` | [paper_31](../../02_related_work/paper_summaries/paper_31.md) | **RAGAS** | EACL 2024 Demo | Có | Thước đo cho Friendly Engine (RQ1, RQ3) |

Ghi chú: hai thư mục trong `04_Hybrid_Dual-System_Retrieval` cùng mang tiền tố `17_` (LQ-RAG và BSARD) do kế thừa đánh số cũ; nội dung không trùng nhau.

---
*Ghi chú: Toàn bộ thư mục này nằm trong .gitignore của repository để không theo dõi file PDF/Markdown nghiên cứu lên git.*
