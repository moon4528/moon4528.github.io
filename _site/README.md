# moon4528.github.io

# moon4528.github.io

GitHub Pages와 Jekyll을 사용해 운영하는 개인 개발 블로그입니다.

백엔드 개발 과정에서 학습한 내용, 프로젝트 경험, 문제 해결 과정과 기술 관련 기록을 정리합니다.

## 블로그 주소

- GitHub Pages: https://moon4528.github.io
- 로컬 미리보기: http://localhost:4000

---

## 기술 구성

- GitHub Pages
- Jekyll
- Ruby
- Bundler
- Markdown
- Git / GitHub

---

## 프로젝트 구조

```text
moon4528.github.io/
├── _config.yml
├── _posts/
│   └── YYYY-MM-DD-post-title.md
├── assets/
│   ├── css/
│   └── images/
├── about.md
├── index.md
├── Gemfile
├── Gemfile.lock
└── README.md
```

각 파일과 디렉터리의 역할은 다음과 같습니다.

| 경로 | 설명 |
|---|---|
| `_config.yml` | 블로그 제목, 설명, 테마 등 Jekyll 전체 설정 |
| `_posts/` | 블로그 게시글을 저장하는 디렉터리 |
| `assets/css/` | 사용자 정의 CSS 또는 SCSS 파일 |
| `assets/images/` | 게시글과 페이지에서 사용하는 이미지 |
| `index.md` | 블로그 메인 페이지 |
| `about.md` | 블로그 또는 작성자 소개 페이지 |
| `Gemfile` | 블로그 실행에 필요한 Ruby 패키지 정의 |
| `Gemfile.lock` | 실제 설치된 Ruby 패키지 버전 정보 |
| `README.md` | 저장소와 블로그 사용 방법 설명 |

---

## 사전 준비

로컬에서 블로그를 실행하려면 다음 프로그램이 필요합니다.

- Git
- Ruby
- RubyGems
- Bundler

설치 여부는 PowerShell에서 확인할 수 있습니다.

```powershell
git --version
ruby -v
gem -v
bundle -v
```

Ruby는 Windows용 `Ruby+Devkit x64` 버전을 사용합니다.

RubyInstaller 설치 후에는 MSYS2 및 MINGW 개발 도구도 함께 설치해야 합니다.

---

## 저장소 내려받기

저장소를 처음 내려받는 경우 다음 명령어를 사용합니다.

```powershell
git clone https://github.com/moon4528/moon4528.github.io.git
```

저장소 디렉터리로 이동합니다.

```powershell
cd moon4528.github.io
```

현재 위치가 올바른지 확인합니다.

```powershell
Get-Location
```

파일 목록을 확인합니다.

```powershell
dir
```

---

## 의존성 설치

프로젝트 루트 디렉터리에서 다음 명령어를 실행합니다.

```powershell
bundle install
```

이 명령어는 `Gemfile`에 정의된 Jekyll과 GitHub Pages 관련 패키지를 설치합니다.

설치가 완료되면 다음과 유사한 메시지가 출력됩니다.

```text
Bundle complete!
```

의존성을 변경하지 않았다면 이후에는 매번 `bundle install`을 실행할 필요가 없습니다.

다음과 같은 경우 다시 실행합니다.

- 저장소를 처음 clone한 경우
- `Gemfile`을 수정한 경우
- `Gemfile.lock`이 변경된 경우
- 필요한 gem이 설치되어 있지 않은 경우

---

## 로컬 서버 실행

프로젝트 루트에서 다음 명령어를 실행합니다.

```powershell
bundle exec jekyll serve --livereload
```

정상적으로 실행되면 다음과 유사한 주소가 표시됩니다.

```text
Server address: http://127.0.0.1:4000/
```

브라우저에서 다음 주소로 접속합니다.

```text
http://localhost:4000
```

`--livereload` 옵션을 사용하면 파일 저장 시 Jekyll이 변경 내용을 다시 빌드합니다.

브라우저가 자동으로 새로고침되지 않는 경우 직접 새로고침합니다.

로컬 서버를 종료하려면 서버를 실행한 PowerShell에서 다음 키를 누릅니다.

```text
Ctrl + C
```

---

## 게시글 작성 방법

게시글은 `_posts` 디렉터리에 Markdown 파일로 작성합니다.

파일 이름은 반드시 다음 형식을 사용합니다.

```text
YYYY-MM-DD-post-title.md
```

예시:

```text
_posts/2026-07-28-github-pages-start.md
```

파일명에는 가급적 다음 규칙을 적용합니다.

- 날짜는 `연도-월-일` 형식으로 작성
- 제목은 영문 소문자 사용 권장
- 단어 사이는 하이픈 `-`으로 구분
- 공백과 한글 파일명은 가급적 피하기

---

## 게시글 기본 양식

```markdown
---
layout: post
title: "게시글 제목"
date: 2026-07-28 16:00:00 +0900
categories: backend
tags: [Spring Boot, Java]
---

## 개요

게시글에서 다룰 내용을 간단하게 작성합니다.

## 문제 상황

어떤 문제를 해결하려 했는지 작성합니다.

## 원인 분석

문제가 발생한 원인과 확인 과정을 작성합니다.

## 해결 방법

적용한 해결 방법을 작성합니다.

## 구현 내용

필요한 코드와 설정 내용을 작성합니다.

## 결과

해결 결과와 확인 내용을 작성합니다.

## 회고

작업을 통해 배운 점과 향후 개선 사항을 작성합니다.
```

---

## 게시글 Front Matter

게시글 상단의 `---` 사이 영역을 Front Matter라고 합니다.

```yaml
---
layout: post
title: "게시글 제목"
date: 2026-07-28 16:00:00 +0900
categories: backend
tags: [Spring Boot, Java]
---
```

각 속성의 의미는 다음과 같습니다.

| 속성 | 설명 |
|---|---|
| `layout` | 게시글에 사용할 레이아웃 |
| `title` | 게시글 제목 |
| `date` | 게시글 작성 날짜와 시간 |
| `categories` | 게시글의 큰 분류 |
| `tags` | 게시글에 사용한 기술이나 세부 주제 |

한국 시간은 다음과 같이 `+0900`을 사용합니다.

```yaml
date: 2026-07-28 16:00:00 +0900
```

---

## Markdown 작성 방법

### 제목

```markdown
# 제목 1
## 제목 2
### 제목 3
```

### 강조

```markdown
**굵은 글씨**

*기울임 글씨*

`인라인 코드`
```

### 목록

```markdown
- 항목 1
- 항목 2
- 항목 3
```

```markdown
1. 첫 번째
2. 두 번째
3. 세 번째
```

### 링크

```markdown
[GitHub](https://github.com)
```

### 인용문

```markdown
> 인용하거나 강조할 내용을 작성합니다.
```

### 코드 블록

백틱 세 개 뒤에 언어 이름을 작성합니다.

````text
```java
@RestController
public class HelloController {

    @GetMapping("/hello")
    public String hello() {
        return "Hello";
    }
}
```