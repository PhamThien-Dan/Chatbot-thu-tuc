# Tổng Hợp 33 Bài Báo Khoa Học Cho Dự Án Trợ Lý Thủ Tục Hành Chính (Sys_3_4)

> Danh mục tra cứu theo thư mục toàn văn. Mỗi mục gồm trích dẫn, trạng thái bình duyệt, link đã kiểm tra chéo, tệp PDF và liên kết tới bản tóm tắt học thuật chi tiết (7 phần: tóm tắt, bối cảnh, phương pháp, thực nghiệm, điểm mạnh, hạn chế, kết luận) viết lại từ toàn văn.

> Phiên bản cũ của tài liệu này (V10.5, 20 bài, có các preprint đã bị thay) được lưu tại `_archived_preprints/RESEARCH_PAPERS_V10.5_old.md`.

---

## Nhóm 01: Public Sector LLM Safety & Privacy — An toàn, quyền riêng tư và độ tin cậy LLM trong khu vực công

### 01. Analyzing Leakage of Personally Identifiable Information in Language Models
- **Tác giả:** Nils Lukas, Ahmed Salem, Robert Sim, Shruti Tople, Lukas Wutschitz, Santiago Zanella-Béguelin (University of Waterloo; Microsoft)
- **Năm:** 2023
- **Nguồn công bố:** 2023 IEEE Symposium on Security and Privacy (IEEE S&P 2023) — hội nghị bảo mật hàng đầu, có bình duyệt
- **DOI / Link:** [https://doi.org/10.1109/SP46215.2023.10179300](https://doi.org/10.1109/SP46215.2023.10179300)
- **Tệp toàn văn:** [`Analyzing Leakage of Personally Identifiable Information in Language Models.pdf`](01_Public_Sector_LLM_Safety_Privacy/01_Lukas_2023_PII_Leakage_Language_Models/Analyzing%20Leakage%20of%20Personally%20Identifiable%20Information%20in%20Language%20Models.pdf)
- **Tóm tắt chi tiết:** [`paper_05.md`](../../02_related_work/paper_summaries/paper_05.md)

**Tổng quan.** Bài báo nghiên cứu rủi ro mô hình ngôn ngữ (LM) làm rò rỉ thông tin định danh cá nhân (PII) từ dữ liệu tinh chỉnh. Tác giả đưa ra định nghĩa dạng trò chơi (game-based) cho ba loại tấn công hộp đen — trích xuất (extraction), tái dựng (reconstruction) và suy luận (inference) PII — đề xuất thuật toán tấn công mới và đo hiệu quả của hai biện pháp phòng vệ: che PII bằng NER (scrubbing) và huấn luyện riêng tư vi phân (DP). Kết quả chính: tấn công tái dựng mới tìm lại được tới 10× nhiều PII hơn tấn công trước; DP ở mức câu giảm mạnh rò rỉ nhưng vẫn lộ khoảng 3% chuỗi PII.

- **Phương pháp:** Tấn công trích xuất/tái tạo/suy luận PII; đánh giá scrubbing và DP
- **Dữ liệu:** ECHR, Enron, Yelp-Health; GPT-2
- **Thước đo:** Precision/Recall rò rỉ PII
- **Kết quả chính:** Không phòng vệ: precision 29,56%, recall 22,96%; DP ε=8 còn khoảng 3%; scrubbing dựa trên NER không hoàn hảo.
- **Hạn chế:** Kết quả là cận dưới; chỉ khớp nguyên văn.
- **Áp dụng cho Sys_3_4:** Cơ sở cho che PII và chạy on-prem trong tầng policy.

---

### 02. Not What You've Signed Up For: Compromising Real-World LLM-Integrated Applications with Indirect Prompt Injection
- **Tác giả:** Kai Greshake, Sahar Abdelnabi, Shailesh Mishra, Christoph Endres, Thorsten Holz, Mario Fritz (Saarland University; sequire technology; CISPA Helmholtz Center for Information Security)
- **Năm:** 2023
- **Nguồn công bố:** Proceedings of the 16th ACM Workshop on Artificial Intelligence and Security (AISec '23, đồng tổ chức với ACM CCS 2023) — workshop có bình duyệt của ACM
- **DOI / Link:** [https://doi.org/10.1145/3605764.3623985](https://doi.org/10.1145/3605764.3623985)
- **Tệp toàn văn:** [`Not what you've signed up for - Compromising Real-World LLM-Integrated Applications with Indirect Prompt Injection.pdf`](01_Public_Sector_LLM_Safety_Privacy/02_Greshake_2023_Indirect_Prompt_Injection/Not%20what%20you%27ve%20signed%20up%20for%20-%20Compromising%20Real-World%20LLM-Integrated%20Applications%20with%20Indirect%20Prompt%20Injection.pdf)
- **Tóm tắt chi tiết:** [`paper_06.md`](../../02_related_work/paper_summaries/paper_06.md)

**Tổng quan.** Bài báo giới thiệu khái niệm *chèn lệnh gián tiếp* (Indirect Prompt Injection – IPI): kẻ tấn công không cần tương tác trực tiếp với mô hình mà cài chỉ dẫn độc hại vào dữ liệu có khả năng được truy xuất khi suy luận (trang web, email, mã nguồn). Tác giả xây dựng phân loại mối đe dọa theo góc nhìn an ninh máy tính và minh họa tính khả thi trên Bing Chat (GPT-4), GitHub Copilot và các ứng dụng tổng hợp dùng GPT-4/text-davinci-003. Kết luận chính: với ứng dụng có truy xuất, “dữ liệu” và “lệnh” không còn tách bạch; xử lý dữ liệu truy xuất không tin cậy tương đương thực thi mã tùy ý.

- **Phương pháp:** Phân loại và minh họa tấn công chèn lệnh gián tiếp
- **Dữ liệu:** Không có bộ dữ liệu (proof-of-concept)
- **Thước đo:** Định tính (kịch bản tấn công)
- **Kết quả chính:** Chứng minh dữ liệu truy hồi có thể điều khiển LLM: đánh cắp dữ liệu, lừa đảo, lan truyền.
- **Hạn chế:** Chưa định lượng tỷ lệ thành công.
- **Áp dụng cho Sys_3_4:** Cơ sở cho lớp chống prompt injection và cách ly ngữ cảnh truy hồi.

---

### 03. Large Legal Fictions: Profiling Legal Hallucinations in Large Language Models
- **Tác giả:** Matthew Dahl (Yale), Varun Magesh, Mirac Suzgun, Daniel E. Ho (Stanford University, RegLab)
- **Năm:** 2024
- **Nguồn công bố:** Journal of Legal Analysis, Vol. 16, No. 1, tr. 64–93 (Oxford University Press; truy cập mở, xuất bản trực tuyến 26/06/2024) — tạp chí có bình duyệt (bài cảm ơn ba người phản biện ẩn danh)
- **DOI / Link:** [https://doi.org/10.1093/jla/laae003](https://doi.org/10.1093/jla/laae003)
- **Tệp toàn văn:** [`Large Legal Fictions - Profiling Legal Hallucinations in Large Language Models.pdf`](01_Public_Sector_LLM_Safety_Privacy/03_Dahl_2024_Large_Legal_Fictions/Large%20Legal%20Fictions%20-%20Profiling%20Legal%20Hallucinations%20in%20Large%20Language%20Models.pdf)
- **Tóm tắt chi tiết:** [`paper_32.md`](../../02_related_work/paper_summaries/paper_32.md)

**Tổng quan.** Bài báo là nghiên cứu thực nghiệm có hệ thống đầu tiên về “ảo giác pháp lý” (legal hallucination) của LLM công khai, dùng 14 tác vụ truy vấn kiến thức án lệ liên bang Hoa Kỳ ở ba cấp tòa (Tòa Tối cao – SCOTUS, Tòa Phúc thẩm – USCOA, Tòa Quận – USDC). Với câu hỏi trực tiếp, kiểm chứng được về một vụ án chọn ngẫu nhiên, các LLM ảo giác từ 58% (ChatGPT 4) đến 88% (Llama 2). Ngoài ra, LLM thường chấp nhận tiền đề pháp lý sai của người dùng và đánh giá kém mức độ chắc chắn của chính mình. Bài đề xuất một phân loại ảo giác pháp lý.

- **Phương pháp:** 14 tác vụ truy vấn án lệ; có/không tham chiếu; phản sự thật; ECE
- **Dữ liệu:** 5.000 vụ án mỗi cấp tòa liên bang Hoa Kỳ; >800.000 truy vấn
- **Thước đo:** Tỷ lệ ảo giác, ECE
- **Kết quả chính:** Ảo giác 58% (GPT-4) đến 88% (Llama 2); thường chấp nhận tiền đề sai; tự tin quá mức.
- **Hạn chế:** LLM không truy hồi; chỉ án lệ Hoa Kỳ.
- **Áp dụng cho Sys_3_4:** Bằng chứng không để LLM tự trả lời từ kiến thức tham số; cần clarify và verifier.

---

### 04. NeMo Guardrails: A Toolkit for Controllable and Safe LLM Applications with Programmable Rails
- **Tác giả:** Traian Rebedea, Razvan Dinu, Makesh Sreedhar, Christopher Parisien, Jonathan Cohen (NVIDIA)
- **Năm:** 2023
- **Nguồn công bố:** Proceedings of the 2023 Conference on Empirical Methods in Natural Language Processing: System Demonstrations (EMNLP 2023 Demo), tr. 431–445 — hội nghị có bình duyệt (track demo)
- **DOI / Link:** [https://aclanthology.org/2023.emnlp-demo.40/](https://aclanthology.org/2023.emnlp-demo.40/)
- **Tệp toàn văn:** [`NeMo Guardrails - A Toolkit for Controllable and Safe LLM Applications with Programmable Rails.pdf`](01_Public_Sector_LLM_Safety_Privacy/04_Rebedea_2023_NeMo_Guardrails/NeMo%20Guardrails%20-%20A%20Toolkit%20for%20Controllable%20and%20Safe%20LLM%20Applications%20with%20Programmable%20Rails.pdf)
- **Tóm tắt chi tiết:** [`paper_33.md`](../../02_related_work/paper_summaries/paper_33.md)

**Tổng quan.** Bài báo giới thiệu NeMo Guardrails, bộ công cụ mã nguồn mở (Apache 2.0) để thêm các “rail” (hàng rào) có thể lập trình vào ứng dụng hội thoại dùng LLM. Khác với rail “nhúng” vào mô hình qua căn chỉnh (alignment) khi huấn luyện, rail lập trình được định nghĩa lúc chạy bằng ngôn ngữ mô hình hóa Colang, độc lập với LLM nền và có thể diễn giải. Runtime đóng vai trò proxy giữa người dùng và LLM, giống một bộ quản lý hội thoại. Kết quả ban đầu cho thấy cách tiếp cận dùng được với nhiều nhà cung cấp LLM, kể cả mô hình mở cỡ nhỏ.

- **Phương pháp:** Rail lập trình bằng Colang; topical/execution rails (fact-check, hallucination, moderation)
- **Dữ liệu:** Banking (231 mẫu), Anthropic Red-Teaming/Helpful, MS MARCO, 20 câu tiền đề sai
- **Thước đo:** Accuracy, tỷ lệ chặn/cho qua
- **Kết quả chính:** Chặn gần 99% prompt có hại, 2% hữu ích; hallucination rail 65% → 95%.
- **Hạn chế:** Độ trễ/chi phí ~3 lần; rail dựa LLM không tất định.
- **Áp dụng cho Sys_3_4:** Tham chiếu gần nhất cho tầng policy của Sys_3_4.

---

## Nhóm 02: Legal & Regulatory RAG — RAG cho pháp lý và quy định

### 05. LegalCheck: Retrieval- and Context-Augmented Generation for Drafting Municipal Legal Advice Letters
- **Tác giả:** Virgill van der Meer (Municipality of Amsterdam), Julien Rossi (University of Amsterdam)
- **Năm:** 2026
- **Nguồn công bố:** Proceedings of the 21st International Conference on Artificial Intelligence and Law (ICAIL 2026), Singapore, 8–12/6/2026 — short paper, hội nghị có bình duyệt (ACM/IAAIL). Trang arXiv ghi “Accepted at ICAIL 2026 as Short Paper”.
- **DOI / Link:** [https://arxiv.org/abs/2605.12012](https://arxiv.org/abs/2605.12012)
- **Tệp toàn văn:** [`LegalCheck - Retrieval- and Context-Augmented Generation for Drafting Municipal Legal Advice Letters.pdf`](02_Legal_Regulatory_RAG/05_vanderMeer_2026_LegalCheck_Municipal_Advice/LegalCheck%20-%20Retrieval-%20and%20Context-Augmented%20Generation%20for%20Drafting%20Municipal%20Legal%20Advice%20Letters.pdf)
- **Tóm tắt chi tiết:** [`paper_07.md`](../../02_related_work/paper_summaries/paper_07.md)

**Tổng quan.** LegalCheck là hệ thống soạn thảo thư tư vấn pháp lý cho các đơn khiếu nại (bezwaar) của công dân tại phòng pháp chế thành phố Amsterdam. Hệ thống kết hợp RAG (truy xuất thư tư vấn cũ và văn bản quy phạm) với CAG (Context-Augmented Generation): đưa hồ sơ vụ việc, kết luận dự kiến do chuyên viên chọn và phản hồi của chuyên viên vào nhiều vòng sinh. Trong thí điểm 6 tháng, 81% nội dung bản nháp AI được giữ nguyên trong thư cuối cùng, và tổng thời gian xử lý giảm 50–70% với các vụ đơn giản.

- **Phương pháp:** Retrieval- và Context-Augmented Generation soạn thư tư vấn pháp lý
- **Dữ liệu:** ~23.500 thư 2022–2025, 4 lĩnh vực xử phạt
- **Thước đo:** Recall, Precision, F1, tỷ lệ giữ lại, thời gian
- **Kết quả chính:** F1 92%; tiết kiệm 92% thời gian soạn thảo; giảm 50–70% tổng thời gian.
- **Hạn chế:** Một cơ quan, nhóm người dùng nhỏ; phụ thuộc LLM bên thứ ba.
- **Áp dụng cho Sys_3_4:** Ví dụ triển khai thực tế ở chính quyền địa phương có người kiểm duyệt.

---

### 06. LegalBench-RAG: A Benchmark for Retrieval-Augmented Generation in the Legal Domain
- **Tác giả:** Nicholas Pipitone, Ghita Houir Alami (ZeroEntropy)
- **Năm:** 2024
- **Nguồn công bố:** arXiv preprint arXiv:2408.10343 [cs.AI] — **chưa có công bố tại hội nghị/tạp chí có bình duyệt** tại thời điểm kiểm tra. Nhóm giữ lại vì đây là benchmark truy xuất pháp lý mở, được cộng đồng RAG pháp lý sử dụng và trích dẫn rộng rãi; dữ liệu nguồn (CUAD, MAUD, ContractNLI, PrivacyQA, LegalBench) đều là các bộ dữ liệu đã công bố có bình duyệt.
- **DOI / Link:** [https://arxiv.org/abs/2408.10343](https://arxiv.org/abs/2408.10343)
- **Tệp toàn văn:** [`LegalBench-RAG - A Benchmark for Retrieval-Augmented Generation in the Legal Domain.pdf`](02_Legal_Regulatory_RAG/06_Pipitone_2024_LegalBench-RAG/LegalBench-RAG%20-%20A%20Benchmark%20for%20Retrieval-Augmented%20Generation%20in%20the%20Legal%20Domain.pdf)
- **Tóm tắt chi tiết:** [`paper_08.md`](../../02_related_work/paper_summaries/paper_08.md)

**Tổng quan.** Bài báo giới thiệu LegalBench-RAG, benchmark đầu tiên (theo tác giả) chuyên đánh giá bước *truy xuất* của pipeline RAG trong miền pháp lý. Benchmark yêu cầu truy xuất chính xác các đoạn văn ngắn (span ký tự) thay vì chỉ ID văn bản hay đoạn lớn. Bộ dữ liệu gồm khoảng 6.858–6.889 cặp truy vấn–đáp án (bài báo ghi cả hai con số) trên kho gần 80 triệu ký tự (714 văn bản), kèm phiên bản rút gọn LegalBench-RAG-mini (776 truy vấn). Thí nghiệm mẫu cho thấy chia đoạn RCTS không rerank cho kết quả tốt nhất, và reranker tổng quát của Cohere làm kết quả kém đi.

- **Phương pháp:** Benchmark truy hồi đoạn chính xác trong văn bản pháp lý
- **Dữ liệu:** ContractNLI, CUAD, MAUD, PrivacyQA (6.889 truy vấn)
- **Thước đo:** Precision@k, Recall@k
- **Kết quả chính:** Recall@64 tối đa 76,39% (chia cố định); rerank Cohere không cải thiện.
- **Hạn chế:** Chỉ hợp đồng/chính sách; có điểm không nhất quán nội bộ.
- **Áp dụng cho Sys_3_4:** Gợi ý đánh giá truy hồi ở mức đoạn/trường.

---

### 07. Hallucination-Free? Assessing the Reliability of Leading AI Legal Research Tools
- **Tác giả:** Varun Magesh, Faiz Surani, Matthew Dahl, Mirac Suzgun, Christopher D. Manning, Daniel E. Ho (Stanford University; Yale University)
- **Năm:** 2025
- **Nguồn công bố:** Journal of Empirical Legal Studies, Vol. 22, No. 2 (2025), trang 216–242 (Wiley/Cornell Law School) — tạp chí có bình duyệt, open access
- **DOI / Link:** [https://doi.org/10.1111/jels.12413](https://doi.org/10.1111/jels.12413)
- **Tệp toàn văn:** [`Hallucination-Free - Assessing the Reliability of Leading AI Legal Research Tools.pdf`](02_Legal_Regulatory_RAG/07_Magesh_2025_Hallucination-Free_Legal_AI_Tools/Hallucination-Free%20-%20Assessing%20the%20Reliability%20of%20Leading%20AI%20Legal%20Research%20Tools.pdf)
- **Tóm tắt chi tiết:** [`paper_09.md`](../../02_related_work/paper_summaries/paper_09.md)

**Tổng quan.** Bài báo là đánh giá thực nghiệm *có đăng ký trước* (preregistered) đầu tiên đối với các công cụ nghiên cứu pháp lý thương mại dựa trên RAG: Lexis+ AI (LexisNexis), Westlaw AI-Assisted Research và Ask Practical Law AI (Thomson Reuters), so với GPT-4. Tác giả đề xuất khung phân loại ảo giác theo hai chiều *tính đúng* (correctness) và *tính có căn cứ* (groundedness). Kết luận: các công cụ RAG thương mại ít ảo giác hơn GPT-4 nhưng vẫn ảo giác khoảng 17%–33% số câu hỏi, trái với tuyên bố “không ảo giác” của nhà cung cấp.

- **Phương pháp:** Đánh giá thực nghiệm công cụ RAG pháp lý thương mại
- **Dữ liệu:** 202 truy vấn pháp lý Hoa Kỳ đăng ký trước
- **Thước đo:** Tỷ lệ ảo giác, chính xác, đầy đủ
- **Kết quả chính:** Lexis+ AI và Practical Law ảo giác >1/6, Westlaw ~1/3 dù dùng RAG.
- **Hạn chế:** Ba sản phẩm, ảnh chụp tại một thời điểm, 202 câu.
- **Áp dụng cho Sys_3_4:** Bằng chứng RAG không loại bỏ ảo giác pháp lý → cần verifier.

---

### 08. HyPA-RAG: A Hybrid Parameter Adaptive Retrieval-Augmented Generation System for AI Legal and Policy Applications
- **Tác giả:** Rishi Kalra, Zekun Wu, Ayesha Gulley, Airlie Hilliard, Xin Guan, Adriano Koshiyama, Philip Treleaven (Holistic AI; University College London)
- **Năm:** 2025 (preprint đầu tiên 9/2024)
- **Nguồn công bố:** Proceedings of NAACL 2025 – Industry Track, ACL Anthology (2025.naacl-industry.79) — hội nghị có bình duyệt
- **DOI / Link:** [https://aclanthology.org/2025.naacl-industry.79/](https://aclanthology.org/2025.naacl-industry.79/)
- **Tệp toàn văn:** [`HyPA-RAG - A Hybrid Parameter Adaptive Retrieval-Augmented Generation System for AI Legal and Policy Applications.pdf`](02_Legal_Regulatory_RAG/08_Kalra_2024_HyPA-RAG_Legal_Policy/HyPA-RAG%20-%20A%20Hybrid%20Parameter%20Adaptive%20Retrieval-Augmented%20Generation%20System%20for%20AI%20Legal%20and%20Policy%20Applications.pdf)
- **Tóm tắt chi tiết:** [`paper_10.md`](../../02_related_work/paper_summaries/paper_10.md)

**Tổng quan.** Bài báo đề xuất HyPA-RAG cho hỏi đáp chính sách và pháp luật về AI, lấy Luật địa phương số 144 của New York (LL144, về công cụ ra quyết định tuyển dụng tự động) làm tình huống thử nghiệm. Hệ thống gồm: bộ phân loại độ phức tạp truy vấn để chọn tham số truy xuất thích ứng; truy xuất lai dense + sparse (BM25) + đồ thị tri thức (knowledge graph); và khung đánh giá với các loại câu hỏi riêng. Kết quả: cấu hình thích ứng tốt nhất đạt Faithfulness 0,9044 (so với 0,8480 của cấu hình top-k cố định tốt nhất); trong ablation, Correctness cao nhất đạt 0,8402.

- **Phương pháp:** Phân loại độ phức tạp → điều chỉnh tham số truy hồi lai + KG
- **Dữ liệu:** LL144 (15 trang), bộ câu hỏi sinh bằng GPT-3.5/Giskard
- **Thước đo:** Correctness, Faithfulness, Context Precision/Recall
- **Kết quả chính:** DistilBERT phân loại F1 0,90; LLM không truy hồi Correctness chỉ 0,20–0,46.
- **Hạn chế:** Một người chấm; một văn bản luật.
- **Áp dụng cho Sys_3_4:** Ý tưởng điều chỉnh top-k theo độ phức tạp câu hỏi.

---

## Nhóm 03: Fact-Checking & Verifiers — Kiểm chứng sự thật và đo ảo giác

### 09. Chain-of-Verification Reduces Hallucination in Large Language Models (CoVe)
- **Tác giả:** Shehzaad Dhuliawala, Mojtaba Komeili, Jing Xu, Roberta Raileanu, Xian Li, Asli Celikyilmaz, Jason Weston (Meta AI; ETH Zürich)
- **Năm:** 2024 (preprint 9/2023)
- **Nguồn công bố:** Findings of the Association for Computational Linguistics: ACL 2024 — hội nghị có bình duyệt, ACL Anthology
- **DOI / Link:** [https://aclanthology.org/2024.findings-acl.212/](https://aclanthology.org/2024.findings-acl.212/)
- **Tệp toàn văn:** [`Chain-of-Verification (CoVe) Reduces Hallucination in Large Language Models.pdf`](03_Fact-Checking_Verifiers/09_Dhuliawala_2023_Chain-of-Verification_CoVe/Chain-of-Verification%20%28CoVe%29%20Reduces%20Hallucination%20in%20Large%20Language%20Models.pdf)
- **Tóm tắt chi tiết:** [`paper_13.md`](../../02_related_work/paper_summaries/paper_13.md)

**Tổng quan.** Bài báo đề xuất Chain-of-Verification (CoVe): LLM (1) soạn câu trả lời nháp, (2) tự lập danh sách câu hỏi kiểm chứng, (3) trả lời các câu hỏi đó một cách độc lập để không bị câu trả lời nháp chi phối, và (4) sinh câu trả lời cuối đã kiểm chứng. Trên Llama 65B, CoVe tăng gấp đôi precision ở câu hỏi dạng danh sách Wikidata (0,17 → 0,36), tăng F1 trên MultiSpanQA từ 0,39 lên 0,48 và tăng FactScore khi sinh tiểu sử từ 55,9 lên 71,4.

- **Phương pháp:** Lập kế hoạch câu hỏi kiểm chứng → trả lời độc lập → sửa
- **Dữ liệu:** Wikidata, Wiki-Category, MultiSpanQA, tiểu sử
- **Thước đo:** Precision, F1, FActScore
- **Kết quả chính:** Precision Wikidata 0,17 → 0,36; FActScore 55,9 → 71,4.
- **Hạn chế:** Không loại bỏ hoàn toàn ảo giác; tăng chi phí sinh.
- **Áp dụng cho Sys_3_4:** Ý tưởng kiểm chứng từng điểm sau sinh (verify_point).

---

### 10. Self-RAG: Learning to Retrieve, Generate, and Critique through Self-Reflection
- **Tác giả:** Akari Asai, Zeqiu Wu, Yizhong Wang, Avirup Sil, Hannaneh Hajishirzi (University of Washington; Allen Institute for AI; IBM Research AI)
- **Năm:** 2024 (preprint 10/2023)
- **Nguồn công bố:** The Twelfth International Conference on Learning Representations (ICLR 2024), báo cáo oral — hội nghị hàng đầu, có bình duyệt (OpenReview)
- **DOI / Link:** [https://proceedings.iclr.cc/paper_files/paper/2024/hash/25f7be9694d7b32d5cc670927b8091e1-Abstract-Conference.html](https://proceedings.iclr.cc/paper_files/paper/2024/hash/25f7be9694d7b32d5cc670927b8091e1-Abstract-Conference.html)
- **Tệp toàn văn:** [`Self-RAG - Learning to Retrieve, Generate, and Critique through Self-Reflection.pdf`](03_Fact-Checking_Verifiers/10_Asai_2024_Self-RAG_Reflection_Critique/Self-RAG%20-%20Learning%20to%20Retrieve%2C%20Generate%2C%20and%20Critique%20through%20Self-Reflection.pdf)
- **Tóm tắt chi tiết:** [`paper_14.md`](../../02_related_work/paper_summaries/paper_14.md)

**Tổng quan.** Self-RAG huấn luyện một LLM duy nhất vừa sinh văn bản vừa sinh *token phản tư* (reflection tokens) để tự quyết định khi nào cần truy xuất, đánh giá đoạn văn truy xuất có liên quan không, câu trả lời có được đoạn văn hỗ trợ không, và câu trả lời có hữu ích không. Với Llama2 7B/13B, Self-RAG vượt các LLM và mô hình RAG mã nguồn mở trên sáu tác vụ, và vượt ChatGPT ở PubHealth, PopQA, sinh tiểu sử và ở độ chính xác trích dẫn (citation precision) trên ASQA.

- **Phương pháp:** Huấn luyện LLM sinh reflection token quyết định truy hồi và tự phê bình
- **Dữ liệu:** 150K mẫu huấn luyện; PopQA, PubHealth, ARC, TriviaQA, ASQA, tiểu sử
- **Thước đo:** Accuracy, FactScore, citation precision/recall
- **Kết quả chính:** Self-RAG 13B: PopQA 55,8; FactScore 80,2; citation precision 70,3.
- **Hạn chế:** Cần huấn luyện lại mô hình.
- **Áp dụng cho Sys_3_4:** Đối chứng giữa tự phê bình học được và verifier tất định.

---

### 11. CRITIC: Large Language Models Can Self-Correct with Tool-Interactive Critiquing
- **Tác giả:** Zhibin Gou, Zhihong Shao, Yeyun Gong, Yelong Shen, Yujiu Yang, Nan Duan, Weizhu Chen (Tsinghua University; Microsoft Research Asia; Microsoft Azure AI)
- **Năm:** 2024
- **Nguồn công bố:** The Twelfth International Conference on Learning Representations (ICLR 2024) — hội nghị hàng đầu, có bình duyệt (bản PDF ghi “Published as a conference paper at ICLR 2024”)
- **DOI / Link:** [https://proceedings.iclr.cc/paper_files/paper/2024/hash/fef126561bbf9d4467dbb8d27334b8fe-Abstract-Conference.html](https://proceedings.iclr.cc/paper_files/paper/2024/hash/fef126561bbf9d4467dbb8d27334b8fe-Abstract-Conference.html)
- **Tệp toàn văn:** [`CRITIC - Large Language Models Can Self-Correct with Tool-Interactive Critiquing.pdf`](03_Fact-Checking_Verifiers/11_Gou_2024_CRITIC_Self-Correct_Tool_Interactive/CRITIC%20-%20Large%20Language%20Models%20Can%20Self-Correct%20with%20Tool-Interactive%20Critiquing.pdf)
- **Tóm tắt chi tiết:** [`paper_15.md`](../../02_related_work/paper_summaries/paper_15.md)

**Tổng quan.** CRITIC là khung “kiểm chứng rồi sửa” cho LLM hộp đen: từ câu trả lời ban đầu, LLM tương tác với công cụ ngoài (Google Search, trình thông dịch Python, Perspective API) để sinh lời phê bình, sau đó sửa câu trả lời dựa trên phê bình và lặp lại đến khi đạt điều kiện dừng. Không cần huấn luyện thêm, chỉ cần prompt few-shot. Với ChatGPT, CRITIC tăng trung bình 7,7 F1 trên ba bộ QA, tăng 7,0% tuyệt đối trên ba bộ toán, và giảm 79,2% xác suất sinh nội dung độc hại. Phát hiện then chốt: LLM tự sửa mà không có phản hồi từ bên ngoài chỉ cải thiện ít, thậm chí làm kết quả xấu đi.

- **Phương pháp:** Vòng xác minh → phê bình → sửa dùng công cụ ngoài
- **Dữ liệu:** AmbigNQ, TriviaQA, HotpotQA, GSM8k, SVAMP, TabMWP, RealToxicityPrompts
- **Thước đo:** F1, độ chính xác, độc hại
- **Kết quả chính:** ChatGPT AmbigNQ F1 64,3 → 74,9; tự sửa không công cụ có thể làm kết quả xấu đi.
- **Hạn chế:** Độ trễ tăng theo số vòng.
- **Áp dụng cho Sys_3_4:** Củng cố việc kiểm chứng phải dựa vào nguồn ngoài (CSDL thủ tục), không tự phán.

---

### 12. RAGTruth: A Hallucination Corpus for Developing Trustworthy Retrieval-Augmented Language Models
- **Tác giả:** Cheng Niu, Yuanhao Wu, Juno Zhu, Siliang Xu, Kashun Shum, Randy Zhong, Juntong Song, Tong Zhang (NewsBreak; University of Illinois Urbana-Champaign)
- **Năm:** 2024
- **Nguồn công bố:** Proceedings of the 62nd Annual Meeting of the Association for Computational Linguistics (ACL 2024), Volume 1: Long Papers, trang 10862–10878 — hội nghị hàng đầu, có bình duyệt
- **DOI / Link:** [https://aclanthology.org/2024.acl-long.585/](https://aclanthology.org/2024.acl-long.585/)
- **Tệp toàn văn:** [`RAGTruth - A Hallucination Corpus for Developing Trustworthy Retrieval-Augmented Language Models.pdf`](03_Fact-Checking_Verifiers/12_Niu_2024_RAGTruth_Hallucination_Corpus/RAGTruth%20-%20A%20Hallucination%20Corpus%20for%20Developing%20Trustworthy%20Retrieval-Augmented%20Language%20Models.pdf)
- **Tóm tắt chi tiết:** [`paper_16.md`](../../02_related_work/paper_summaries/paper_16.md)

**Tổng quan.** Bài báo xây dựng RAGTruth — kho dữ liệu khoảng 18.000 câu trả lời sinh tự nhiên bởi 6 LLM trong bối cảnh RAG, được người chú thích ảo giác ở mức câu trả lời và mức từ/đoạn (span), phân thành 4 loại. Tác giả đo tần suất ảo giác của các LLM, đánh giá các phương pháp phát hiện ảo giác hiện có, và cho thấy Llama-2-13B tinh chỉnh trên RAGTruth đạt F1 phát hiện mức câu trả lời 78,7% — cao hơn prompt GPT-4-turbo (63,4%).

- **Phương pháp:** Kho chú thích ảo giác mức span cho đầu ra RAG
- **Dữ liệu:** 2.965 mẫu, 17.790 câu trả lời, 14.289 span
- **Thước đo:** Precision/Recall/F1 phát hiện ảo giác
- **Kết quả chính:** 43,1% câu trả lời có ảo giác; data-to-text cao nhất (68,6%).
- **Hạn chế:** Chỉ tiếng Anh; cần kiểm tra khả năng tổng quát.
- **Áp dụng cho Sys_3_4:** Mô hình đánh giá ảo giác cho Friendly Engine; data-to-text tương tự bảng lệ phí.

---

### 13. FActScore: Fine-grained Atomic Evaluation of Factual Precision in Long Form Text Generation
- **Tác giả:** Sewon Min, Kalpesh Krishna, Xinxi Lyu, Mike Lewis, Wen-tau Yih, Pang Wei Koh, Mohit Iyyer, Luke Zettlemoyer, Hannaneh Hajishirzi (University of Washington; UMass Amherst; Allen Institute for AI; Meta AI)
- **Năm:** 2023
- **Nguồn công bố:** Proceedings of the 2023 Conference on Empirical Methods in Natural Language Processing (EMNLP 2023), trang 12076–12100 — hội nghị hàng đầu, có bình duyệt
- **DOI / Link:** [https://aclanthology.org/2023.emnlp-main.741/](https://aclanthology.org/2023.emnlp-main.741/)
- **Tệp toàn văn:** [`FActScore - Fine-grained Atomic Evaluation of Factual Precision in Long Form Text Generation.pdf`](03_Fact-Checking_Verifiers/13_Min_2023_FActScore_Atomic_Factuality/FActScore%20-%20Fine-grained%20Atomic%20Evaluation%20of%20Factual%20Precision%20in%20Long%20Form%20Text%20Generation.pdf)
- **Tóm tắt chi tiết:** [`paper_17.md`](../../02_related_work/paper_summaries/paper_17.md)

**Tổng quan.** Bài báo đề xuất FActScore — thước đo độ chính xác sự kiện của văn bản dài, bằng cách tách văn bản thành các *sự kiện nguyên tử* (atomic facts) và tính tỷ lệ sự kiện được một nguồn tri thức đáng tin hỗ trợ. Đánh giá thủ công cho thấy InstructGPT, ChatGPT và PerplexityAI (có tìm kiếm) chỉ đạt lần lượt 42,5%, 58,3% và 71,5%. Tác giả xây dựng bộ ước lượng tự động có sai số dưới 2% so với người, và dùng nó đánh giá 6.500 văn bản của 13 đối tượng (chi phí tương đương 26.000 USD nếu thuê người chấm).

- **Phương pháp:** Tách sự kiện nguyên tử, kiểm tra với nguồn tri thức
- **Dữ liệu:** Tiểu sử 183 người (thủ công), 500 người (tự động)
- **Thước đo:** FActScore
- **Kết quả chính:** ChatGPT 58,3%; PerplexityAI 71,5%; chính xác giảm mạnh với thực thể hiếm.
- **Hạn chế:** Chỉ tiểu sử và Wikipedia.
- **Áp dụng cho Sys_3_4:** Thước đo phân rã sự kiện cho đánh giá câu trả lời thủ tục.

---

## Nhóm 04: Hybrid & Dual-System Retrieval — Truy hồi lai

### 14. Corrective Retrieval Augmented Generation (CRAG)
- **Tác giả:** Shi-Qi Yan, Jia-Chen Gu, Yun Zhu, Zhen-Hua Ling (University of Science and Technology of China; UCLA; Google DeepMind)
- **Năm:** 2024
- **Nguồn công bố:** arXiv preprint arXiv:2401.15884 (bản v3, 10/2024) — **chưa có công bố tại hội nghị/tạp chí có bình duyệt** tại thời điểm kiểm tra. Nhóm giữ lại vì đây là phương pháp nền tảng, được trích dẫn rộng rãi và triển khai phổ biến (ví dụ trong các framework RAG); mã nguồn công khai.
- **DOI / Link:** [https://arxiv.org/abs/2401.15884](https://arxiv.org/abs/2401.15884)
- **Tệp toàn văn:** [`Corrective Retrieval Augmented Generation (CRAG).pdf`](04_Hybrid_Dual-System_Retrieval/14_Yan_2024_CRAG_Corrective_RAG/Corrective%20Retrieval%20Augmented%20Generation%20%28CRAG%29.pdf)
- **Tóm tắt chi tiết:** [`paper_18.md`](../../02_related_work/paper_summaries/paper_18.md)

**Tổng quan.** CRAG giải quyết tình huống bộ truy xuất trả về tài liệu sai hoặc không liên quan. Một bộ đánh giá truy xuất nhẹ (T5-large, 0,77B tham số) chấm mức liên quan của từng tài liệu và kích hoạt một trong ba hành động: *Correct* (tinh lọc tri thức trong tài liệu), *Incorrect* (bỏ tài liệu, chuyển sang tìm kiếm web), *Ambiguous* (kết hợp cả hai). Tài liệu được tinh lọc theo cách “tách rồi ghép lại” (decompose-then-recompose). CRAG “cắm vào là chạy” với RAG và Self-RAG; ví dụ với SelfRAG-LLaMA2-7b, CRAG vượt RAG chuẩn 7,0 điểm trên PopQA và 36,6 điểm trên PubHealth.

- **Phương pháp:** Bộ đánh giá truy hồi → Correct/Incorrect/Ambiguous → tìm bổ sung
- **Dữ liệu:** PopQA, Biography, PubHealth, ARC
- **Thước đo:** Accuracy, FactScore
- **Kết quả chính:** RAG → CRAG: PopQA 52,8 → 59,8; PubHealth 39,0 → 75,6.
- **Hạn chế:** Cần tinh chỉnh bộ đánh giá ngoài; dùng web search.
- **Áp dụng cho Sys_3_4:** Ý tưởng chấm độ tin cậy truy hồi trước khi sinh.

---

### 15. BEIR: A Heterogeneous Benchmark for Zero-shot Evaluation of Information Retrieval Models
- **Tác giả:** Nandan Thakur, Nils Reimers, Andreas Rücklé, Abhishek Srivastava, Iryna Gurevych (UKP Lab, Technische Universität Darmstadt)
- **Năm:** 2021
- **Nguồn công bố:** Proceedings of the Neural Information Processing Systems Track on Datasets and Benchmarks 1 (NeurIPS 2021 Datasets and Benchmarks, Round 2) — có bình duyệt
- **DOI / Link:** [https://datasets-benchmarks-proceedings.neurips.cc/paper/2021/hash/65b9eea6e1cc6bb9f0cd2a47751a186f-Abstract-round2.html](https://datasets-benchmarks-proceedings.neurips.cc/paper/2021/hash/65b9eea6e1cc6bb9f0cd2a47751a186f-Abstract-round2.html)
- **Tệp toàn văn:** [`BEIR - A Heterogeneous Benchmark for Zero-shot Evaluation of Information Retrieval Models.pdf`](04_Hybrid_Dual-System_Retrieval/15_Thakur_2021_BEIR_Zero-shot_IR_Benchmark/BEIR%20-%20A%20Heterogeneous%20Benchmark%20for%20Zero-shot%20Evaluation%20of%20Information%20Retrieval%20Models.pdf)
- **Tóm tắt chi tiết:** [`paper_19.md`](../../02_related_work/paper_summaries/paper_19.md)

**Tổng quan.** BEIR là benchmark đánh giá khả năng tổng quát zero-shot (ngoài phân phối huấn luyện) của các mô hình truy xuất thông tin, gồm 18 bộ dữ liệu thuộc 9 loại tác vụ và nhiều miền. Bài đánh giá 10 hệ thống thuộc 5 kiến trúc: từ vựng, sparse, dense, late-interaction và rerank. Kết luận chính: BM25 là baseline rất bền vững; rerank (BM25 + cross-encoder) và late-interaction (ColBERT) tổng quát tốt nhất nhưng tốn kém; các mô hình dense hiệu quả về tính toán nhưng thường kém BM25 khi gặp miền mới.

- **Phương pháp:** So sánh lexical, sparse, dense, late-interaction, rerank
- **Dữ liệu:** 18 bộ dữ liệu tiếng Anh
- **Thước đo:** nDCG@10, Recall@100
- **Kết quả chính:** BM25 + cross-encoder +11% so với BM25; DPR −47,7%; BM25 là baseline mạnh.
- **Hạn chế:** Thiên lệch từ vựng trong chú thích; chỉ tiếng Anh.
- **Áp dụng cho Sys_3_4:** Cơ sở cho thiết kế truy hồi lai + reranker.

---

### 16. Optimizing Retrieval-Augmented Generation with Multi-Agent Hybrid Retrieval
- **Tác giả:** Hediyeh Baban, Sai Abhishek Pidaparthi, Samaksh Gulati, Aashutosh Nema (Dell Technologies)
- **Năm:** 2025
- **Nguồn công bố:** Workshop GenAIRecP 2025 (Generative AI for Recommendation and Personalization) tổ chức cùng ACM SIGKDD 2025 (KDD ’25, Toronto) — workshop có bình duyệt. Bản PDF dùng mẫu ACM KDD ’25; DOI in trên PDF (10.1145/3690624) là DOI chung của kỷ yếu mẫu, không phải DOI riêng của bài.
- **DOI / Link:** [https://genai-personalization.github.io/assets/papers/GenAIRecP2025/11_Baban.pdf](https://genai-personalization.github.io/assets/papers/GenAIRecP2025/11_Baban.pdf)
- **Tệp toàn văn:** [`Optimizing Retrieval-Augmented Generation with Multi-Agent Hybrid Retrieval.pdf`](04_Hybrid_Dual-System_Retrieval/16_Baban_2025_Multi-Agent_Hybrid_Retrieval_KDD/Optimizing%20Retrieval-Augmented%20Generation%20with%20Multi-Agent%20Hybrid%20Retrieval.pdf)
- **Tóm tắt chi tiết:** [`paper_20.md`](../../02_related_work/paper_summaries/paper_20.md)

**Tổng quan.** Bài báo đề xuất một quy trình RAG lai “agentic” trên LangGraph: hai nhánh truy xuất song song (BM25 và embedding Sentence-BERT), mỗi nhánh có tác tử truy xuất và tác tử lọc; một tác tử phân tích độ phức tạp gán trọng số cho hai nhánh; tác tử so sánh hợp nhất điểm theo trọng số; cuối cùng LLM sắp xếp lại theo ngữ cảnh. Trên kho 100.000 tài liệu và 500 truy vấn, hệ thống giảm thời gian truy xuất trung bình từ 43 giây xuống 11 giây (nhanh gấp 4 lần) và tăng Top-10 accuracy từ 85% lên 92% so với baseline lai tĩnh.

- **Phương pháp:** Tác tử điều phối BM25 + embedding, tự điều chỉnh trọng số
- **Dữ liệu:** 100.000 tài liệu, 500 truy vấn chú thích
- **Thước đo:** Top-10 accuracy, F1, độ trễ
- **Kết quả chính:** Top-10 85% → 92%; độ trễ 43 s → 11 s; trọng số BM25/embedding 30/70 tốt nhất.
- **Hạn chế:** Phụ thuộc embedding; chi phí điều phối.
- **Áp dụng cho Sys_3_4:** Tham khảo cân bằng sparse/dense; RRF trong Sys_3_4.

---

### 17. Legal Query RAG (LQ-RAG)
- **Tác giả:** Rahman S. M. Wahidur, Sumin Kim, Haeung Choi, David S. Bhatti, Heung-No Lee (Gwangju Institute of Science and Technology – GIST, Hàn Quốc)
- **Năm:** 2025
- **Nguồn công bố:** IEEE Access, Vol. 13 (2025), trang 36978–36994 — tạp chí có bình duyệt (nhận bài 14/1/2025, chấp nhận 31/1/2025, xuất bản 14/2/2025), open access CC BY 4.0
- **DOI / Link:** [https://doi.org/10.1109/ACCESS.2025.3542125](https://doi.org/10.1109/ACCESS.2025.3542125)
- **Tệp toàn văn:** [`Legal_Query_RAG_IEEE_Access_2025.pdf`](04_Hybrid_Dual-System_Retrieval/17_GIST_2025_LQ-RAG_Legal_Query_Feedback/Legal_Query_RAG_IEEE_Access_2025.pdf)
- **Tóm tắt chi tiết:** [`paper_11.md`](../../02_related_work/paper_summaries/paper_11.md)

**Tổng quan.** Bài báo đề xuất LQ-RAG, một khung RAG cho truy vấn pháp lý có vòng phản hồi đệ quy. Khung gồm bốn thành phần: mô hình embedding tinh chỉnh cho luật (GIST-Law-Embed), mô hình sinh tinh chỉnh lai (HFM – hợp nhất hai bản LoRA của LLaMA-3-8B), tác tử đánh giá dùng GPT-4, và tác tử viết lại prompt. Kết quả: embedding tinh chỉnh tăng Hit Rate 13% và MRR 15%; HFM cải thiện 24% so với LLM tổng quát; LQ-RAG đạt điểm liên quan trung bình 80%, cao hơn RAG thường 23% và RAG với mô hình tinh chỉnh (FTM) 14%.

- **Phương pháp:** RAG có tác tử đánh giá phản hồi + tinh chỉnh embedding/LLM
- **Dữ liệu:** 7 bộ truy hồi tự xây; benchmark tổng quát và pháp lý
- **Thước đo:** Hit Rate, MRR, điểm benchmark
- **Kết quả chính:** HFM cải thiện 9% (tổng quát) và 38% (pháp lý); kém ở một số bộ.
- **Hạn chế:** Phụ thuộc GPT-4 đánh giá; độ trễ cao.
- **Áp dụng cho Sys_3_4:** Vòng phản hồi viết lại truy vấn; cảnh báo chi phí độ trễ.

---

### 17. A Statutory Article Retrieval Dataset in French (BSARD)
- **Tác giả:** Antoine Louis, Gerasimos Spanakis (Law & Tech Lab, Maastricht University)
- **Năm:** 2022
- **Nguồn công bố:** Proceedings of the 60th Annual Meeting of the Association for Computational Linguistics (ACL 2022), Volume 1: Long Papers, trang 6789–6803 — hội nghị hàng đầu, có bình duyệt
- **DOI / Link:** [https://aclanthology.org/2022.acl-long.468/](https://aclanthology.org/2022.acl-long.468/)
- **Tệp toàn văn:** [`A Statutory Article Retrieval Dataset in French.pdf`](04_Hybrid_Dual-System_Retrieval/17_Louis_2022_BSARD_Statutory_Article_Retrieval/A%20Statutory%20Article%20Retrieval%20Dataset%20in%20French.pdf)
- **Tóm tắt chi tiết:** [`paper_12.md`](../../02_related_work/paper_summaries/paper_12.md)

**Tổng quan.** Bài báo giới thiệu BSARD — bộ dữ liệu truy xuất điều luật bằng tiếng Pháp bản ngữ, gồm hơn 1.100 câu hỏi pháp lý của công dân Bỉ được chuyên gia gán nhãn với các điều luật liên quan trong kho hơn 22.600 điều luật. Tác giả đánh giá các phương pháp truy xuất từ vựng (TF-IDF, BM25) và dense (bi-encoder), ở chế độ zero-shot và có huấn luyện. Kết quả tốt nhất: bi-encoder two-tower huấn luyện trên BSARD đạt R@100 = 74,78%.

- **Phương pháp:** Benchmark truy hồi điều luật; so sánh lexical và dense
- **Dữ liệu:** 1.108 câu hỏi, 22.633 điều luật
- **Thước đo:** R@k, MRR, MAP, độ trễ
- **Kết quả chính:** BM25 R@100 51,33%; bi-encoder huấn luyện 74,78%.
- **Hạn chế:** Kho chỉ 32 bộ luật; câu hỏi không phải lúc nào cũng trả lời được bằng luật.
- **Áp dụng cho Sys_3_4:** Cơ sở so sánh BM25 với dense và truy hồi lai cho văn bản quy phạm.

---

## Nhóm 05: Local SLMs & Edge AI — Mô hình mở, tinh chỉnh hiệu quả

### 18. QLoRA: Efficient Finetuning of Quantized LLMs
- **Tác giả:** Tim Dettmers, Artidoro Pagnoni, Ari Holtzman, Luke Zettlemoyer (University of Washington)
- **Năm:** 2023
- **Nguồn công bố:** Advances in Neural Information Processing Systems 36 (NeurIPS 2023) — hội nghị hàng đầu, có bình duyệt
- **DOI / Link:** [https://proceedings.neurips.cc/paper_files/paper/2023/hash/1feb87871436031bdc0f2beaa62a049b-Abstract-Conference.html](https://proceedings.neurips.cc/paper_files/paper/2023/hash/1feb87871436031bdc0f2beaa62a049b-Abstract-Conference.html)
- **Tệp toàn văn:** [`QLoRA - Efficient Finetuning of Quantized LLMs.pdf`](05_Local_SLMs_Edge_AI/18_Dettmers_2023_QLoRA_Efficient_Finetuning/QLoRA%20-%20Efficient%20Finetuning%20of%20Quantized%20LLMs.pdf)
- **Tóm tắt chi tiết:** [`paper_21.md`](../../02_related_work/paper_summaries/paper_21.md)

**Tổng quan.** QLoRA cho phép tinh chỉnh LLM 65B tham số trên một GPU 48GB mà vẫn giữ hiệu năng như tinh chỉnh đầy đủ 16-bit. Cơ chế: lan truyền gradient qua mô hình nền đã đóng băng và lượng tử 4-bit vào các adapter hạng thấp (LoRA). Ba đổi mới chính: kiểu dữ liệu 4-bit NormalFloat (NF4), lượng tử kép (Double Quantization) và Paged Optimizers. Họ mô hình Guanaco tinh chỉnh bằng QLoRA đạt 99,3% hiệu năng của ChatGPT trên Vicuna benchmark (theo GPT-4 chấm) sau 24 giờ trên một GPU.

- **Phương pháp:** NF4 + double quantization + paged optimizer + LoRA
- **Dữ liệu:** GLUE, Super-NaturalInstructions, MMLU, 8 bộ chỉ dẫn
- **Thước đo:** Perplexity, MMLU, Elo (Vicuna bench)
- **Kết quả chính:** NF4 + DQ tái tạo hiệu năng 16-bit (MMLU 53,1 vs 53,0); Guanaco 7B cần 5GB.
- **Hạn chế:** Chưa chứng minh ở 33B/65B so với full 16-bit.
- **Áp dụng cho Sys_3_4:** Khả thi tinh chỉnh Qwen2.5 trên GPU on-prem.

---

### 19. Qwen2.5 Technical Report
- **Tác giả:** Qwen Team (Alibaba Group) — An Yang, Baosong Yang, Beichen Zhang và cộng sự
- **Năm:** 2024 (bản v2: 1/2025)
- **Nguồn công bố:** Báo cáo kỹ thuật trên arXiv (arXiv:2412.15115) — **không phải bài hội nghị/tạp chí có bình duyệt**. Nhóm giữ lại vì đây là tài liệu chính thức, duy nhất mô tả mô hình nền Qwen2.5 mà hệ thống Sys_3_4 sử dụng; trọng số mô hình công khai và được cộng đồng kiểm chứng độc lập rộng rãi.
- **DOI / Link:** [https://arxiv.org/abs/2412.15115](https://arxiv.org/abs/2412.15115)
- **Tệp toàn văn:** [`Qwen2.5 Technical Report - Advancing Open Foundation Models across Scales.pdf`](05_Local_SLMs_Edge_AI/19_Qwen_2024_Qwen2.5_Technical_Report/Qwen2.5%20Technical%20Report%20-%20Advancing%20Open%20Foundation%20Models%20across%20Scales.pdf)
- **Tóm tắt chi tiết:** [`paper_22.md`](../../02_related_work/paper_summaries/paper_22.md)

**Tổng quan.** Báo cáo giới thiệu dòng LLM Qwen2.5 gồm bảy kích thước trọng số mở (0.5B, 1.5B, 3B, 7B, 14B, 32B, 72B — bản base và instruct, kèm bản lượng tử) và hai mô hình MoE độc quyền (Qwen2.5-Turbo, Qwen2.5-Plus). Cải tiến chính: dữ liệu tiền huấn luyện tăng từ 7 lên 18 nghìn tỷ token; hậu huấn luyện với hơn 1 triệu mẫu SFT cùng RL nhiều giai đoạn (DPO ngoại tuyến, GRPO trực tuyến). Theo báo cáo, Qwen2.5-72B-Instruct cạnh tranh với Llama-3-405B-Instruct dù nhỏ hơn khoảng 5 lần, và Qwen2.5-7B-Instruct vượt Gemma2-9B-IT và Llama3.1-8B-Instruct ở hầu hết tác vụ, trừ IFEval.

- **Phương pháp:** Tiền huấn luyện 18T token + hậu huấn luyện SFT/RL
- **Dữ liệu:** Benchmark mở + nội bộ (dữ liệu huấn luyện không công bố)
- **Thước đo:** MMLU, MATH, HumanEval, IFEval…
- **Kết quả chính:** Qwen2.5-7B-Instruct vượt Gemma2-9B và Llama3.1-8B (trừ IFEval).
- **Hạn chế:** Không bình duyệt; không đánh giá riêng tiếng Việt.
- **Áp dụng cho Sys_3_4:** Tài liệu chính thức của mô hình dùng trong Friendly Engine.

---

### 20. Unveiling the Secret Recipe: A Guide for Supervised Fine-Tuning Small LLMs
- **Tác giả:** Aldo Pareja, Nikhil Shivakumar Nayak, Hao Wang, Krishnateja Killamsetty, Shivchander Sudalairaj, Wenlong Zhao, Seungwook Han, Abhishek Bhandwaldar, Guangxuan Xu, Kai Xu, Ligong Han, Luke Inglis, Akash Srivastava (Red Hat AI Innovation; MIT-IBM Watson AI Lab; IBM Research; MIT; UMass Amherst)
- **Năm:** 2025 (preprint 12/2024)
- **Nguồn công bố:** The Thirteenth International Conference on Learning Representations (ICLR 2025), poster — hội nghị hàng đầu, có bình duyệt
- **DOI / Link:** [https://iclr.cc/virtual/2025/poster/28940](https://iclr.cc/virtual/2025/poster/28940)
- **Tệp toàn văn:** [`Unveiling the Secret Recipe - A Guide For Supervised Fine-Tuning Small LLMs.pdf`](05_Local_SLMs_Edge_AI/20_Pareja_2024_Guide_SFT_Small_LLMs/Unveiling%20the%20Secret%20Recipe%20-%20A%20Guide%20For%20Supervised%20Fine-Tuning%20Small%20LLMs.pdf)
- **Tóm tắt chi tiết:** [`paper_23.md`](../../02_related_work/paper_summaries/paper_23.md)

**Tổng quan.** Bài báo là nghiên cứu thực nghiệm có hệ thống về tinh chỉnh có giám sát (SFT) cho LLM cỡ nhỏ (3B–7B) trên dữ liệu chỉ dẫn về tri thức và kỹ năng, với bốn mô hình mở. Phát hiện chính: (i) batch size lớn kết hợp learning rate thấp cho kết quả tốt hơn trên MMLU, MTBench và Open LLM Leaderboard; (ii) động lực huấn luyện giai đoạn đầu (gradient norm thấp, loss cao) dự báo tốt hiệu năng cuối, cho phép dừng sớm các lần chạy kém; (iii) bỏ warmup và dùng learning rate hằng số không làm giảm hiệu năng; (iv) huấn luyện “gộp” (stacked) ngang hoặc hơn huấn luyện “theo pha” (phased) mà hiệu quả mẫu hơn.

- **Phương pháp:** Nghiên cứu thực nghiệm siêu tham số SFT cho LLM 3B–7B
- **Dữ liệu:** Dữ liệu tổng hợp theo taxonomy LAB
- **Thước đo:** MMLU, MTBench, GSM8K…
- **Kết quả chính:** Batch lớn + LR thấp tổng quát tốt hơn; stacked ≈ phased nhưng ít mẫu hơn.
- **Hạn chế:** Chỉ 3B–7B; không xét LoRA.
- **Áp dụng cho Sys_3_4:** Hướng dẫn nếu nhóm tinh chỉnh Qwen2.5 cho thủ tục hành chính.

---

## Nhóm 06: Vietnamese Legal & Public Admin AI — Pháp lý và hành chính tiếng Việt

### 21. ViGPTQA – State-of-the-Art LLMs for Vietnamese Question Answering: System Overview, Core Models Training, and Evaluations
- **Tác giả:** Minh-Thuan Nguyen, Khanh-Tung Tran, Vincent Nguyen, Xuan-Son Vu
- **Năm:** 2023
- **Nguồn công bố:** Proceedings of the 2023 Conference on Empirical Methods in Natural Language Processing: Industry Track (EMNLP 2023), trang 754–764 — hội nghị có bình duyệt (peer-reviewed), ACL Anthology
- **DOI / Link:** [https://aclanthology.org/2023.emnlp-industry.70/](https://aclanthology.org/2023.emnlp-industry.70/)
- **Tệp toàn văn:** [`ViGPTQA - State-of-the-Art LLMs for Vietnamese Question Answering.pdf`](06_Vietnamese_Legal_and_Public_Admin_AI/21_ViGPTQA_2023_Vietnamese_Legal_QA/ViGPTQA%20-%20State-of-the-Art%20LLMs%20for%20Vietnamese%20Question%20Answering.pdf)
- **Tóm tắt chi tiết:** [`paper_01.md`](../../02_related_work/paper_summaries/paper_01.md)

**Tổng quan.** Bài báo xây dựng ViGPTQA – một hệ thống hỏi đáp tiếng Việt chạy thực tế dựa trên LLM – và đề xuất ViGPT, một LLM đơn ngữ tiếng Việt được tinh chỉnh theo chỉ dẫn (instruction-tuned), cùng biến thể chuyên miền pháp luật ViGPT-Law. Nhóm tác giả công bố thêm các bộ dữ liệu đánh giá mới (ViLawsQA, ViTruthfulQA) và mã nguồn, trọng số mô hình. Kết quả chính: trên ViLawsQA, khi có ngữ cảnh truy xuất, ViGPT-Law-v2 đạt điểm người đánh giá 2,17–2,24/4 (2,52/4 với ngữ cảnh chuẩn), trong khi không có ngữ cảnh chỉ đạt tối đa 1,23/4.

- **Phương pháp:** Tinh chỉnh chỉ dẫn LLM tiếng Việt (ViGPT) + RAG
- **Dữ liệu:** ViLawsQA (1.020 bộ, 27 lĩnh vực luật), ViTruthfulQA, MRC tiếng Việt
- **Thước đo:** ROUGE-1, điểm người (0–4)
- **Kết quả chính:** ViGPT-Law-v2 + ngữ cảnh chuẩn đạt ROUGE-1 45,33, điểm người 2,52; không có ngữ cảnh thì câu trả lời phần lớn không hữu ích.
- **Hạn chế:** Dữ liệu chỉ dẫn tiếng Việt còn yếu; tính trung thực chưa tuyệt đối.
- **Áp dụng cho Sys_3_4:** Khẳng định cần ngữ cảnh truy hồi khi hỏi đáp pháp luật tiếng Việt; định hướng chọn LLM hỗ trợ tốt tiếng Việt.

---

### 23. Integrating Information Retrieval and Large Language Models for Vietnamese Legal Document Query Systems
- **Tác giả:** Pham Thi Xuan Hien, Duong Ngoc Thao Nhi, Pham Thi Ngoc Huyen
- **Năm:** 2025
- **Nguồn công bố:** Proceedings of the 17th International Joint Conference on Knowledge Discovery, Knowledge Engineering and Knowledge Management (IC3K 2025) – Vol. 2: KEOD và KMIS, trang 290–300, SCITEPRESS — hội nghị có bình duyệt
- **DOI / Link:** [https://doi.org/10.5220/0013751200004000](https://doi.org/10.5220/0013751200004000)
- **Tệp toàn văn:** [`Integrating Information Retrieval and Large Language Models for Vietnamese Legal Document Query Systems.pdf`](06_Vietnamese_Legal_and_Public_Admin_AI/23_Hien_2025_Integrating_IR_LLM_Vietnamese_Legal/Integrating%20Information%20Retrieval%20and%20Large%20Language%20Models%20for%20Vietnamese%20Legal%20Document%20Query%20Systems.pdf)
- **Tóm tắt chi tiết:** [`paper_02.md`](../../02_related_work/paper_summaries/paper_02.md)

**Tổng quan.** Bài báo đề xuất một hệ thống hỏi đáp văn bản pháp luật Việt Nam theo kiến trúc RAG, kết hợp truy xuất vector với LLM (GPT-4) để sinh câu trả lời có trích dẫn. Đóng góp chính là kiến trúc ba tầng xử lý và “tri-vector database” gồm ba chỉ mục riêng: đoạn văn bản luật, cặp hỏi-đáp và tóm tắt tri thức. Theo bài báo, hệ thống đạt Context Recall 0,847, độ chính xác trích dẫn pháp lý 94,2% và điểm hài lòng người dùng trung bình 4,23/5.

- **Phương pháp:** IR + LLM truy vấn văn bản pháp luật (RAG phân cấp)
- **Dữ liệu:** 45.000 văn bản, 12 lĩnh vực; 2.000 cặp hỏi–đáp do chuyên gia xác nhận
- **Thước đo:** Context Precision/Recall, MRR, ROUGE, Legal Citation Accuracy
- **Kết quả chính:** Citation Accuracy 94,2% (baseline tốt nhất 81,2%); độ chính xác giảm theo độ phức tạp câu hỏi.
- **Hạn chế:** Khó xử lý quy định mâu thuẫn; phụ thuộc kho đã xử lý.
- **Áp dụng cho Sys_3_4:** Công trình gần nhất về RAG pháp luật Việt Nam; bài học trích dẫn điều khoản.

---

### 24. Crossing Linguistic Horizons: Finetuning and Comprehensive Evaluation of Vietnamese Large Language Models
- **Tác giả:** Sang T. Truong, Duc Q. Nguyen, Toan Nguyen, Dong D. Le, Nhi N. Truong, Tho Quan, Sanmi Koyejo (Stanford University; Trường ĐH Bách khoa – ĐHQG TP.HCM)
- **Năm:** 2024
- **Nguồn công bố:** Findings of the Association for Computational Linguistics: NAACL 2024, trang 2849–2900 — hội nghị có bình duyệt, ACL Anthology
- **DOI / Link:** [https://aclanthology.org/2024.findings-naacl.182/](https://aclanthology.org/2024.findings-naacl.182/)
- **Tệp toàn văn:** [`Crossing Linguistic Horizons - Finetuning and Comprehensive Evaluation of Vietnamese Large Language Models.pdf`](06_Vietnamese_Legal_and_Public_Admin_AI/24_Truong_2024_Vietnamese_LLMs_Finetune_Evaluation/Crossing%20Linguistic%20Horizons%20-%20Finetuning%20and%20Comprehensive%20Evaluation%20of%20Vietnamese%20Large%20Language%20Models.pdf)
- **Tóm tắt chi tiết:** [`paper_03.md`](../../02_related_work/paper_summaries/paper_03.md)

**Tổng quan.** Bài báo tinh chỉnh và công bố năm LLM tiếng Việt mã nguồn mở (URA-LLaMa 7B/13B/70B dựa trên LLaMa-2, MixSUra dựa trên Mixtral 8×7B, GemSUra 7B dựa trên Gemma 7B), đồng thời xây dựng khung đánh giá toàn diện gồm 10 kịch bản và 31 chỉ số, áp dụng cho 14 LLM. Kết luận chính: tinh chỉnh giúp chuyển giao tri thức giữa các ngôn ngữ; mô hình lớn hơn có thể thiên kiến và kém hiệu chỉnh (calibration) hơn; chất lượng dữ liệu tinh chỉnh là yếu tố then chốt hơn số tham số.

- **Phương pháp:** Tinh chỉnh LLaMa-2 cho tiếng Việt, đánh giá toàn diện
- **Dữ liệu:** Nhiều tác vụ tiếng Việt (QA, tóm tắt, phân loại, suy luận…), 31 chỉ số, 14 LLM
- **Thước đo:** Độ chính xác theo tác vụ, hiệu chỉnh, thiên kiến, độc hại
- **Kết quả chính:** GPT-4 tốt nhất; mô hình tinh chỉnh vượt LLaMa-2 nền; kích thước không quyết định.
- **Hạn chế:** Nguy cơ nhiễm dữ liệu; dữ liệu tiếng Việt hạn chế.
- **Áp dụng cho Sys_3_4:** Cơ sở chọn và đánh giá LLM cho tiếng Việt (Qwen2.5 trong Sys_3_4).

---

### 25. Improving Vietnamese-English Cross-Lingual Retrieval for Legal and General Domains
- **Tác giả:** Toan Ngoc Nguyen, Nam Le Hai, Nguyen Doan Hieu, Dai An Nguyen, Linh Ngo Van, Thien Huu Nguyen, Sang Dinh (BKAI – ĐH Bách khoa Hà Nội; University of Oregon)
- **Năm:** 2025
- **Nguồn công bố:** Proceedings of NAACL 2025 (Volume 2: Short Papers), trang 142–153 — hội nghị có bình duyệt, ACL Anthology
- **DOI / Link:** [https://aclanthology.org/2025.naacl-short.12/](https://aclanthology.org/2025.naacl-short.12/)
- **Tệp toàn văn:** [`Improving Vietnamese-English Cross-Lingual Retrieval for Legal and General Domains.pdf`](06_Vietnamese_Legal_and_Public_Admin_AI/25_Nguyen_2025_ViEn_CrossLingual_Legal_Retrieval/Improving%20Vietnamese-English%20Cross-Lingual%20Retrieval%20for%20Legal%20and%20General%20Domains.pdf)
- **Tóm tắt chi tiết:** [`paper_04.md`](../../02_related_work/paper_summaries/paper_04.md)

**Tổng quan.** Bài báo xây dựng bộ dữ liệu truy xuất văn bản pháp luật tiếng Việt VNLawQC (từ Thư viện Pháp luật), bộ dữ liệu tổng hợp VNSynLawQC và bộ dữ liệu truy xuất xuyên ngôn ngữ Việt–Anh cho cả miền pháp luật và miền tổng quát. Tác giả đề xuất hàm mất mát phụ (auxiliary loss) và chiến lược huấn luyện đối xứng (symmetrical training) để tinh chỉnh BGE-M3. Kết quả: trên VNLawQC (truy vấn tiếng Anh, văn bản tiếng Việt), điểm trung bình tăng từ 42,99 (BGE-M3 gốc, dense) lên 69,75 (tinh chỉnh xuyên ngôn ngữ + đối xứng).

- **Phương pháp:** Tinh chỉnh BGE-M3 xuyên ngôn ngữ + dữ liệu tổng hợp
- **Dữ liệu:** VNLawQC, VNSynLawQC, ZaloLegal2021, ZaloWikipediaQA
- **Thước đo:** Recall/MRR (dense, dense+rerank)
- **Kết quả chính:** VNLawQC Việt–Anh 42,99 → 69,75; ZaloLegal2021 53,63 → 80,55.
- **Hạn chế:** Dữ liệu dựa vào dịch máy; chỉ một mô hình nền.
- **Áp dụng cho Sys_3_4:** Trực tiếp liên quan BGE-M3 trong Friendly Engine; tinh chỉnh embedding cho văn bản pháp luật.

---

## Nhóm 07: Production Engineering & Serving — Hạ tầng phục vụ

### 26. GPTCache: An Open-Source Semantic Cache for LLM Applications Enabling Faster Answers and Cost Savings
- **Tác giả:** Bang Fu, Di Feng (Zilliz Inc.)
- **Năm:** 2023
- **Nguồn công bố:** Proceedings of the 3rd Workshop for Natural Language Processing Open Source Software (NLP-OSS 2023, tổ chức cùng EMNLP 2023), trang 212–218 — workshop có bình duyệt, ACL Anthology
- **DOI / Link:** [https://aclanthology.org/2023.nlposs-1.24/](https://aclanthology.org/2023.nlposs-1.24/)
- **Tệp toàn văn:** [`GPTCache - An Open-Source Semantic Cache for LLM Applications.pdf`](07_Production_Engineering_and_Serving/26_Fu_2023_GPTCache_Semantic_Cache_LLM/GPTCache%20-%20An%20Open-Source%20Semantic%20Cache%20for%20LLM%20Applications.pdf)
- **Tóm tắt chi tiết:** [`paper_24.md`](../../02_related_work/paper_summaries/paper_24.md)

**Tổng quan.** GPTCache là bộ nhớ đệm ngữ nghĩa mã nguồn mở cho ứng dụng LLM: truy vấn được nhúng thành vector và so khớp với các câu hỏi đã lưu; nếu đủ tương đồng thì trả về câu trả lời đã lưu mà không gọi LLM. Theo tác giả, khi trúng cache, tốc độ phản hồi nhanh gấp 2–10 lần (khoảng 0,3 giây so với trung bình 3 giây của ChatGPT) và không tốn token.

- **Phương pháp:** Cache truy vấn bằng embedding + bộ đánh giá tương đồng
- **Dữ liệu:** Cặp câu tự tạo bằng ChatGPT (30.000 khóa)
- **Thước đo:** Tỷ lệ trúng, trúng đúng/sai, độ trễ
- **Kết quả chính:** 876/1.000 trúng (39 sai); độ trễ khi trúng ~0,2 s.
- **Hạn chế:** Trúng sai rõ rệt; phụ thuộc embedding.
- **Áp dụng cho Sys_3_4:** Cảnh báo rủi ro trả nhầm thủ tục tương tự khi dùng cache.

---

### 27. RouteLLM: Learning to Route LLMs with Preference Data
- **Tác giả:** Isaac Ong, Amjad Almahairi, Vincent Wu, Wei-Lin Chiang, Tianhao Wu, Joseph E. Gonzalez, M Waleed Kadous, Ion Stoica (UC Berkeley; Anyscale; Canva)
- **Năm:** 2025 (preprint 6/2024)
- **Nguồn công bố:** The Thirteenth International Conference on Learning Representations (ICLR 2025) — hội nghị hàng đầu, có bình duyệt (bản PDF ghi “Published as a conference paper at ICLR 2025”)
- **DOI / Link:** [https://proceedings.iclr.cc/paper_files/paper/2025/hash/5503a7c69d48a2f86fc00b3dc09de686-Abstract-Conference.html](https://proceedings.iclr.cc/paper_files/paper/2025/hash/5503a7c69d48a2f86fc00b3dc09de686-Abstract-Conference.html)
- **Tệp toàn văn:** [`RouteLLM - Learning to Route LLMs with Preference Data.pdf`](07_Production_Engineering_and_Serving/27_Ong_2024_RouteLLM_Learning_Route_LLMs/RouteLLM%20-%20Learning%20to%20Route%20LLMs%20with%20Preference%20Data.pdf)
- **Tóm tắt chi tiết:** [`paper_25.md`](../../02_related_work/paper_summaries/paper_25.md)

**Tổng quan.** RouteLLM là khung học bộ định tuyến (router) chọn giữa một LLM mạnh nhưng đắt (GPT-4) và một LLM yếu nhưng rẻ (Mixtral-8x7B) cho từng truy vấn, học từ dữ liệu sở thích của người dùng (Chatbot Arena) kèm tăng cường dữ liệu. Kết quả: giảm chi phí hơn 2 lần mà không giảm đáng kể chất lượng (tới 3,66 lần trên MT Bench ở mức 95% chất lượng GPT-4), và router tổng quát được sang cặp mô hình không có trong dữ liệu huấn luyện.

- **Phương pháp:** Router học từ dữ liệu ưu tiên chọn mô hình mạnh/yếu
- **Dữ liệu:** Chatbot Arena + tăng cường; MMLU, MT Bench, GSM8K
- **Thước đo:** APGR, CPT
- **Kết quả chính:** Matrix factorization APGR 0,802 trên MT Bench; cần dữ liệu trong miền.
- **Hạn chế:** Chỉ hai mô hình; phân phối thực tế có thể khác.
- **Áp dụng cho Sys_3_4:** Cơ sở cho định tuyến Strict/Friendly Engine.

---

### 28. Efficient Memory Management for Large Language Model Serving with PagedAttention (vLLM)
- **Tác giả:** Woosuk Kwon, Zhuohan Li, Siyuan Zhuang, Ying Sheng, Lianmin Zheng, Cody Hao Yu, Joseph E. Gonzalez, Hao Zhang, Ion Stoica (UC Berkeley; Stanford; UC San Diego)
- **Năm:** 2023
- **Nguồn công bố:** Proceedings of the 29th ACM Symposium on Operating Systems Principles (SOSP ’23), Koblenz, Đức — hội nghị hàng đầu về hệ điều hành/hệ thống, có bình duyệt
- **DOI / Link:** [https://doi.org/10.1145/3600006.3613165](https://doi.org/10.1145/3600006.3613165)
- **Tệp toàn văn:** [`Efficient Memory Management for Large Language Model Serving with PagedAttention.pdf`](07_Production_Engineering_and_Serving/28_Kwon_2023_vLLM_PagedAttention_Memory_Management/Efficient%20Memory%20Management%20for%20Large%20Language%20Model%20Serving%20with%20PagedAttention.pdf)
- **Tóm tắt chi tiết:** [`paper_26.md`](../../02_related_work/paper_summaries/paper_26.md)

**Tổng quan.** Bài báo đề xuất PagedAttention — thuật toán attention lấy cảm hứng từ bộ nhớ ảo và phân trang của hệ điều hành — và xây dựng vLLM, hệ thống phục vụ LLM đạt mức lãng phí bộ nhớ KV cache gần bằng 0 và chia sẻ KV cache linh hoạt trong và giữa các yêu cầu. Theo đánh giá, vLLM tăng thông lượng 2–4 lần so với FasterTransformer và Orca ở cùng mức độ trễ; lợi ích lớn hơn với chuỗi dài, mô hình lớn và thuật toán giải mã phức tạp.

- **Phương pháp:** PagedAttention quản lý KV cache theo trang
- **Dữ liệu:** Tải công việc từ ShareGPT, Alpaca
- **Thước đo:** Thông lượng ở cùng độ trễ
- **Kết quả chính:** Thông lượng cao hơn 2–4 lần so với hệ thống trước.
- **Hạn chế:** Kernel attention chậm hơn 20–26%.
- **Áp dụng cho Sys_3_4:** Nền tảng phục vụ Qwen2.5 on-prem (vLLM).

---

### 29. Nougat: Neural Optical Understanding for Academic Documents
- **Tác giả:** Lukas Blecher, Guillem Cucurull, Thomas Scialom, Robert Stojnic (Meta AI)
- **Năm:** 2024 (preprint 8/2023)
- **Nguồn công bố:** The Twelfth International Conference on Learning Representations (ICLR 2024) — hội nghị hàng đầu, có bình duyệt (OpenReview)
- **DOI / Link:** [https://proceedings.iclr.cc/paper_files/paper/2024/hash/a39a9aceda771cded859ae7560530e09-Abstract-Conference.html](https://proceedings.iclr.cc/paper_files/paper/2024/hash/a39a9aceda771cded859ae7560530e09-Abstract-Conference.html)
- **Tệp toàn văn:** [`Nougat - Neural Optical Understanding for Academic Documents.pdf`](07_Production_Engineering_and_Serving/29_Blecher_2023_Nougat_Neural_Optical_Understanding/Nougat%20-%20Neural%20Optical%20Understanding%20for%20Academic%20Documents.pdf)
- **Tóm tắt chi tiết:** [`paper_27.md`](../../02_related_work/paper_summaries/paper_27.md)

**Tổng quan.** Nougat là mô hình Transformer mã hóa–giải mã chuyển ảnh trang tài liệu khoa học thành văn bản markup (Markdown có LaTeX cho công thức và bảng) mà không cần bộ OCR bên ngoài hay văn bản nhúng trong PDF. Trên tập test arXiv, Nougat base (350M tham số) đạt edit distance 0,071, BLEU 89,1, F1 93,1 — vượt xa văn bản nhúng trong PDF (F1 79,2) và GROBID + LaTeX-OCR (F1 73,0).

- **Phương pháp:** Transformer ảnh → markup (Swin + mBART)
- **Dữ liệu:** arXiv, PubMed Central, Industry Documents
- **Thước đo:** Edit distance, BLEU, METEOR, F1
- **Kết quả chính:** F1 93,1; bảng F1 78,0; lặp ở 1,5% trang.
- **Hạn chế:** Chủ yếu tiếng Anh, tài liệu khoa học.
- **Áp dụng cho Sys_3_4:** Tham khảo trích xuất bảng biểu từ văn bản thủ tục.

---

## Nhóm 08: Universal Domain & Auto Evaluation — Căn chỉnh, pipeline và đánh giá tự động

### 30. Constitutional AI: Harmlessness from AI Feedback
- **Tác giả:** Yuntao Bai, Saurav Kadavath, Sandipan Kundu, Amanda Askell, … , Jared Kaplan (Anthropic; 51 tác giả)
- **Năm:** 2022
- **Nguồn công bố:** arXiv preprint arXiv:2212.08073 (báo cáo nghiên cứu của Anthropic) — **không phải bài hội nghị/tạp chí có bình duyệt**. Nhóm giữ lại vì đây là công trình gốc của phương pháp “Constitutional AI / RLAIF”, được trích dẫn và áp dụng rất rộng rãi trong nghiên cứu căn chỉnh (alignment) LLM.
- **DOI / Link:** [https://arxiv.org/abs/2212.08073](https://arxiv.org/abs/2212.08073)
- **Tệp toàn văn:** [`Constitutional AI - Harmlessness from AI Feedback.pdf`](08_Universal_Domain_and_Auto_Evaluation/30_Bai_2022_Constitutional_AI_Harmlessness/Constitutional%20AI%20-%20Harmlessness%20from%20AI%20Feedback.pdf)
- **Tóm tắt chi tiết:** [`paper_28.md`](../../02_related_work/paper_summaries/paper_28.md)

**Tổng quan.** Bài báo đề xuất Constitutional AI (CAI): huấn luyện trợ lý AI vô hại mà **không dùng nhãn của con người về tính có hại**; giám sát của con người chỉ được cung cấp qua một danh sách ngắn các nguyên tắc bằng ngôn ngữ tự nhiên (“hiến pháp”, 16 nguyên tắc). Quy trình gồm giai đoạn học có giám sát (tự phê bình → tự sửa → tinh chỉnh) và giai đoạn học tăng cường từ phản hồi AI (RLAIF). Kết quả: mô hình RL-CAI vô hại hơn nhưng ít né tránh hơn — giải thích lý do khi từ chối thay vì chỉ từ chối — và được người đánh giá ưa chuộng hơn so với mô hình huấn luyện bằng nhãn có hại của con người.

- **Phương pháp:** SL tự phê bình/sửa + RLAIF theo bộ nguyên tắc
- **Dữ liệu:** 182.831 prompt red team; 135.296 prompt hữu ích
- **Thước đo:** Elo hữu ích/vô hại, độ chính xác đánh giá HHH
- **Kết quả chính:** RL-CAI vô hại hơn ở cùng mức hữu ích so với HH-RLHF.
- **Hạn chế:** Vẫn cần nhãn người cho hữu ích; Goodhart khi quá huấn luyện.
- **Áp dụng cho Sys_3_4:** Tinh thần nguyên tắc tường minh trong tầng policy.

---

### 31. DSPy: Compiling Declarative Language Model Calls into Self-Improving Pipelines
- **Tác giả:** Omar Khattab, Arnav Singhvi, Paridhi Maheshwari, Zhiyuan Zhang, Keshav Santhanam, Sri Vardhamanan, Saiful Haq, Ashutosh Sharma, Thomas T. Joshi, Hanna Moazam, Heather Miller, Matei Zaharia, Christopher Potts
- **Năm:** 2024 (bản arXiv v1: 10/2023)
- **Nguồn công bố:** The Twelfth International Conference on Learning Representations (ICLR 2024) — hội nghị có bình duyệt (Spotlight). Lưu ý: tên chính thức trong kỷ yếu ICLR là “DSPy: Compiling Declarative Language Model Calls into **State-of-the-Art** Pipelines”; bản arXiv/PDF tham chiếu dùng tên “…Self-Improving Pipelines”.
- **DOI / Link:** [https://proceedings.iclr.cc/paper_files/paper/2024/hash/f1cf02ce09757f57c3b93c0db83181e0-Abstract-Conference.html](https://proceedings.iclr.cc/paper_files/paper/2024/hash/f1cf02ce09757f57c3b93c0db83181e0-Abstract-Conference.html)
- **Tệp toàn văn:** [`DSPy - Compiling Declarative Language Model Calls into Self-Improving Pipelines.pdf`](08_Universal_Domain_and_Auto_Evaluation/31_Khattab_2024_DSPy_Compiling_Declarative_Pipelines/DSPy%20-%20Compiling%20Declarative%20Language%20Model%20Calls%20into%20Self-Improving%20Pipelines.pdf)
- **Tóm tắt chi tiết:** [`paper_29.md`](../../02_related_work/paper_summaries/paper_29.md)

**Tổng quan.** Bài báo giới thiệu DSPy, một mô hình lập trình coi pipeline LLM là “đồ thị biến đổi văn bản” (text transformation graph): các lời gọi LM được khai báo bằng *signature* (mô tả vào/ra bằng ngôn ngữ tự nhiên), cài đặt bằng *module* có tham số, và được *teleprompter* (bộ tối ưu) tự động biên dịch thành prompt/demo hoặc trọng số tinh chỉnh dựa trên một metric. Trên GSM8K và HotPotQA, chương trình DSPy vài dòng, sau vài phút biên dịch, giúp GPT-3.5 và llama2-13b-chat vượt few-shot chuẩn lần lượt hơn 25% và 65%, và vượt pipeline dùng demo chuyên gia lần lượt 5–46% và 16–40%.

- **Phương pháp:** Signature – module – teleprompter tự tối ưu demo/prompt
- **Dữ liệu:** GSM8K, HotPotQA (200 train/300 dev)
- **Thước đo:** Accuracy, EM, passage accuracy
- **Kết quả chính:** GPT-3.5 vượt few-shot >25%, llama2-13b >65%; GSM8K CoT ensemble 88,3% dev.
- **Hạn chế:** Chỉ hai case study; phụ thuộc chất lượng metric.
- **Áp dụng cho Sys_3_4:** Tối ưu prompt/demo cho các bước Friendly Engine.

---

### 32. ToolLLM: Facilitating Large Language Models to Master 16000+ Real-world APIs
- **Tác giả:** Yujia Qin, Shihao Liang, Yining Ye, Kunlun Zhu, Lan Yan, Yaxi Lu, Yankai Lin, Xin Cong, Xiangru Tang, Bill Qian, Sihan Zhao, Lauren Hong, Runchu Tian, Ruobing Xie, Jie Zhou, Mark Gerstein, Dahai Li, Zhiyuan Liu, Maosong Sun (Tsinghua University, Yale, Renmin University, Tencent WeChat AI…)
- **Năm:** 2024 (bản arXiv v2: 10/2023)
- **Nguồn công bố:** The Twelfth International Conference on Learning Representations (ICLR 2024) — hội nghị có bình duyệt
- **DOI / Link:** [https://proceedings.iclr.cc/paper_files/paper/2024/hash/28e50ee5b72e90b50e7196fde8ea260e-Abstract-Conference.html](https://proceedings.iclr.cc/paper_files/paper/2024/hash/28e50ee5b72e90b50e7196fde8ea260e-Abstract-Conference.html)
- **Tệp toàn văn:** [`ToolLLM - Facilitating Large Language Models to Master 16000+ Real-world APIs.pdf`](08_Universal_Domain_and_Auto_Evaluation/32_Qin_2024_ToolLLM_Mastering_APIs/ToolLLM%20-%20Facilitating%20Large%20Language%20Models%20to%20Master%2016000%2B%20Real-world%20APIs.pdf)
- **Tóm tắt chi tiết:** [`paper_30.md`](../../02_related_work/paper_summaries/paper_30.md)

**Tổng quan.** Bài báo đề xuất ToolLLM, một khung tổng quát cho năng lực dùng công cụ (API) của LLM mã nguồn mở, gồm: bộ dữ liệu tinh chỉnh chỉ dẫn ToolBench (16.464 REST API thật từ RapidAPI, 49 danh mục), thuật toán suy luận cây quyết định tìm kiếm theo chiều sâu (DFSDT), bộ đánh giá tự động ToolEval, bộ truy hồi API dạng dense, và mô hình ToolLLaMA (LLaMA-2 7B tinh chỉnh). ToolLLaMA đạt hiệu năng gần với ChatGPT (mô hình “thầy”) và tổng quát hóa sang API chưa thấy cũng như sang bộ dữ liệu ngoài phân phối APIBench.

- **Phương pháp:** ToolBench + DFSDT + API retriever + ToolLLaMA
- **Dữ liệu:** 16.464 API, 126.486 cặp chỉ dẫn–lời giải; APIBench
- **Thước đo:** Pass Rate, Win Rate (ToolEval), NDCG
- **Kết quả chính:** ToolLLaMA-DFSDT pass 66,7 (ChatGPT-DFSDT 64,8); retriever NDCG@5 84,9 vs BM25 17,0.
- **Hạn chế:** Đánh giá dựa ChatGPT; chi phí DFSDT.
- **Áp dụng cho Sys_3_4:** Chọn thủ tục/công cụ đúng từ kho lớn; giới hạn hành động của LLM.

---

### 33. RAGAS: Automated Evaluation of Retrieval Augmented Generation
- **Tác giả:** Shahul Es, Jithin James (Exploding Gradients), Luis Espinosa-Anke, Steven Schockaert (CardiffNLP, Cardiff University; AMPLYFI)
- **Năm:** 2024
- **Nguồn công bố:** Proceedings of the 18th Conference of the European Chapter of the Association for Computational Linguistics (EACL 2024): System Demonstrations, tr. 150–158 — hội nghị có bình duyệt (track demo)
- **DOI / Link:** [https://aclanthology.org/2024.eacl-demo.16/](https://aclanthology.org/2024.eacl-demo.16/)
- **Tệp toàn văn:** [`RAGAS - Automated Evaluation of Retrieval Augmented Generation.pdf`](08_Universal_Domain_and_Auto_Evaluation/33_Es_2024_RAGAS_Automated_Evaluation_RAG/RAGAS%20-%20Automated%20Evaluation%20of%20Retrieval%20Augmented%20Generation.pdf)
- **Tóm tắt chi tiết:** [`paper_31.md`](../../02_related_work/paper_summaries/paper_31.md)

**Tổng quan.** Bài báo giới thiệu RAGAS (Retrieval Augmented Generation Assessment), một khung đánh giá **không cần tham chiếu** (reference-free) cho pipeline RAG, gồm ba thước đo tính bằng cách prompt LLM: Faithfulness (câu trả lời có dựa trên ngữ cảnh truy hồi), Answer Relevance (câu trả lời có đáp đúng câu hỏi) và Context Relevance (ngữ cảnh có tập trung, ít thông tin thừa). Tác giả xây bộ dữ liệu WikiEval có nhãn người để kiểm tra mức đồng thuận, và cho thấy RAGAS khớp với đánh giá của người tốt hơn hai baseline dùng ChatGPT chấm trực tiếp.

- **Phương pháp:** Faithfulness, Answer Relevance, Context Relevance không cần tham chiếu
- **Dữ liệu:** WikiEval (50 trang Wikipedia)
- **Thước đo:** Độ chính xác so với người (so sánh cặp)
- **Kết quả chính:** Faithfulness 0,95; Answer Rel. 0,78; Context Rel. 0,70 (vượt GPT Score/Ranking).
- **Hạn chế:** WikiEval nhỏ; phụ thuộc LLM đánh giá.
- **Áp dụng cho Sys_3_4:** Thước đo cho Friendly Engine (RQ1, RQ3).

---
