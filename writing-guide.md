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
---
```

{: .highlight }
`nav_exclude: true`를 넣으면 개별 글이 왼쪽 메뉴에 길게 쌓이지 않고, 글 목록 페이지에서만 보입니다.

## 배포

글을 추가하고 `main` 브랜치에 푸시하면 GitHub Actions가 자동으로 사이트를 다시 배포합니다.
