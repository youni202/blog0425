---
layout: default
title: GitHub Pages와 Jekyll 시작하기
nav_order: 5
permalink: /series/github-pages-jekyll/
---

# GitHub Pages와 Jekyll 시작하기

GitHub에 새 저장소를 만들고, Jekyll 테마를 적용해 GitHub Pages 블로그로 운영하는 과정을 정리하는 시리즈입니다.

## 시리즈 구성

1. [GitHub 저장소 만들기]({{ "/2026/04/25/github-pages-jekyll-01-create-repository/" | relative_url }})
2. [로컬에 저장소 클론하고 첫 커밋 준비하기]({{ "/2026/04/25/github-pages-jekyll-02-clone-repository/" | relative_url }})
3. [Jekyll 테마 선택하고 기본 파일 만들기]({{ "/2026/04/25/github-pages-jekyll-03-setup-jekyll-theme/" | relative_url }})
4. [GitHub Pages 설정하고 자동 배포하기]({{ "/2026/04/25/github-pages-jekyll-04-deploy-pages/" | relative_url }})
5. [글 작성 흐름과 운영 팁 정리하기]({{ "/2026/04/25/github-pages-jekyll-05-writing-workflow/" | relative_url }})

## 전체 흐름

| 단계 | 목표 | 결과물 |
| --- | --- | --- |
| 1 | GitHub에 빈 저장소 만들기 | 원격 저장소 URL |
| 2 | 로컬 작업 폴더와 원격 저장소 연결 | 클론된 프로젝트 |
| 3 | Jekyll 테마 적용 | `_config.yml`, `Gemfile`, 기본 페이지 |
| 4 | GitHub Pages 배포 설정 | 공개 블로그 URL |
| 5 | 글 작성과 배포 반복 | 지속적으로 운영 가능한 블로그 |

{: .tip }
처음부터 모든 것을 완벽하게 만들기보다, 최소 블로그를 먼저 배포한 뒤 글과 구조를 조금씩 다듬는 편이 훨씬 수월합니다.
