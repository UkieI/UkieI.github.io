# Blog Writing and Project Structure Guide

This project is a simple Jekyll portfolio and blog. Use this guide when you want to add new work notes, project writeups, or bilingual blog posts.

## Project Structure

```text
my-portfolio/
+-- _config.yml          # Main site settings
+-- index.md             # English home page
+-- about.md             # English about page
+-- vi/
|   +-- index.md         # Vietnamese home page
|   +-- about.md         # Vietnamese about page
+-- _posts/              # All blog posts
+-- _data/               # Shared structured data, such as projects
+-- _layouts/            # Page and post templates
+-- _includes/           # Shared parts like nav and footer
+-- assets/
|   +-- css/style.css    # Main styling
+-- docker-compose.yml   # Local Jekyll server with Docker
+-- Gemfile              # Ruby dependencies
+-- BLOG_GUIDE.md        # This guide
```

## Where To Edit

Use these files for normal content work:

- `index.md`: update English homepage content, featured projects, and intro.
- `about.md`: update English biography or resume-style information.
- `vi/index.md`: update Vietnamese homepage content.
- `vi/about.md`: update Vietnamese biography.
- `_posts/`: add new blog articles.
- `assets/`: store images, diagrams, screenshots, and CSS.

Avoid editing these unless you are changing the site system:

- `_layouts/`: controls how pages and posts are rendered.
- `_includes/`: shared navigation and footer.
- `Gemfile`, `Gemfile.lock`: Ruby/Jekyll dependencies.
- `_site/`: generated output. Do not edit manually.
- `.jekyll-cache/`: generated cache. Do not edit manually.

## Writing A New Blog Post

All posts go inside `_posts/`.

File name format:

```text
YYYY-MM-DD-language-short-title.md
```

Examples:

```text
_posts/2026-06-11-en-paddleocr-ocr-stage.md
_posts/2026-06-11-vi-paddleocr-ocr-stage.md
```

Use `en` for English posts and `vi` for Vietnamese posts.

## Adding Featured Projects

Featured projects are managed in `_data/projects.yml`. Add or edit projects there instead of editing the project lists directly in `index.md` or `vi/index.md`.

Project template:

```yml
- id: your-project-id
  order: 3
  featured: true
  links:
    post: "/blog/your-project-post/"
    source: "https://github.com/your-name/your-project"
    demo: ""
  tech:
    - Python
    - FastAPI
    - Qdrant
  en:
    title: "English project title"
    description: "Short English project description."
  vi:
    title: "Tieu de du an tieng Viet"
    description: "Mo ta ngan bang tieng Viet."
```

Project rules:

- Keep `id` unique.
- Use `order` to control display order.
- Set `featured: true` to show the project on both homepages.
- Set `featured: false` to keep the project in data but hide it from homepages.
- Use `links.post` for the main blog post about the project. The project title links here first.
- Leave `links.post`, `links.source`, or `links.demo` as an empty string when unavailable.
- Put shared technologies in `tech`.
- Put language-specific title and description inside `en` and `vi`.

## Related Posts

Use `related_ref` to group posts about the same project or research topic.

Example:

```md
related_ref: legal-document-research
```

Any English posts with the same `related_ref` will appear under **Related Posts** at the bottom of the article. Vietnamese posts with the same `related_ref` will appear under **Bài viết liên quan** on Vietnamese articles.

Keep `ref` and `related_ref` separate:

- `ref`: connects translations of the same article.
- `related_ref`: connects different articles in the same topic series.

## Blog Post Template

Copy this template for a new English post:

```md
---
layout: post
title: "Your Post Title"
date: 2026-06-11
categories: [AI, NLP]
tags: [Python, RAG, Qdrant]
excerpt: "One short sentence that summarizes the article."
lang: en
ref: your-shared-post-id
permalink: /blog/your-url-slug/
---

Write your article here.
```

Copy this template for a Vietnamese post:

```md
---
layout: post
title: "Tieu de bai viet"
date: 2026-06-11
categories: [AI, NLP]
tags: [Python, RAG, Qdrant]
excerpt: "Mot cau ngan tom tat noi dung bai viet."
lang: vi
ref: your-shared-post-id
permalink: /vi/blog/your-url-slug/
---

Viet noi dung bai viet o day.
```

Important fields:

- `layout: post`: tells Jekyll to use the blog post layout.
- `title`: post title shown on the page.
- `date`: publish date.
- `categories`: broad topics.
- `tags`: specific tools, methods, or keywords.
- `excerpt`: short summary.
- `lang`: use `en` or `vi`.
- `ref`: shared ID for the same article in different languages.
- `permalink`: final URL.

## Bilingual Post Workflow

For one article in two languages:

1. Write the English post in `_posts/`.
2. Write the Vietnamese version in `_posts/`.
3. Use the same `date`, `categories`, `tags`, and `ref`.
4. Use different `lang` values.
5. Use different `permalink` values.

Example:

```md
lang: en
ref: paddleocr-ocr-stage
permalink: /blog/paddleocr-ocr-stage/
```

```md
lang: vi
ref: paddleocr-ocr-stage
permalink: /vi/blog/giai-doan-ocr-paddleocr/
```

The homepage automatically lists posts by language:

- English posts appear on `/`.
- Vietnamese posts appear on `/vi/`.

## Suggested Blog Categories

Keep categories broad and reusable:

- `AI`
- `NLP`
- `OCR`
- `RAG`
- `Backend`
- `Search`
- `Research`
- `Project`
- `Learning`

Use tags for specific details:

- `PaddleOCR`
- `PhoBERT`
- `Qdrant`
- `Neo4j`
- `FastAPI`
- `LangChain`
- `Gemini`
- `PyTorch`

## Simple Article Structure

Use this structure for work logs or project writeups:

```md
## Context

What problem are you working on?

## Goal

What are you trying to achieve?

## Approach

What method, model, library, or system design did you use?

## Implementation Notes

What did you build or test?

## Problems

What issues did you find?

## Result

What works now?

## Next Steps

What will you do next?
```

## Adding Images

Put images in `assets/images/`.

Recommended structure:

```text
assets/images/
+-- posts/
|   +-- paddleocr-ocr-stage/
|       +-- sample-input.png
|       +-- pipeline.png
+-- projects/
    +-- legal-search/
        +-- architecture.png
```

Use images in Markdown like this:

```md
![OCR pipeline diagram](/assets/images/posts/paddleocr-ocr-stage/pipeline.png)
```

Keep image file names short, lowercase, and descriptive.

## Running The Site Locally

With Docker:

```bash
docker compose up
```

Then open:

```text
http://localhost:4000
```

Without Docker, if Ruby and Bundler are installed:

```bash
bundle install
bundle exec jekyll serve
```

## Publishing Checklist

Before committing a new post:

- File name starts with the correct date.
- Front matter is wrapped with `---`.
- `layout: post` is set.
- `lang` is correct.
- `permalink` starts with `/blog/` for English or `/vi/blog/` for Vietnamese.
- Tags and categories are useful.
- Links work.
- Images are stored in `assets/images/`.
- The site runs locally without build errors.

## Recommended Writing Rules

- Keep each post focused on one topic.
- Prefer clear technical notes over long introductions.
- Explain what you did, why you did it, and what changed.
- Add code snippets only when they help the reader understand the work.
- Use screenshots or diagrams for pipelines and system architecture.
- End with concrete next steps.
