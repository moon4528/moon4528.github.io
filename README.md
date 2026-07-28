# moon4528.github.io

GitHub Pages와 Jekyll을 사용해 운영하는 개인 개발 블로그입니다.

백엔드 개발 과정에서 학습한 내용, 프로젝트 경험, 설계 결정, 트러블슈팅 기록을 프로젝트와 개발자 노트 구조로 나누어 정리합니다.

## 블로그 주소

- GitHub Pages: https://moon4528.github.io
- 로컬 미리보기: http://localhost:4000

## 기술 구성

- GitHub Pages
- Jekyll
- Ruby
- Bundler
- Markdown
- SCSS

## 현재 구조

```text
moon4528.github.io/
├── _config.yml
├── _layouts/
│   ├── default.html
│   ├── document.html
│   ├── home.html
│   ├── page.html
│   └── post.html
├── _projects/
│   └── bitepick/
│       ├── overview.md
│       ├── architecture.md
│       ├── retrospective.md
│       └── work/
│           └── 2026-07-28-infra.md
├── _notes/
│   └── developer-notes/
│       ├── network/
│       │   └── http-cache.md
│       └── os/
│           └── process-thread.md
├── _posts/
│   └── YYYY-MM-DD-post-title.md
├── assets/
│   └── css/
│       └── style.scss
├── about.md
├── index.md
├── projects.md
├── notes.md
├── Gemfile
├── Gemfile.lock
└── README.md
```

## 디렉터리 역할

| 경로 | 설명 |
|---|---|
| `_config.yml` | 사이트 제목, 설명, 컬렉션, permalink, 기본 레이아웃 설정 |
| `_layouts/` | 사이트 공통 화면, 홈, 문서, 일반 페이지, 포스트 레이아웃 |
| `_projects/` | 프로젝트별 문서 컬렉션 |
| `_notes/` | OS, Network, Cloud, Develop 등 개발자 노트 컬렉션 |
| `_posts/` | 날짜 기반 일반 블로그 포스트 |
| `assets/css/style.scss` | 전체 디자인과 반응형 스타일 |
| `index.md` | 메인 페이지 |
| `projects.md` | 프로젝트 목록 페이지 |
| `notes.md` | 개발자 노트 목록 페이지 |
| `about.md` | 작성자 소개 페이지 |
| `_site/` | Jekyll 빌드 결과물 |

## 콘텐츠 관리 방식

### 프로젝트 문서

프로젝트는 `_projects/{project-name}/` 아래에 작성합니다.

권장 구조:

```text
_projects/
└── project-name/
    ├── overview.md
    ├── architecture.md
    ├── retrospective.md
    └── work/
        └── YYYY-MM-DD-work-title.md
```

프로젝트 문서 기본 양식:

```markdown
---
title: 프로젝트 문서 제목
project: ProjectName
section: overview
order: 1
summary: 목록과 홈에 표시할 짧은 설명
---

## 개요

문서 내용을 작성합니다.
```

`section`은 문서 성격에 맞게 사용합니다.

- `overview`: 프로젝트 개요와 소개
- `architecture`: 시스템 설계와 아키텍처
- `work`: 작업 기록
- `retrospective`: 회고

### 개발자 노트

기술 학습 내용은 `_notes/developer-notes/{category}/` 아래에 작성합니다.

권장 구조:

```text
_notes/
└── developer-notes/
    ├── os/
    ├── network/
    ├── cloud/
    └── develop/
```

개발자 노트 기본 양식:

```markdown
---
title: 노트 제목
category: Network
topic: HTTP
summary: 목록에 표시할 짧은 설명
---

## 핵심 질문

- 정리할 질문을 작성합니다.
```

### 일반 포스트

날짜 기반의 일반 블로그 글은 `_posts/` 아래에 작성합니다.

```text
_posts/YYYY-MM-DD-post-title.md
```

기본 양식:

```markdown
---
layout: post
title: "게시글 제목"
date: 2026-07-28 16:00:00 +0900
categories: backend
tags: [Spring Boot, Java]
---

## 개요

게시글 내용을 작성합니다.
```

## 로컬 실행

처음 실행할 때 의존성을 설치합니다.

```powershell
bundle install
```

로컬 서버를 실행합니다.

```powershell
bundle exec jekyll serve --livereload
```

브라우저에서 접속합니다.

```text
http://localhost:4000
```

Windows에서 `bundle`이 PATH에 잡히지 않는 경우 Ruby 설치 경로의 실행 파일을 직접 사용할 수 있습니다.

```powershell
C:\Ruby33-x64\bin\bundle.bat install
C:\Ruby33-x64\bin\jekyll.bat serve --livereload
```

## 빌드 확인

정적 파일 생성이 정상 동작하는지 확인합니다.

```powershell
bundle exec jekyll build
```

Windows에서 PATH 문제가 있으면 다음 명령을 사용합니다.

```powershell
C:\Ruby33-x64\bin\jekyll.bat build
```

## 디자인 방향

현재 디자인은 심플한 모던 블로그를 기준으로 구성되어 있습니다.

- 작은 글자 크기와 여백 중심의 레이아웃
- 파스텔 계열 배경과 카드 색상
- 프로젝트와 노트 구조를 보여주는 홈 화면
- 모바일에서도 한 줄씩 읽히는 반응형 목록

전체 스타일은 `assets/css/style.scss`에서 관리합니다.
