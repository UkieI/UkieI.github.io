---
layout: default
title: "Trang chủ"
lang: vi
permalink: /vi/
translation_url: /
---

# ĐỖ THÀNH ĐẠT

AI Engineer & NLP Specialist. Mình tập trung vào huấn luyện mô hình ngôn ngữ, xây dựng hệ thống tìm kiếm ngữ nghĩa và thiết kế các pipeline truy xuất thông tin thông minh. Hiện mình đang ở Đà Nẵng, Việt Nam.

[GitHub](https://github.com/UkieI) &middot; dothanhdat2003.work@gmail.com &middot; (+84) 812174123

---

## Dự án nổi bật

{% assign featured_projects = site.data.projects | where: "featured", true | sort: "order" %}
{% for project in featured_projects %}
{% assign project_text = project.vi %}
{% assign project_title_url = "" %}
{% if project.links.post and project.links.post != "" %}
  {% assign project_title_url = project.links.post %}
{% elsif project.links.source and project.links.source != "" %}
  {% assign project_title_url = project.links.source %}
{% endif %}

* {% if project_title_url != "" %}**[{{ project_text.title }}]({{ project_title_url | relative_url }})**{% else %}**{{ project_text.title }}**{% endif %}
  {{ project_text.description }}
  _{% for item in project.tech %}`{{ item }}`{% unless forloop.last %} &middot; {% endunless %}{% endfor %}_
  {% assign project_links = "" %}
  {% if project.links.post and project.links.post != "" %}{% assign project_links = project_links | append: "[Bài viết](" | append: project.links.post | append: ")" %}{% endif %}
  {% if project.links.source and project.links.source != "" %}
    {% if project_links != "" %}{% assign project_links = project_links | append: ", " %}{% endif %}
    {% assign project_links = project_links | append: "[Nguồn](" | append: project.links.source | append: ")" %}
  {% endif %}
  {% if project.links.demo and project.links.demo != "" %}
    {% if project_links != "" %}{% assign project_links = project_links | append: ", " %}{% endif %}
    {% assign project_links = project_links | append: "[Demo](" | append: project.links.demo | append: ")" %}
  {% endif %}
  {% if project_links != "" %}**Liên kết**: {{ project_links }}{% endif %}
{% else %}
Chưa có dự án nổi bật.
{% endfor %}

---

## Bài viết

{% assign posts = site.posts | where: "lang", "vi" %}
{% for post in posts %}
* [**{{ post.title }}**]({{ post.url | relative_url }}) &mdash; {{ post.date | date: "%d/%m/%Y" }}
{% else %}
Chưa có bài viết tiếng Việt.
{% endfor %}
