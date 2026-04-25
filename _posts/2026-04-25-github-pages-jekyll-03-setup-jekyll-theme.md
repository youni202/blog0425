---
layout: default
title: "3. Jekyll 테마 선택하고 기본 파일 만들기"
date: 2026-04-25 00:30:00 +0900
nav_exclude: true
permalink: /series/github-pages-jekyll/03-setup-jekyll-theme/
---

# 3. Jekyll 테마 선택하고 기본 파일 만들기

GitHub 저장소를 로컬에 클론했다면 이제 Jekyll 사이트의 기본 파일을 만들 차례입니다. 이 글에서는 Just the Docs 테마를 기준으로 설명합니다.

Just the Docs는 원래 문서 사이트용 테마지만, 블로그나 지식 정리 노트에도 잘 어울립니다. 왼쪽 메뉴, 검색, 표, 코드 블록, callout 같은 기능이 기본으로 준비되어 있어서 글이 쌓여도 관리하기 쉽습니다.

## 이번 글의 목표

이 글을 끝내면 다음 파일이 생깁니다.

| 파일 | 역할 |
| --- | --- |
| `Gemfile` | Jekyll과 테마 의존성 정의 |
| `_config.yml` | 사이트 제목, 주소, 테마 설정 |
| `index.md` | 첫 화면 |
| `_posts/...md` | 첫 글 |
| `.gitignore` | 빌드 결과물 제외 |

## 기본 폴더 구조

처음에는 단순하게 시작합니다.

```txt
.
├── Gemfile
├── _config.yml
├── index.md
├── .gitignore
└── _posts/
    └── 2026-04-25-welcome.md
```

Jekyll은 `_config.yml`을 읽고 사이트 설정을 결정합니다. `_posts` 폴더 안의 Markdown 파일은 블로그 글로 처리합니다.

## Gemfile 만들기

프로젝트 루트에 `Gemfile`을 만듭니다.

```ruby
source "https://rubygems.org"

gem "jekyll", "~> 4.3"
gem "just-the-docs"

group :jekyll_plugins do
  gem "jekyll-seo-tag"
end
```

이 파일은 GitHub Actions가 사이트를 빌드할 때 필요한 Ruby gem을 설치하는 기준이 됩니다.

## _config.yml 만들기

다음으로 `_config.yml`을 만듭니다.

```yaml
title: My Blog
description: GitHub Pages blog powered by Jekyll
theme: just-the-docs

url: "https://username.github.io"
baseurl: "/repository-name"

permalink: pretty
lang: ko-KR
search_enabled: true
heading_anchors: true
```

여기서 가장 중요한 값은 `url`과 `baseurl`입니다.

| 설정 | 예시 | 설명 |
| --- | --- | --- |
| `url` | `https://youni202.github.io` | GitHub Pages의 기본 도메인 |
| `baseurl` | `/blog0425` | 저장소 이름 |

일반 저장소로 Pages를 운영할 때는 `baseurl`을 비워두면 CSS, 링크, 이미지 경로가 깨질 수 있습니다.

{: .tip }
저장소 이름이 `username.github.io`인 사용자 사이트라면 보통 `baseurl`을 비워둡니다. 일반 저장소라면 `/repository-name`을 넣습니다.

## 홈 페이지 만들기

`index.md` 파일을 만듭니다.

```md
---
layout: home
title: 홈
nav_order: 1
---

# My Blog

GitHub Pages와 Jekyll로 운영하는 블로그입니다.

## 최근 글

{% raw %}
{% for post in site.posts %}
- [{{ post.title }}]({{ post.url | relative_url }}) - {{ post.date | date: "%Y-%m-%d" }}
{% else %}
- 아직 등록된 글이 없습니다.
{% endfor %}
{% endraw %}
```

위 코드에서 `site.posts`는 Jekyll이 알고 있는 글 목록입니다. 새 글을 `_posts` 폴더에 넣으면 홈 화면에 자동으로 나타납니다.

## 첫 글 만들기

`_posts` 폴더를 만들고 첫 글을 추가합니다.

```txt
_posts/2026-04-25-welcome.md
```

내용은 다음처럼 시작할 수 있습니다.

```md
---
layout: default
title: 블로그 시작
date: 2026-04-25 00:00:00 +0900
nav_exclude: true
---

# 블로그 시작

첫 글입니다.

GitHub Pages와 Jekyll로 블로그를 만들었습니다.
```

`nav_exclude: true`는 개별 글이 왼쪽 메뉴에 모두 표시되지 않도록 하는 설정입니다. 글이 많아질수록 메뉴가 길어지기 때문에 블로그 글에는 이 값을 넣는 편이 좋습니다.

## .gitignore 만들기

Jekyll은 로컬에서 빌드하면 `_site` 폴더를 만듭니다. 이 폴더는 결과물이므로 Git에 올리지 않는 편이 좋습니다.

`.gitignore` 파일을 만들고 다음 내용을 넣습니다.

```txt
_site/
.sass-cache/
.jekyll-cache/
.jekyll-metadata
vendor/
.bundle/
```

## 변경 사항 커밋하기

파일을 만든 뒤 상태를 확인합니다.

```sh
git status
```

문제가 없다면 커밋합니다.

```sh
git add .
git commit -m "Set up Jekyll site"
git push
```

아직 GitHub Pages 설정을 하지 않았기 때문에 push해도 사이트가 바로 열리지는 않을 수 있습니다. 다음 글에서 배포 설정을 연결합니다.

## 체크리스트

- `Gemfile`을 만들었다.
- `_config.yml`에 `url`과 `baseurl`을 설정했다.
- `index.md` 홈 페이지를 만들었다.
- `_posts`에 첫 글을 만들었다.
- `.gitignore`에 Jekyll 빌드 결과물을 제외했다.
- 변경 사항을 커밋하고 push했다.

## 다음 글

[GitHub Pages 설정하고 자동 배포하기]({{ "/series/github-pages-jekyll/04-deploy-pages/" | relative_url }})
