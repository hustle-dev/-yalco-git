# yalco-git

인프런의 [제대로 파는 Git &amp; Github - by 얄코](https://www.inflearn.com/course/%EC%A0%9C%EB%8C%80%EB%A1%9C-%ED%8C%8C%EB%8A%94-%EA%B9%83/dashboard)를 보고 학습하는 레포지토리입니다.

![](https://cdn.inflearn.com/public/files/pages/bb66ff7b-0d11-4735-8ac8-8a6360bd5b94/%EA%B0%95%EC%9D%98%201.png)

## Git 시작하기

### Git을 배워야 하는 이유

프로젝트의 **시간**과 **차원**을 관리

- 시간: 프로젝트의 버전을 과거로 되돌리거나 특정 내역 취소 가능

- 차원: 프로젝트의 여러 모드를 쉽게 전환하고 관리

### 강의를 위한 설치와 세팅(맥)

1. Git 설치

```bash
brew install git
```

2. SourceTree 설치

https://www.sourcetreeapp.com/

3. vscode 설치

https://code.visualstudio.com/

4. iterm2 설치

https://www.yalco.kr/_03_mac_terminal/

협업시 윈도우와 맥에서 엔터 방식 차이로 인한 오류 방지를 위해 아래 명령어 입력

```bash
git config --global core.autocrlf input
```

### CLI vs GUI. 무엇을 사용해야 할까요?

얄코의 경우

- git에서 뭔가를 실행하기 위한 어떤 명령들을 사용하는 경우 -> CLI

- 프로젝트의 상태를 Git상에서 자세히 살펴보아야 할 때는 -> GUI(소스트리 사용)

> 공부할때는 CLI로 학습하는것이 좋다.

### Git 설정 & 프로젝트 관리 시작하기

1. Git 최초 설정

Git 전역으로 사용자 이름과 이메일 주소를 설정

```bash
git config --global user.name "(본인 이름)"
```

```bash
git config --global user.email "(본인 이메일)"
```

**기본 브랜치명 변경**

```bash
git config --global init.defaultBranch main
```

> main으로 브랜치명을 변경하자.

2. 프로젝트 생성 & Git 관리 시작

원하는 폴더에서 아래의 명령어 입력

```bash
git init
```

> 그러나 나는 이미 github에 레포를 만들었기 때문에 git clone으로 자동으로 생성

파일 생성후 아래의 명령어를 입력하면 현재 상태 확인 가능

```bash
git status
```

3. 소스트리로 해보기

소스트리에서 git init 명령어를 gui로 할 수 있는데 그냥 명령어로 치는게 빠름

소스트리에서 GUI로 현재 상태가 어떤지 확인할 수 있음

### Git에게 맡기지 않을 것들

- 포함할 필요가 없을 때

  - 자동으로 생성 또는 다운로드되는 파일들 (빌드 결과물, 라이브러리)

- 포함하지 말아야 할 때
  - 보안상 민감한 정보를 담은 파일

**.gitignore 사용**

파일 생성 후, `secrets.yaml ` 입력

## 시간 여행하기

### 변화를 타임캡슐에 담아 묻기

1. 프로젝트의 변경 사항들을 타임 캡슐(버전)에 담기

변경사항 확인

```bash
git status
```

> 추적하지 않는(untracked) 파일: Git의 관리에 들어간 적 없는 파일

파일 하나 담기

```bash
git add tigers.yaml
```

모든 파일 담기

```bash
git add .
```

2. 타임캡슐 묻기

```bash
git commit
```

3. 다음 변경사항들을 만들고 타임캡슐 묻기

파일 삭제및 변경 추가 한 후, `git status`와 `git diff`로 확인해볼 수 있다.

add와 commit을 한번에 할 수 있다.

```bash
git commit -am "(메시지)"
```

> 📍 단 새로 추가된(untracked) 파일이 없을 때 한정

이후 실습 진행

### 과거로 돌아가는 두 가지 방법

- reset: 원하는 시점으로 돌아간 뒤 이후 내역들을 지운다.

> 즉, 히스토리를 지우게 됨

- revert: 되돌리기 원하는 시점의 커밋을 거꾸로 실행한다.

> 히스토리를 하나하나 남길 필요가 있을 때, 이 방식을 사용!

### 과거로 돌아가기 실습

reset, revert 실습진행

```bash
git reset --hard
```

> 이를 사용하면 현재 작업 위치인 HEAD의 포인터를 특정 위치로 변경할 수 있다.

> 즉 워킹 디렉토리까지 업데이트 한다는 의미

## 차원 넘나들기

### 여러 branch 만들어보기

branch: 분기된 가지(다른 차원)

사용 이유

- 프로젝트를 여러개로 관리해야할 때

  - 예) 배포용, 테스트용, 새로운 기능 추가용

- 여러 작업들이 각각 독립되어 진행될 때

  - 예) 신기능1, 신기능2, 코드개선, 긴급수정..
  - 각각의 차원에서 작업한 뒤 확정된 것을 메인 차원에 통합

`add-coach`란 브랜치 생성

```bash
git branch add-coach
```

브랜치 목록 확인

```bash
git branch
```

`add-coach` 브랜치로 이동

```bash
git switch add-coach
```

브랜치 생성과 동시 이동

```bash
git switch -c new-teams
```

브랜치 삭제

```bash
git branch -d (삭제할 브랜치명)
```

다른 브랜치로 가져오지 않은 내용이 있는 브랜치를 지우는 경우 `-D` 사용

```bash
git branch -D (강제삭제할 브랜치명)
```

CLI에서 여러 브랜치의 내역 편리하게 보는 방법

```bash
git log --all --decorate --oneline --graph
```

> 근데 GUI환경인 소스트리가 있으므로 이런것을 확인하고 싶을때는 그냥 gui켜서 확인하는 것이 좋다.

### branch를 합치는 두 가지 방법

- merge: 두 브랜치를 한 커밋에 이어붙인다.

> 즉, 새로운 커밋이 생기는것

- rebase: 브랜치를 다른 브랜치에 이어붙인다.

> 현재 작업중인 브랜치를 다른 브랜치에 하나 하나 커밋한 것처럼 추가한다.

merge는 브랜치 히스토리가 남지만, rebase는 브랜치 히스토리가 남지 않는다.

> 팀원들과 협업하는 경우 rebase를 사용하지 않는것이 좋다고함.

### branch 합치기 실습

### 충돌 해결하기

merge와 rebase를 활용하여 실습진행

## GitHub 사용하기

### push와 pull

push 할 것이 있을 시 pull 하는 두 가지 방법

- `git pull --no-rebase` -> merge 방식

- `git pull --rebase` -> rebase 방식
  > 협업시 사용 OK(보통 협업할 때는 브런치를 만들어서 작업하기에 rebase를 잘 사용하지 않음. 그러나 단순히 push하기 전 rebase는 ㄱㅊ)

원격 저장소에 문제가 생겨서 로컬의 것으로 강제 push를 하기 위해선 아래의 명령어를 사용할 수 있음

```bash
git push --force
```

### 원격의 브랜치 다루기

로컬에서 `from-local` 이라는 브랜치를 만들고, 원격에 다음의 명령어로 브랜치를 생성할 수 있다.

```bash
git push -u origin from-local
```

브랜치 목록을 살펴보는 방법으로 아래의 명령어를 사용할 수 있다.

```bash
git branch --all
```

**원격의 브랜치 로컬에 받아오기**

github에서 `from-remote` 브랜치 만들기

이후 아래 명령어로 변경사항 확인

```bash
git fetch
```

아래 명령어로 로컬에 같은 이름의 브랜치를 생성하여 연결하고 switch

```bash
git switch -t origin/from-remote
```

**원격의 브랜치 삭제**

```bash
git push (원격 이름) --delete (원격의 브랜치명)
```

## Git 보다 깊이 알기

## 프로답게 커밋 관리하기

## 취소와 되돌리기 보다 깊이 알기

## 태그

## Branch 보다 깊이 알기

## 분석하고 디버깅 하기

## Git의 추가 기능들

## GitHub 잘 활용하기

## GitHub 제대로 활용하기
