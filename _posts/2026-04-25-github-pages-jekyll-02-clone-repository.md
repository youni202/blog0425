---
layout: default
title: "2. 로컬에 저장소 클론하고 첫 커밋 준비하기"
date: 2026-04-25 00:20:00 +0900
nav_exclude: true
permalink: /series/github-pages-jekyll/02-clone-repository/
---

# 2. 로컬에 저장소 클론하고 첫 커밋 준비하기

이 글에서는 GitHub에서 만든 저장소를 내 컴퓨터로 가져오고, 앞으로 글과 설정 파일을 관리할 작업 폴더를 준비합니다.

## 목표

원격 저장소를 로컬 폴더에 클론하고, Git 커밋과 푸시가 가능한 상태를 만듭니다.

## 클론하기

작업할 폴더에서 다음 명령을 실행합니다.

```sh
git clone https://github.com/username/repository-name.git
```

특정 폴더 안에 바로 클론하고 싶다면 마지막에 폴더 이름을 붙입니다.

```sh
git clone https://github.com/username/repository-name.git myblog
```

이미 비어 있는 폴더 안에 저장소 내용을 바로 넣고 싶다면 다음처럼 실행할 수 있습니다.

```sh
git clone https://github.com/username/repository-name.git .
```

## 상태 확인

```sh
git status
git remote -v
```

`origin`이 GitHub 저장소 URL을 가리키면 연결이 잘 된 것입니다.

## 첫 커밋 준비

이후 글에서는 Jekyll 설정 파일을 추가한 뒤 다음 흐름으로 저장합니다.

```sh
git add .
git commit -m "Set up Jekyll site"
git push
```

## 다음 글

[Jekyll 테마 선택하고 기본 파일 만들기]({{ "/series/github-pages-jekyll/03-setup-jekyll-theme/" | relative_url }})
