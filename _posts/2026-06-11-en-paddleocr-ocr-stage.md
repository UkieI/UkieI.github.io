---
layout: post
title: "The OCR Stage in Legal Document Digitization"
date: 2026-06-11
categories: [AI, OCR]
tags: [PaddleOCR, OCR, legal-documents, document-ai]
excerpt: "A short note on researching PaddleOCR for digitizing decisions and decrees in educational institutions."
lang: en
ref: paddleocr-ocr-stage
permalink: /blog/paddleocr-ocr-stage/
---

For my graduation project, I am working on an approach to **digitize and search legal bases** in decisions and decrees used within educational institutions. Before moving into NLP tasks such as metadata extraction, entity recognition, or legal-basis recommendation, the first stage that needs to be reliable is **OCR**.

At this stage, the goal is not to build the full system immediately. The goal is to understand how scanned documents and document images can be converted into text that downstream models can process. For administrative documents, OCR is more than recognizing characters. The pipeline also needs to handle page layout, headings, document numbers, issue dates, legal-basis sections, clauses, signatures, and stamps when they appear.

I chose to study **PaddleOCR** because it already provides a practical document OCR pipeline, including text detection, text recognition, and support for multiple input image formats. Right now, the work is focused on planning the implementation, preparing document images, labeling a small set of samples, and studying how PaddleOCR behaves on Vietnamese legal and administrative text.

A planned OCR pipeline includes these steps:

1. Collect scanned files or document images from decisions and decrees.
2. Preprocess images by correcting rotation, reducing noise, and normalizing contrast.
3. Use PaddleOCR to detect text regions and recognize text content.
4. Review OCR errors in important fields such as document numbers, dates, organization names, and legal-basis sections.
5. Normalize the output into structured text for the later NLP stages.

The main challenge is input quality. Some documents can be blurred, skewed, poorly scanned, or inconsistent in layout. If OCR fails on important fields, later steps such as metadata extraction and semantic search will also become less reliable. That is why OCR acts as the foundation of the whole system.

After the OCR stage becomes more stable, I will continue with the NLP part: automatically extracting metadata and connecting document content to the legal-basis search and recommendation system. For now, the focus is to understand the OCR problem clearly and produce text clean enough for the models that come after it.
