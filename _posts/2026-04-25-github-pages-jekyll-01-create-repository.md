---
layout: default
title: "1. GitHub 저장소 만들기"
date: 2026-04-25 00:10:00 +0900
nav_exclude: true
permalink: /series/github-pages-jekyll/01-create-repository/
---

# 1. GitHub 저장소 만들기

GitHub Pages 블로그의 시작점은 저장소입니다. Jekyll 테마를 적용하더라도 결국 모든 글, 설정, 이미지, 배포 워크플로는 하나의 GitHub 저장소 안에서 관리됩니다.

이 글에서는 블로그용 저장소를 만들고, 나중에 로컬에서 연결할 수 있도록 clone URL을 준비하는 과정까지 정리합니다.

## 이번 글의 목표

이 글을 끝내면 다음 상태가 됩니다.

| 항목 | 결과 |
| --- | --- |
| GitHub 저장소 | 생성 완료 |
| 공개 범위 | GitHub Pages에 맞게 설정 |
| 기본 브랜치 | `main` |
| clone URL | 복사 가능 |

## 저장소 이름 먼저 정하기

GitHub Pages 주소는 저장소 이름에 따라 달라집니다.

| 저장소 이름 | 생성되는 주소 | 추천 상황 |
| --- | --- | --- |
| `username.github.io` | `https://username.github.io/` | 대표 홈페이지를 만들 때 |
| 일반 저장소 이름 | `https://username.github.io/repository-name/` | 블로그, 문서, 프로젝트 사이트를 따로 만들 때 |

예를 들어 GitHub 아이디가 `youni202`이고 저장소 이름이 `blog0425`라면 Pages 주소는 다음처럼 됩니다.

```txt
https://youni202.github.io/blog0425/
```

{: .note }
일반 저장소 이름으로 만들면 나중에 Jekyll 설정에서 `baseurl`을 저장소 이름과 맞춰야 합니다. 이 부분은 3편에서 다룹니다.

## 저장소 만들기

GitHub에 로그인한 뒤 다음 순서로 진행합니다.

1. 오른쪽 위 `+` 버튼을 누릅니다.
2. `New repository`를 선택합니다.
3. `Repository name`에 저장소 이름을 입력합니다.
4. 블로그를 공개할 예정이라면 `Public`을 선택합니다.
5. `Add a README file`은 선택하지 않아도 됩니다.
6. `.gitignore`와 `license`도 처음에는 비워둬도 됩니다.
7. `Create repository`를 누릅니다.

저장소를 비워두는 이유는 로컬에서 Jekyll 구조를 직접 만들고 첫 커밋으로 올리기 위해서입니다. GitHub에서 README를 먼저 만들고 시작해도 되지만, 처음 배우는 단계에서는 “빈 저장소 → 로컬에서 파일 만들기 → push” 흐름이 더 명확합니다.

## Public과 Private 중 무엇을 고를까?

GitHub Pages 블로그를 공개 사이트로 운영하려면 보통 `Public` 저장소가 가장 단순합니다.

| 선택 | 특징 |
| --- | --- |
| Public | Pages 공개 운영이 쉽고, 저장소도 공개됨 |
| Private | 저장소는 숨길 수 있지만 Pages 기능과 요금제 조건을 확인해야 함 |

처음 블로그를 만들 때는 `Public`으로 시작하는 것을 추천합니다. 글과 설정이 모두 공개되어도 괜찮은 구조로 운영하는 편이 GitHub Pages와 잘 맞습니다.

## 저장소 주소 확인하기

저장소를 만들면 GitHub가 다음과 같은 HTTPS 주소를 보여줍니다.

```txt
https://github.com/username/repository-name.git
```

예시는 다음과 같습니다.

```txt
https://github.com/youni202/blog0425.git
```

이 주소는 다음 글에서 `git clone` 명령에 사용합니다.

## 체크리스트

다음 항목을 확인하고 넘어가면 좋습니다.

- 저장소 이름을 정했다.
- 저장소가 `Public`인지 확인했다.
- 기본 브랜치가 `main`인지 확인했다.
- HTTPS clone URL을 복사할 수 있다.
- 아직 Pages 설정은 하지 않았다.

## 자주 헷갈리는 점

**저장소 이름을 바꾸면 Pages 주소도 바뀌나요?**

일반 저장소 Pages 주소는 저장소 이름을 포함합니다. 저장소 이름을 바꾸면 URL도 바뀌므로, 처음에 너무 임시 이름으로 만들지 않는 편이 좋습니다.

**README를 만들고 시작해도 되나요?**

가능합니다. 다만 로컬에서 빈 폴더에 바로 클론하려면 저장소가 비어 있는 편이 깔끔합니다.

**GitHub Pages 설정은 지금 해야 하나요?**

아직 하지 않아도 됩니다. 먼저 로컬에 Jekyll 파일을 만들고 push한 뒤, 4편에서 GitHub Pages와 Actions 배포를 설정합니다.

## 다음 글

[로컬에 저장소 클론하고 첫 커밋 준비하기]({{ "/series/github-pages-jekyll/02-clone-repository/" | relative_url }})
