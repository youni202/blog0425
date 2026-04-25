---
layout: default
title: "1. GitHub 저장소 만들기"
date: 2026-04-25 00:10:00 +0900
nav_exclude: true
---

# 1. GitHub 저장소 만들기

이 글에서는 GitHub Pages 블로그로 사용할 새 저장소를 만드는 과정을 정리합니다.

## 목표

GitHub에 블로그용 저장소를 만들고, 나중에 로컬에서 클론할 수 있는 저장소 URL을 준비합니다.

## 진행 순서

1. GitHub에 로그인합니다.
2. 오른쪽 위 `+` 메뉴에서 `New repository`를 선택합니다.
3. 저장소 이름을 정합니다.
4. 공개 블로그로 운영할 예정이라면 `Public`으로 둡니다.
5. `Create repository`를 눌러 저장소를 만듭니다.

## 저장소 이름 정하기

GitHub Pages에는 크게 두 가지 주소 방식이 있습니다.

| 저장소 이름 | Pages 주소 예시 | 용도 |
| --- | --- | --- |
| `username.github.io` | `https://username.github.io/` | 사용자 대표 사이트 |
| 일반 저장소 이름 | `https://username.github.io/repository-name/` | 프로젝트나 개별 블로그 |

이 시리즈에서는 일반 저장소를 기준으로 설명합니다.

## 확인할 것

저장소를 만든 뒤에는 HTTPS clone URL을 복사해 둡니다.

```txt
https://github.com/username/repository-name.git
```

## 다음 글

[로컬에 저장소 클론하고 첫 커밋 준비하기]({{ "/2026/04/25/github-pages-jekyll-02-clone-repository/" | relative_url }})
