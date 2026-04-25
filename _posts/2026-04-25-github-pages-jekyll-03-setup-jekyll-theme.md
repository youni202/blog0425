---
layout: default
title: "3. Jekyll 테마 선택하고 기본 파일 만들기"
date: 2026-04-25 00:30:00 +0900
nav_exclude: true
---

# 3. Jekyll 테마 선택하고 기본 파일 만들기

이 글에서는 GitHub Pages 블로그에 Jekyll 테마를 적용하기 위한 기본 파일을 만듭니다.

## 목표

Jekyll이 사이트를 빌드할 수 있도록 `_config.yml`, `Gemfile`, 첫 페이지를 준비합니다.

## 테마 선택

문서형 블로그나 지식 정리용 사이트라면 [Just the Docs](https://github.com/just-the-docs/just-the-docs) 같은 테마가 잘 맞습니다.

이유는 다음과 같습니다.

- 검색 기능이 있습니다.
- 왼쪽 내비게이션으로 글 구조를 잡기 좋습니다.
- Markdown 문서가 늘어나도 관리하기 쉽습니다.
- GitHub Pages와 잘 어울립니다.

## 기본 파일 구조

```txt
.
├── Gemfile
├── _config.yml
├── index.md
└── _posts/
    └── YYYY-MM-DD-first-post.md
```

## Gemfile

```ruby
source "https://rubygems.org"

gem "jekyll", "~> 4.3"
gem "just-the-docs"
```

## _config.yml

```yaml
title: My Blog
description: GitHub Pages blog powered by Jekyll
theme: just-the-docs

url: "https://username.github.io"
baseurl: "/repository-name"

permalink: pretty
search_enabled: true
heading_anchors: true
```

{: .note }
일반 저장소로 Pages를 만들 때는 `baseurl`에 저장소 이름을 넣어야 링크와 스타일이 깨지지 않습니다.

## 첫 페이지

```md
---
layout: home
title: 홈
nav_order: 1
---

# My Blog

GitHub Pages와 Jekyll로 운영하는 블로그입니다.
```

## 다음 글

[GitHub Pages 설정하고 자동 배포하기]({{ "/2026/04/25/github-pages-jekyll-04-deploy-pages/" | relative_url }})
