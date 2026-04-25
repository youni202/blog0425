---
layout: default
title: "4. GitHub Pages 설정하고 자동 배포하기"
date: 2026-04-25 00:40:00 +0900
nav_exclude: true
permalink: /series/github-pages-jekyll/04-deploy-pages/
---

# 4. GitHub Pages 설정하고 자동 배포하기

이제 Jekyll 파일을 GitHub에 올렸으니, GitHub Pages가 이 저장소를 웹사이트로 배포하도록 연결합니다. 이 글에서는 GitHub Actions를 사용해 Jekyll 사이트를 빌드하고 Pages에 배포하는 방식을 사용합니다.

## 이번 글의 목표

이 글을 끝내면 다음 상태가 됩니다.

| 항목 | 결과 |
| --- | --- |
| GitHub Pages | 활성화 |
| 배포 방식 | GitHub Actions |
| 자동 배포 | `main` 브랜치 push 때 실행 |
| 사이트 주소 | `https://username.github.io/repository-name/` |

## Pages 설정 열기

GitHub 저장소에서 다음 위치로 이동합니다.

```txt
Settings > Pages
```

`Build and deployment` 영역에서 배포 방식을 `GitHub Actions`로 선택합니다.

{: .note }
저장소가 비어 있거나 Jekyll 파일이 아직 push되지 않았다면 먼저 3편의 파일을 커밋하고 push한 뒤 진행하는 것이 좋습니다.

## GitHub Actions 워크플로 만들기

프로젝트 루트에 다음 경로로 파일을 만듭니다.

```txt
.github/workflows/pages.yml
```

내용은 다음과 같습니다.

{% raw %}
```yaml
name: Deploy Jekyll site to Pages

on:
  push:
    branches:
      - main
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: pages
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Ruby
        uses: ruby/setup-ruby@v1
        with:
          ruby-version: "3.3"
          bundler-cache: true

      - name: Setup Pages
        id: pages
        uses: actions/configure-pages@v5

      - name: Build with Jekyll
        run: bundle exec jekyll build --baseurl "${{ steps.pages.outputs.base_path }}"
        env:
          JEKYLL_ENV: production

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```
{% endraw %}

## 워크플로가 하는 일

이 파일은 크게 두 단계로 동작합니다.

| Job | 역할 |
| --- | --- |
| `build` | 저장소를 체크아웃하고 Jekyll 사이트를 빌드한 뒤 artifact로 업로드 |
| `deploy` | 빌드 결과물을 GitHub Pages에 배포 |

`ruby/setup-ruby`의 `bundler-cache: true` 설정은 `Gemfile`을 기준으로 필요한 gem을 설치하고 캐시합니다. 매번 처음부터 설치하지 않아도 되므로 배포가 조금 더 빨라집니다.

## 커밋하고 푸시하기

워크플로 파일을 만든 뒤 커밋합니다.

```sh
git add .github/workflows/pages.yml
git commit -m "Set up GitHub Pages deployment"
git push
```

push가 끝나면 GitHub 저장소의 `Actions` 탭으로 이동합니다. `Deploy Jekyll site to Pages` 워크플로가 실행 중인지 확인합니다.

## 배포 성공 확인

Actions 실행이 성공하면 Pages 주소로 접속합니다.

```txt
https://username.github.io/repository-name/
```

예시는 다음과 같습니다.

```txt
https://youni202.github.io/blog0425/
```

처음 배포 직후에는 GitHub Pages 캐시 때문에 몇 초에서 몇 분 정도 기다려야 할 수 있습니다.

## 자주 만나는 오류

**`Get Pages site failed` 또는 `Pages site not found`**

Pages 설정이 아직 활성화되지 않았을 때 발생할 수 있습니다. `Settings > Pages`에서 배포 방식을 `GitHub Actions`로 선택했는지 확인합니다.

**CSS가 깨지고 글만 보입니다**

`_config.yml`의 `baseurl`이 저장소 이름과 맞는지 확인합니다. 일반 저장소 Pages라면 보통 `/repository-name` 형태입니다.

**Liquid syntax error가 납니다**

블로그 글 안에 GitHub Actions expression 문법을 넣으면 Jekyll이 Liquid 문법으로 오해할 수 있습니다. 코드 블록 앞뒤를 Liquid의 raw/endraw 태그로 감싸면 됩니다.

## 체크리스트

- `Settings > Pages`에서 GitHub Actions 배포를 선택했다.
- `.github/workflows/pages.yml` 파일을 만들었다.
- 워크플로 파일을 커밋하고 push했다.
- Actions 탭에서 배포 성공을 확인했다.
- Pages 주소로 접속해 사이트가 열리는지 확인했다.

## 다음 글

[글 작성 흐름과 운영 팁 정리하기]({{ "/series/github-pages-jekyll/05-writing-workflow/" | relative_url }})
