---
layout: default
title: "5. 글 작성 흐름과 운영 팁 정리하기"
date: 2026-04-25 00:50:00 +0900
nav_exclude: true
permalink: /series/github-pages-jekyll/05-writing-workflow/
---

# 5. 글 작성 흐름과 운영 팁 정리하기

GitHub Pages와 Jekyll 배포까지 끝났다면 이제 남은 일은 글을 쓰고, 커밋하고, 푸시하는 흐름을 반복하는 것입니다. 이 글에서는 블로그를 오래 운영하기 위한 기본 글 작성 방식과 폴더 구조, 운영 팁을 정리합니다.

## 이번 글의 목표

이 글을 끝내면 다음 흐름을 이해하게 됩니다.

| 작업 | 결과 |
| --- | --- |
| 새 글 만들기 | `_posts`에 Markdown 파일 추가 |
| 글 설정하기 | front matter 작성 |
| 글 목록 연결 | `site.posts`로 자동 노출 |
| 발행하기 | commit 후 push |
| 운영하기 | 시리즈, 이미지, 초안 관리 |

## 새 글 파일 만들기

Jekyll에서 블로그 글은 `_posts` 폴더에 넣습니다.

파일 이름은 반드시 다음 형식을 따릅니다.

```txt
YYYY-MM-DD-title.md
```

예를 들면 다음과 같습니다.

```txt
_posts/2026-04-25-github-pages-jekyll.md
```

날짜는 글의 발행일로 쓰이고, 뒤의 `title` 부분은 URL에 사용됩니다. 한글 파일명도 가능하지만 URL을 깔끔하게 유지하려면 영어 소문자와 하이픈을 쓰는 편이 좋습니다.

## front matter 작성하기

Jekyll 글의 맨 위에는 front matter를 넣습니다.

```md
---
layout: default
title: 글 제목
date: 2026-04-25 00:00:00 +0900
nav_exclude: true
---

# 글 제목

본문을 작성합니다.
```

각 항목의 의미는 다음과 같습니다.

| 항목 | 설명 |
| --- | --- |
| `layout` | 어떤 레이아웃으로 보여줄지 선택 |
| `title` | 글 제목 |
| `date` | 글 발행 날짜와 시간 |
| `nav_exclude` | 왼쪽 메뉴에서 숨길지 여부 |

`nav_exclude: true`를 넣으면 개별 글이 왼쪽 메뉴에 모두 나타나지 않습니다. 블로그 글은 글 목록에서만 보이게 하고, 메뉴에는 소개나 시리즈 목차 같은 고정 페이지만 두는 편이 깔끔합니다.

## 글 작성 템플릿

매번 새 글을 처음부터 쓰기보다 템플릿을 하나 만들어두면 편합니다.

```txt
_templates/post.md
```

예시는 다음과 같습니다.

```md
---
layout: default
title: 글 제목
date: YYYY-MM-DD 00:00:00 +0900
nav_exclude: true
---

# 글 제목

첫 문단에는 글의 핵심을 짧게 적습니다.

## 배경

왜 이 글을 쓰는지 적습니다.

## 내용

정리할 내용을 적습니다.

## 마무리

나중에 다시 볼 포인트를 적습니다.
```

새 글을 쓸 때는 이 파일을 복사해서 `_posts`에 넣고 제목과 날짜를 바꾸면 됩니다.

## 글 목록 만들기

글이 늘어나면 글 목록 페이지가 필요합니다.

예를 들어 `posts.md`를 만들고 다음처럼 작성합니다.

{% raw %}
```md
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
```
{% endraw %}

`site.posts`는 Jekyll이 자동으로 모아주는 글 목록입니다. 최신 글이 위에 오도록 정렬됩니다.

## 시리즈 글 운영하기

여러 글을 하나의 흐름으로 묶고 싶다면 시리즈 목차 페이지를 따로 만드는 것이 좋습니다.

예시는 다음과 같습니다.

```txt
series-github-pages-jekyll.md
```

그리고 각 글에는 고정 permalink를 지정합니다.

```yaml
permalink: /series/github-pages-jekyll/01-create-repository/
```

이렇게 하면 날짜가 바뀌어도 링크가 안정적으로 유지됩니다.

{: .tip }
튜토리얼 시리즈는 날짜 기반 URL보다 의미 있는 고정 URL이 더 읽기 좋습니다.

## 이미지 넣기

이미지는 글별 폴더에 모아두면 관리하기 쉽습니다. 특히 워드 문서나 기존 블로그에서 이미지를 옮길 때는 글과 이미지 폴더가 1:1로 매칭되어야 누락을 줄일 수 있습니다.

```txt
assets/
└── images/
    └── posts/
        └── github-pages-jekyll/
            ├── 01-create-repository.png
            └── 02-pages-settings.png
```

이미지는 `figure.html` include로 넣습니다.

{% raw %}
```liquid
{% include figure.html
  src="/assets/images/posts/github-pages-jekyll/02-pages-settings.png"
  alt="GitHub 저장소의 Pages 설정 화면에서 GitHub Actions가 선택된 모습"
  caption="GitHub Pages의 배포 방식을 GitHub Actions로 선택합니다."
  credit="출처: GitHub 화면 캡처"
%}
```
{% endraw %}

`alt`에는 이미지를 볼 수 없는 사람도 내용을 이해할 수 있는 설명을 적습니다. `caption`에는 이미지가 본문에서 어떤 맥락을 갖는지 적습니다.

이미지 파일 이름은 순서를 알 수 있게 작성합니다.

```txt
01-overview.png
02-create-repository.png
03-pages-settings.png
```

## 발행 흐름

글을 작성한 뒤에는 항상 상태를 확인합니다.

```sh
git status
```

새 글만 커밋하려면 파일을 직접 지정합니다.

```sh
git add _posts/2026-04-25-github-pages-jekyll.md
git commit -m "Add GitHub Pages Jekyll post"
git push
```

여러 파일을 한 번에 커밋할 수도 있습니다.

```sh
git add .
git commit -m "Update blog posts"
git push
```

push가 끝나면 GitHub Actions가 자동으로 사이트를 다시 빌드하고 배포합니다.

## 배포 후 확인할 것

글을 push한 뒤에는 다음을 확인합니다.

- GitHub 저장소의 `Actions` 탭에서 배포가 성공했는지 확인합니다.
- 글 목록 페이지에 새 글이 보이는지 확인합니다.
- 새 글 URL을 직접 열어봅니다.
- 표, 코드 블록, 이미지, 링크가 제대로 보이는지 확인합니다.
- 이미지마다 alt와 caption이 빠지지 않았는지 확인합니다.

## 운영 팁

| 상황 | 추천 방식 |
| --- | --- |
| 글이 아직 덜 완성됨 | `_drafts/` 폴더에 보관 |
| 글은 공개하지만 메뉴에는 숨김 | `nav_exclude: true` 사용 |
| 시리즈 글을 묶고 싶음 | 시리즈 목차 페이지와 고정 permalink 사용 |
| 이미지가 필요함 | `assets/images/posts/post-slug/` 폴더와 `figure.html` 사용 |
| 링크가 자주 깨짐 | `relative_url` 필터 사용 |
| 긴 코드 예시가 있음 | fenced code block 사용 |
| GitHub Actions 문법을 글에 넣음 | Liquid의 raw/endraw 태그 사용 |

## 마무리

GitHub Pages와 Jekyll 조합의 가장 큰 장점은 블로그 전체가 파일과 Git 기록으로 남는다는 점입니다. 글을 쓰고, 커밋하고, 푸시하면 자동으로 배포됩니다.

처음에는 구조를 너무 복잡하게 만들 필요가 없습니다. 홈, 글 목록, 소개, 시리즈 목차 정도만 있어도 충분히 운영을 시작할 수 있습니다. 글이 쌓이면 그때 카테고리, 태그, 이미지, 검색 최적화 같은 요소를 조금씩 추가하면 됩니다.

[시리즈 목차로 돌아가기]({{ "/series/github-pages-jekyll/" | relative_url }})
