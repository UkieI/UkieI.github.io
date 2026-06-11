---
layout: default
title: "Trang chủ"
lang: vi
permalink: /vi/
translation_url: /
---

# ĐỖ THÀNH ĐẠT

AI Engineer & NLP Specialist. Mình tập trung vào huấn luyện mô hình ngôn ngữ, xây dựng hệ thống tìm kiếm ngữ nghĩa và thiết kế các pipeline truy xuất thông tin thông minh. Hiện mình đang ở Đà Nẵng, Việt Nam.

[GitHub](https://github.com/UkieI) · dothanhdat2003.work@gmail.com · (+84) 812174123

---

## Dự án nổi bật

* **[Hệ thống tìm kiếm và đề xuất căn cứ pháp lý](https://github.com/UkieI/E2E_VBPL)**
  Hệ thống truy xuất hybrid graph-vector cho môi trường cơ sở giáo dục. Dự án kết hợp PaddleOCR, PhoBERT-CRF để trích xuất thực thể và backend sử dụng Qdrant cùng Neo4j.
  _`PyTorch` · `PaddleOCR` · `Qdrant` · `Neo4j` · `Elasticsearch`_
  **Nguồn**: [Github](https://github.com/UkieI/E2E_VBPL), [Demo](https://drive.google.com/drive/folders/1iytdegNUbnb8_9_yNeKP1Od-xMdF6YK3?usp=sharing)

* **[RAG trên văn bản pháp lý](https://github.com/dothanhdat2003)**
  Chatbot RAG cho văn bản pháp lý tiếng Việt, sử dụng Gemini API, LangChain, Qwen2.5 và FastAPI. Dự án bao gồm crawling dữ liệu, chunking và phân tích intent/entity/sentiment.
  _`LangChain` · `Qwen2.5` · `Qdrant` · `FastAPI` · `Gemini API`_

---

## Bài viết

{% assign posts = site.posts | where: "lang", "vi" %}
{% for post in posts %}
* [**{{ post.title }}**]({{ post.url | relative_url }}) — {{ post.date | date: "%d/%m/%Y" }}
{% else %}
Chưa có bài viết tiếng Việt.
{% endfor %}
