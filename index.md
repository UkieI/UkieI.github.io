---
layout: default
title: "Home"
lang: en
permalink: /
translation_url: /vi/
---

# DO THANH DAT

AI Engineer & NLP Specialist. Focused on training language models, building semantic search engines, and designing intelligent retrieval pipelines. Based in Da Nang, Viet Nam.

[GitHub](https://github.com/UkieI) &middot; dothanhdat2003.work@gmail.com &middot; (+84) 812174123

---

## Featured Projects

{% assign featured_projects = site.data.projects | where: "featured", true | sort: "order" %}
{% for project in featured_projects %}
{% assign project_text = project.en %}
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
  {% if project.links.post and project.links.post != "" %}{% assign project_links = project_links | append: "[Blog](" | append: project.links.post | append: ")" %}{% endif %}
  {% if project.links.source and project.links.source != "" %}
    {% if project_links != "" %}{% assign project_links = project_links | append: ", " %}{% endif %}
    {% assign project_links = project_links | append: "[Source](" | append: project.links.source | append: ")" %}
  {% endif %}
  {% if project.links.demo and project.links.demo != "" %}
    {% if project_links != "" %}{% assign project_links = project_links | append: ", " %}{% endif %}
    {% assign project_links = project_links | append: "[Demo](" | append: project.links.demo | append: ")" %}
  {% endif %}
  {% if project_links != "" %}**Links**: {{ project_links }}{% endif %}
{% else %}
No featured projects yet.
{% endfor %}

---

## Writing

{% assign posts = site.posts | where: "lang", "en" %}
{% for post in posts %}
* [**{{ post.title }}**]({{ post.url | relative_url }}) &mdash; {{ post.date | date: "%B %d, %Y" }}
{% else %}
No English articles yet.
{% endfor %}
