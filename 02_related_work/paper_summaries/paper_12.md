# Paper 12 Summary

## Citation

Tên bài: A Statutory Article Retrieval Dataset in French (BSARD)
Tác giả: Antoine Louis, Gerasimos Spanakis (Law & Tech Lab, Maastricht University)
Năm: 2022
Nguồn: Proceedings of the 60th Annual Meeting of the Association for Computational Linguistics (ACL 2022), Volume 1: Long Papers, trang 6789–6803 — hội nghị hàng đầu, có bình duyệt
DOI/Link: https://aclanthology.org/2022.acl-long.468/ (DOI: 10.18653/v1/2022.acl-long.468)

## Problem

**Tóm tắt tổng quan.** Bài báo giới thiệu BSARD — bộ dữ liệu truy xuất điều luật bằng tiếng Pháp bản ngữ, gồm hơn 1.100 câu hỏi pháp lý của công dân Bỉ được chuyên gia gán nhãn với các điều luật liên quan trong kho hơn 22.600 điều luật. Tác giả đánh giá các phương pháp truy xuất từ vựng (TF-IDF, BM25) và dense (bi-encoder), ở chế độ zero-shot và có huấn luyện. Kết quả tốt nhất: bi-encoder two-tower huấn luyện trên BSARD đạt R@100 = 74,78%.

**Bối cảnh và động lực.** Phần lớn người dân thiếu hiểu biết pháp luật và kết quả công cụ tìm kiếm thường dẫn tới trang thương mại. Truy xuất điều luật khó vì: câu hỏi dùng ngôn ngữ đời thường còn điều luật dùng ngôn ngữ pháp lý; một câu hỏi có nhiều cách diễn giải; và luật thành văn có cấu trúc thứ bậc, một điều luật chỉ đủ nghĩa khi đặt trong ngữ cảnh chương/mục. Bộ dữ liệu duy nhất trước đó (COLIEE Statute Law) dùng câu hỏi thi luật sư Nhật dịch sang tiếng Anh, chỉ có câu hỏi đóng và ít điều luật hơn khoảng 30 lần — không phản ánh câu hỏi của người dân.

## Method

1. **Xây dựng kho điều luật:** thu thập 32 bộ luật công khai của Bỉ cùng tiêu đề các cấp (quyển, phần, chương, mục); dùng biểu thức chính quy làm sạch dấu vết sửa đổi; loại các điều đã bị bãi bỏ → 22.633 điều luật.
2. **Thu thập câu hỏi:** hợp tác với tổ chức Droits Quotidiens (khoảng 4.000 email/năm từ người dân). Sáu luật gia soạn “câu hỏi mẫu” ẩn danh bằng ngôn ngữ đời thường và dẫn điều luật liên quan → hơn 3.200 câu hỏi.
3. **Tinh chỉnh câu hỏi:** khoảng 1/3 bị trùng; ghép thêm thẻ ngữ cảnh (ví dụ “Tôi là người thuê nhà ở Brussels”) vào đầu câu hỏi để phân biệt.
4. **Lọc và ghép tham chiếu:** phân tích tham chiếu bằng regex, bỏ câu hỏi dẫn tới văn bản ngoài 32 bộ luật → 1.108 câu hỏi (886 train / 222 test).
5. **Mô hình so sánh:** TF-IDF, BM25 (k1 = 1,0; b = 0,6); bi-encoder zero-shot (word2vec, fastText, CamemBERT); bi-encoder siamese và two-tower dựa trên CamemBERT huấn luyện với in-batch negatives, chia điều luật dài thành đoạn 200 token chồng lấn 20.

```mermaid
flowchart LR
    C[32 bộ luật Bỉ] --> CL[Làm sạch, bỏ điều bãi bỏ] --> K[(22.633 điều luật + tiêu đề)]
    DQ[Email người dân → câu hỏi mẫu của luật gia] --> RF[Ghép thẻ ngữ cảnh, khử trùng]
    RF --> F[Regex ghép tham chiếu, lọc] --> DS[BSARD: 1.108 câu hỏi]
    DS --> M1[TF-IDF / BM25]
    DS --> M2[Bi-encoder zero-shot]
    DS --> M3[Bi-encoder huấn luyện: siamese / two-tower]
    K --> M1 & M2 & M3 --> EV[R@k, MAP@100, MRR@100, độ trễ]
```

## Dataset

BSARD: 1.108 câu hỏi (độ dài trung vị 14 từ) và 22.633 điều luật (độ dài trung vị 77 từ; 142 điều trên 1.000 từ). Chủ đề: gia đình 30,6%, nhà ở 27,4%, tiền bạc 16,0%, tư pháp 13,6%, người nước ngoài 5,7%, an sinh xã hội 3,5%, lao động 3,2%. 75% câu hỏi có dưới 5 điều luật liên quan, 7% có trên 20 (tối đa 109). Chỉ 1.612 điều luật được dẫn ít nhất một lần. Công bố với giấy phép phi thương mại.

## Evaluation

Recall@k (k = 100, 200, 500), MAP@100, MRR@100 và độ trễ truy vấn (ms). Tác giả cố ý không báo cáo Precision@k vì số điều luật liên quan khác nhau giữa các câu hỏi.

## Results

- **Không huấn luyện:** TF-IDF R@100 = 40,13%; BM25 51,33% (MRR@100 24,59%; độ trễ 1.342 ms); bi-encoder word2vec 49,41%; fastText 32,93%; CamemBERT zero-shot chỉ 4,21%.
- **Có huấn luyện:** siamese CamemBERT R@100 = 71,63%, MRR@100 = 43,52%; two-tower R@100 = 74,78%, R@500 = 83,39%, MAP@100 = 35,67%, độ trễ khoảng 26 ms.
- **Nhận xét của tác giả:** bi-encoder huấn luyện vượt trội rõ rệt; BM25 vẫn là baseline mạnh trong miền chuyên biệt; dùng trực tiếp embedding CamemBERT không tinh chỉnh cho kết quả rất kém.
- Không có ablation riêng ngoài so sánh siamese/two-tower và các loại embedding.

**Điểm mạnh.**

- Bộ dữ liệu bản ngữ, câu hỏi gần với cách người dân thực sự hỏi, nhãn do luật gia giàu kinh nghiệm gán; công bố dữ liệu và mã.
- Phân tích kỹ đặc điểm dữ liệu (độ dài, số điều liên quan, phân bố chủ đề).
- Baseline đa dạng, có báo cáo độ trễ — hữu ích cho lựa chọn kiến trúc thực tế.

## Limitations

**(a) Bài báo thừa nhận:** kho chỉ gồm 32 bộ luật, thiếu hàng nghìn nghị định, chỉ thị, pháp lệnh, nên một số câu hỏi mất bớt điều luật liên quan; không phải câu hỏi nào cũng trả lời được chỉ bằng luật thành văn (cần án lệ); rủi ro bị dùng cho mục đích thương mại hoặc lách luật.

**(b) Quan sát:** tập test nhỏ (222 câu hỏi); điều luật bị cắt ở 1.000 từ đầu khi huấn luyện; không thử cross-encoder rerank hay truy xuất lai; chưa khai thác cấu trúc thứ bậc (tác giả để làm hướng tương lai); chỉ truy xuất, không sinh câu trả lời.

## Relevance to our topic

BSARD có bối cảnh rất giống Sys_3_4: câu hỏi đời thường của người dân → văn bản quy phạm trong hệ thống luật thành văn (civil law), có cấu trúc thứ bậc. Kết quả “BM25 là baseline mạnh nhưng dense huấn luyện tốt hơn nhiều, còn embedding tổng quát chưa tinh chỉnh rất kém” củng cố kiến trúc kép của nhóm: truy hồi từ vựng có trọng số (IDF âm tiết) cho Strict Engine và embedding chuyên dụng cho Friendly Engine. Kỹ thuật ghép thẻ ngữ cảnh (vai trò, địa phương) vào câu hỏi tương ứng với hồ sơ người dùng (tỉnh, xã/phường) trong bộ nhớ của Sys_3_4.

**Kết luận.** BSARD là bộ dữ liệu truy xuất điều luật đầu tiên lấy câu hỏi của người dân làm trung tâm, cho thấy bi-encoder huấn luyện trong miền đạt R@100 khoảng 75% nhưng vẫn cách xa chuyên gia. Hướng tiếp theo tác giả đề xuất: mô hình xử lý điều luật dài và khai thác cấu trúc thứ bậc của pháp luật.

## Possible improvement

- Xây dựng bộ đánh giá kiểu BSARD cho thủ tục hành chính Việt Nam: câu hỏi người dân được chuẩn hóa, gán nhãn thủ tục/điều khoản liên quan, có thẻ ngữ cảnh địa phương.
- Báo cáo đồng thời R@k, MRR và độ trễ như bài để so sánh Strict và Friendly Engine.
- Khai thác cấu trúc thứ bậc (nhóm thủ tục, lĩnh vực) trong xếp hạng — hướng mà bài báo nêu nhưng chưa làm.
