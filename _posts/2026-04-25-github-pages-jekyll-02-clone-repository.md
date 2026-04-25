---
layout: default
title: "2. 로컬에 저장소 클론하고 첫 커밋 준비하기"
date: 2026-04-25 00:20:00 +0900
nav_exclude: true
permalink: /series/github-pages-jekyll/02-clone-repository/
---

# 2. 로컬에 저장소 클론하고 첫 커밋 준비하기

이제 GitHub에 만든 저장소를 내 컴퓨터로 가져올 차례입니다. 로컬에 저장소를 클론하면 Markdown 글, Jekyll 설정, GitHub Actions 워크플로 파일을 편집하고 Git으로 기록할 수 있습니다.

## 이번 글의 목표

이 글을 끝내면 다음 상태가 됩니다.

| 항목 | 결과 |
| --- | --- |
| 로컬 작업 폴더 | 준비 완료 |
| Git 원격 연결 | `origin` 설정 완료 |
| 기본 브랜치 | `main` 확인 |
| 커밋/푸시 흐름 | 실행 준비 |

## 작업 폴더 정하기

먼저 블로그를 둘 위치를 정합니다.

예를 들어 개발 작업을 `~/dev` 아래에 모아둔다면 다음처럼 이동합니다.

```sh
cd ~/dev
```

이제 GitHub 저장소를 클론합니다.

```sh
git clone https://github.com/username/repository-name.git
```

예시는 다음과 같습니다.

```sh
git clone https://github.com/youni202/blog0425.git
```

이 명령은 `blog0425`라는 폴더를 만들고, 그 안에 Git 저장소를 연결합니다.

## 원하는 폴더 이름으로 클론하기

로컬 폴더 이름을 저장소 이름과 다르게 쓰고 싶다면 마지막에 폴더 이름을 붙입니다.

```sh
git clone https://github.com/username/repository-name.git myblog
```

이 경우 GitHub 저장소 이름은 그대로지만, 내 컴퓨터에서는 `myblog` 폴더로 작업합니다.

## 이미 비어 있는 폴더에 클론하기

현재 폴더가 비어 있고, 그 폴더 자체를 저장소로 쓰고 싶다면 마지막에 `.`을 붙입니다.

```sh
git clone https://github.com/username/repository-name.git .
```

{: .highlight }
`.`으로 클론할 때는 현재 폴더가 비어 있어야 안전합니다. 이미 파일이 있다면 충돌이 날 수 있습니다.

## 연결 상태 확인하기

클론이 끝나면 폴더 안으로 들어갑니다.

```sh
cd repository-name
```

현재 브랜치를 확인합니다.

```sh
git branch --show-current
```

보통 `main`이 출력됩니다.

원격 저장소 연결도 확인합니다.

```sh
git remote -v
```

다음처럼 `origin`이 GitHub 주소를 가리키면 정상입니다.

```txt
origin  https://github.com/username/repository-name.git (fetch)
origin  https://github.com/username/repository-name.git (push)
```

## 현재 상태 확인하기

```sh
git status
```

빈 저장소를 클론했다면 아직 커밋이 없거나, 작업할 파일이 없는 상태일 수 있습니다. 괜찮습니다. 다음 글에서 Jekyll 파일을 추가하면서 첫 커밋을 만들게 됩니다.

## 커밋과 푸시 흐름 미리 보기

GitHub Pages 블로그 운영은 결국 다음 흐름을 반복하는 일입니다.

```sh
git status
git add .
git commit -m "작업 내용 설명"
git push
```

각 명령의 역할은 이렇습니다.

| 명령 | 역할 |
| --- | --- |
| `git status` | 바뀐 파일 확인 |
| `git add .` | 커밋에 포함할 파일 선택 |
| `git commit -m "..."` | 변경 사항을 기록 |
| `git push` | GitHub에 업로드 |

## 체크리스트

다음 항목을 확인하고 넘어갑니다.

- 로컬 작업 폴더가 준비됐다.
- `git remote -v`에서 GitHub 저장소가 보인다.
- 기본 브랜치가 `main`이다.
- `git status` 명령이 정상 실행된다.

## 자주 만나는 오류

**`fatal: destination path ... already exists`**

같은 이름의 폴더가 이미 있다는 뜻입니다. 다른 폴더 이름으로 클론하거나, 비어 있는 새 폴더에서 다시 시도합니다.

**`Could not resolve host: github.com`**

네트워크나 DNS 문제일 수 있습니다. 인터넷 연결을 확인하고 다시 실행합니다.

**인증을 요구하는 창이 뜹니다**

HTTPS로 push할 때 GitHub 로그인이 필요할 수 있습니다. GitHub Desktop, Git Credential Manager, GitHub CLI 중 하나로 인증해두면 편합니다.

## 다음 글

[Jekyll 테마 선택하고 기본 파일 만들기]({{ "/series/github-pages-jekyll/03-setup-jekyll-theme/" | relative_url }})
