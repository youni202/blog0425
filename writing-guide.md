---
layout: default
title: 글 작성 가이드
nav_order: 4
permalink: /writing-guide/
---

# 글 작성 가이드

새 글은 `_posts/` 폴더에 Markdown 파일로 추가합니다.

파일 이름은 다음 형식을 사용합니다.

```txt
YYYY-MM-DD-title.md
```

예시는 다음과 같습니다.

```txt
2026-04-25-my-first-note.md
```

글 맨 위에는 front matter를 넣습니다.

```yaml
---
layout: default
title: 글 제목
date: 2026-04-25 00:00:00 +0900
nav_exclude: true
image_dir: /assets/images/posts/my-first-note
---
```

{: .highlight }
`nav_exclude: true`를 넣으면 개별 글이 왼쪽 메뉴에 길게 쌓이지 않고, 글 목록 페이지에서만 보입니다.

## 배포

글을 추가하고 `main` 브랜치에 푸시하면 GitHub Actions가 자동으로 사이트를 다시 배포합니다.

## 이미지 관리

이미지는 글마다 별도 폴더에 저장합니다.

```txt
assets/images/posts/
└── my-first-note/
    ├── 01-main-screen.png
    ├── 02-settings-page.png
    └── 03-result.png
```

폴더 이름은 글 파일의 slug와 맞춥니다.

| 글 파일 | 이미지 폴더 |
| --- | --- |
| `_posts/2026-04-25-my-first-note.md` | `assets/images/posts/my-first-note/` |
| `_posts/2026-04-25-teams-intro.md` | `assets/images/posts/teams-intro/` |

본문에는 `figure.html` include를 사용합니다.

{% raw %}
```liquid
{% include figure.html
  src="/assets/images/posts/my-first-note/01-main-screen.png"
  alt="GitHub Pages 설정 화면에서 GitHub Actions가 선택된 모습"
  caption="GitHub Pages 배포 방식을 GitHub Actions로 선택합니다."
  credit="출처: GitHub 화면 캡처"
%}
```
{% endraw %}

`alt`에는 이미지를 보지 못해도 의미가 전달되도록 설명을 적습니다. `caption`에는 본문을 읽는 사람이 이미지의 맥락을 이해할 수 있는 설명을 적습니다.

{: .tip }
워드 파일이나 기존 블로그 글에서 이미지를 가져올 때도 글별 폴더에 이미지를 먼저 넣고, 본문에는 같은 순서의 `figure.html` include를 연결하면 누락을 줄일 수 있습니다.

## 워드/기존 블로그에서 가져올 때

워드 문서나 기존 블로그 글을 옮길 때는 다음 순서로 정리합니다.

1. 글 하나당 Markdown 파일 하나를 만듭니다.
2. 글의 slug를 정합니다.
3. `assets/images/posts/slug/` 폴더를 만듭니다.
4. 원본 이미지 파일을 순서대로 저장합니다.
5. 본문에서 이미지가 들어갈 위치마다 `figure.html` include를 넣습니다.
6. 모든 이미지에 `alt`와 `caption`을 작성합니다.

이미지 파일 이름은 순서를 알 수 있게 짓습니다.

```txt
01-overview.png
02-create-repository.png
03-pages-settings.png
```

이렇게 하면 나중에 글과 이미지를 함께 찾기 쉽고, 이미지가 누락됐는지도 확인하기 쉽습니다.
