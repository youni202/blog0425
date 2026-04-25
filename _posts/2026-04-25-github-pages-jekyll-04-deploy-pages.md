---
layout: default
title: "4. GitHub Pages 설정하고 자동 배포하기"
date: 2026-04-25 00:40:00 +0900
nav_exclude: true
---

# 4. GitHub Pages 설정하고 자동 배포하기

이 글에서는 GitHub Pages를 켜고, `main` 브랜치에 푸시할 때마다 자동으로 블로그가 배포되도록 설정합니다.

## 목표

GitHub Actions로 Jekyll 사이트를 빌드하고 GitHub Pages에 배포합니다.

## Pages 설정

GitHub 저장소에서 다음 위치로 이동합니다.

```txt
Settings > Pages
```

배포 방식을 `GitHub Actions`로 선택합니다.

## 워크플로 파일 만들기

`.github/workflows/pages.yml` 파일을 만듭니다.

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

## 배포 확인

파일을 커밋하고 푸시합니다.

```sh
git add .
git commit -m "Set up GitHub Pages deployment"
git push
```

GitHub 저장소의 `Actions` 탭에서 배포가 성공했는지 확인합니다.

## 다음 글

[글 작성 흐름과 운영 팁 정리하기]({{ "/2026/04/25/github-pages-jekyll-05-writing-workflow/" | relative_url }})
