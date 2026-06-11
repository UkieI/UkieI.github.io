---
layout: post
title: "Giai đoạn OCR trong bài toán số hoá văn bản pháp lý"
date: 2026-06-11
categories: [AI, OCR]
tags: [PaddleOCR, OCR, legal-documents, document-ai]
excerpt: "Ghi chú ngắn về giai đoạn nghiên cứu OCR bằng PaddleOCR trong bài toán dữ liệu hoá văn bản quyết định, nghị định trong cơ sở giáo dục."
lang: vi
ref: paddleocr-ocr-stage
permalink: /vi/blog/giai-doan-ocr-paddleocr/
---

Trong đề án tốt nghiệp, mình đang xây dựng hướng tiếp cận cho bài toán **dữ liệu hoá và tìm kiếm căn cứ pháp lý** trong các văn bản quyết định, nghị định thuộc môi trường cơ sở giáo dục. Trước khi đi đến các phần NLP như trích xuất metadata, nhận diện thực thể hay đề xuất căn cứ liên quan, giai đoạn đầu tiên cần làm chắc là **OCR**.

Ở bước này, mục tiêu không phải là xây dựng ngay một hệ thống hoàn chỉnh, mà là hiểu rõ cách biến ảnh hoặc bản scan văn bản thành dữ liệu text có thể xử lý tiếp. Với các văn bản hành chính, OCR không chỉ đơn giản là nhận diện chữ. Mô hình còn phải xử lý bố cục trang, tiêu đề, số hiệu văn bản, ngày ban hành, phần căn cứ, nội dung điều khoản và chữ ký/con dấu nếu có.

Mình chọn nghiên cứu **PaddleOCR** vì thư viện này đã cung cấp sẵn pipeline tương đối đầy đủ cho document OCR, bao gồm phát hiện vùng chữ, nhận dạng ký tự và hỗ trợ nhiều dạng ảnh đầu vào. Trong giai đoạn hiện tại, công việc chính là lên kế hoạch triển khai, chuẩn bị dữ liệu ảnh, label thử một số mẫu và tìm hiểu kỹ hơn cách PaddleOCR hoạt động trên văn bản tiếng Việt.

Một pipeline OCR dự kiến sẽ gồm các bước chính:

1. Thu thập ảnh hoặc file scan từ văn bản quyết định, nghị định.
2. Tiền xử lý ảnh như xoay thẳng trang, giảm nhiễu và chuẩn hoá độ tương phản.
3. Dùng PaddleOCR để phát hiện vùng chữ và nhận dạng nội dung.
4. Kiểm tra lỗi OCR trên các trường quan trọng như số văn bản, ngày tháng, tên cơ quan và phần căn cứ.
5. Chuẩn hoá output thành text có cấu trúc để phục vụ các bước NLP phía sau.

Điểm khó của giai đoạn này nằm ở chất lượng tài liệu đầu vào. Một số văn bản có thể bị mờ, lệch trang, scan thiếu nét hoặc có bố cục không đồng nhất. Nếu OCR sai ở các phần quan trọng, những bước sau như trích xuất metadata hoặc tìm kiếm ngữ nghĩa cũng sẽ bị ảnh hưởng. Vì vậy, OCR đóng vai trò như lớp nền của toàn bộ hệ thống.

Sau khi giai đoạn OCR ổn định hơn, mình sẽ tiếp tục nghiên cứu phần NLP để tự động trích xuất metadata và kết nối nội dung văn bản với hệ thống tìm kiếm, đề xuất căn cứ pháp lý. Nhưng ở thời điểm này, trọng tâm vẫn là hiểu bài toán OCR thật rõ và tạo ra dữ liệu text đủ sạch để các mô hình phía sau có thể hoạt động tốt.
