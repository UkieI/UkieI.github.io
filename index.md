---
layout: default
title: "Home"
lang: en
permalink: /
translation_url: /vi/
---

# DO THANH DAT

AI Engineer & NLP Specialist. Focused on training language models, building semantic search engines, and designing intelligent retrieval pipelines. Based in Da Nang, Viet Nam.

[GitHub](https://github.com/UkieI) · dothanhdat2003.work@gmail.com · (+84) 812174123

---

## Featured Projects

* **[Legal-Basis Search & Recommendation System](https://github.com/UkieI/E2E_VBPL)**
  Hybrid Graph-Vector Retrieval system for educational institutions. Combines PaddleOCR, PhoBERT-CRF for entity extraction, and a dual Qdrant & Neo4j backend.
  _`PyTorch` · `PaddleOCR` · `Qdrant` · `Neo4j` · `Elasticsearch`_
  **Source**: [Github](https://github.com/UkieI/E2E_VBPL), [Demo](https://drive.google.com/drive/folders/1iytdegNUbnb8_9_yNeKP1Od-xMdF6YK3?usp=sharing)

* **[RAG on Legal Documents](https://github.com/dothanhdat2003)**
  Vietnamese legal document RAG chatbot utilizing Gemini API, LangChain, Qwen2.5, and FastAPI. Includes web crawling, chunking, and intent/entity/sentiment analysis.
  _`LangChain` · `Qwen2.5` · `Qdrant` · `FastAPI` · `Gemini API`_

---

## Writing

{% assign posts = site.posts | where: "lang", "en" %}
{% for post in posts %}
* [**{{ post.title }}**]({{ post.url | relative_url }}) — {{ post.date | date: "%B %d, %Y" }}
{% else %}
No English articles yet.
{% endfor %}
