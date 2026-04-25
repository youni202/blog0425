---
layout: default
title: "5. 글 작성 흐름과 운영 팁 정리하기"
date: 2026-04-25 00:50:00 +0900
nav_exclude: true
permalink: /series/github-pages-jekyll/05-writing-workflow/
---

# 5. 글 작성 흐름과 운영 팁 정리하기

이 글에서는 Jekyll 블로그를 만든 뒤 실제로 글을 쓰고 운영하는 흐름을 정리합니다.

## 목표

새 글을 만들고, 커밋하고, GitHub Pages에 자동 배포하는 반복 흐름을 익힙니다.

## 글 파일 만들기

Jekyll의 일반적인 블로그 글은 `_posts/` 폴더에 넣습니다.

```txt
_posts/YYYY-MM-DD-title.md
```

예시는 다음과 같습니다.

```txt
_posts/2026-04-25-github-pages-jekyll.md
```

## 글 기본 형식

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

## 발행 흐름

```sh
git status
git add _posts/2026-04-25-github-pages-jekyll.md
git commit -m "Add GitHub Pages Jekyll post"
git push
```

푸시가 끝나면 GitHub Actions가 자동으로 사이트를 다시 배포합니다.

## 운영 팁

| 상황 | 추천 방식 |
| --- | --- |
| 글이 아직 덜 완성됨 | `_drafts/` 폴더에 보관 |
| 글은 공개하지만 메뉴에는 숨김 | `nav_exclude: true` 사용 |
| 시리즈 글을 묶고 싶음 | 시리즈 안내 페이지를 따로 만들기 |
| 이미지가 필요함 | `assets/images/` 폴더 사용 |
| 링크가 자주 깨짐 | `relative_url` 필터 사용 |

## 마무리

GitHub Pages와 Jekyll 조합의 장점은 글과 설정을 모두 Git으로 관리할 수 있다는 점입니다. 한 번 구조를 잡아두면 글을 쓰고 푸시하는 단순한 흐름만 반복하면 됩니다.

[시리즈 목차로 돌아가기]({{ "/series/github-pages-jekyll/" | relative_url }})
