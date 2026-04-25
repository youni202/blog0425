---
layout: home
title: 홈
nav_order: 1
---

# Youni's Blog

생각, 공부, 작업 기록을 차곡차곡 정리하는 공간입니다.

GitHub Pages와 [Just the Docs](https://github.com/just-the-docs/just-the-docs) 테마로 운영합니다.

## 최근 글

{% for post in site.posts %}
- [{{ post.title }}]({{ post.url | relative_url }}) - {{ post.date | date: "%Y-%m-%d" }}
{% else %}
- 아직 등록된 글이 없습니다.
{% endfor %}

## 빠른 링크

- [글 목록]({{ "/posts/" | relative_url }})
- [소개]({{ "/about/" | relative_url }})
- [글 작성 가이드]({{ "/writing-guide/" | relative_url }})
- [GitHub Pages와 Jekyll 시작하기]({{ "/series/github-pages-jekyll/" | relative_url }})
- [기획자의 프로젝트 문서 흐름]({{ "/series/planner-workflow/" | relative_url }})
