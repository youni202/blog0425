---
layout: default
title: 글 목록
nav_order: 3
permalink: /posts/
---

# 글 목록

{% for post in site.posts %}
## [{{ post.title }}]({{ post.url | relative_url }})

{{ post.date | date: "%Y-%m-%d" }}

{% if post.excerpt %}
{{ post.excerpt | strip_html | truncate: 160 }}
{% endif %}

{% else %}
아직 등록된 글이 없습니다.
{% endfor %}
