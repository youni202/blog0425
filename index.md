---
layout: home
title: Home
nav_order: 1
---

# Youni Blog

Welcome to my GitHub Pages blog.

This site uses the [Just the Docs](https://github.com/just-the-docs/just-the-docs) Jekyll theme.

## Latest posts

{% for post in site.posts %}
- [{{ post.title }}]({{ post.url | relative_url }}) - {{ post.date | date: "%Y-%m-%d" }}
{% endfor %}
