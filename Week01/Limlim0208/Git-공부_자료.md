# 공부 자료

---

[교육 목표]

1. Git의 개념과 이해
2. Git의 핵심 구조 및 흐름
3. 브랜치
4. 협업 시 필요한 기본 명령어

---

## 0. 문제 상황

소프트웨어 개발에서는 파일이 계속 수정됨

하지만 파일을 계속 복사해서 관리하면 시간이 지날수록 관리가 매우 어려워짐

예를 들어 프로그램 하나를 만든다고 가정

```jsx
프로그램_v1
프로그램_v2
프로그램_v3
프로그램_최종
프로그램_최종_진짜
프로그램_최종_진짜_수정
```

**버전 관리를 체계적으로 하지 않을 때 생기는 문제**

- 어떤 파일이 최신인지 모른다
- 누가 무엇을 수정했는지 모른다
- 이전 상태로 되돌리기 어렵다
- 여러 사람이 동시에 작업하면 파일이 충돌한다

이 문제를 해결하기 위해 **버전 관리 시스템(Version Control System)**이 등장

### 버전 관리 시스템이란?

파일 변화를 시간에 따라 기록했다가 나중에 특정 시점의 버전을 다시 꺼내올 수 있는 시스템

그 중 가장 널리 사용되는 시스템이 **Git**

---

## 1. Git이란?

> **Distributed Version Control System = 분산형 버전 관리 시스템**
> 

Git은 빠르고 효율적으로 파일 변경 이력을 관리하는 도구이자, 
여러 사람들이 동시에 안전하게 협업할 수 있게 해주는 무료 오픈소스 분산 버전 관리 시스템이다.

- 누가 언제 무엇을 수정했는지 기록
- 이전 버전으로 언제든 되돌리기 가능
- 여러 사람이 동시에 개발 가능
- 코드 변경 내역을 안전하게 관리

### 버전이란?

- 소프트웨어나 문서의 특정 시점 상태
- 버전을 기록함으로써 다양한 실험이나 기능 개발을 독립적으로 진행할 수 있음

### **버전 관리란?**

- 소스 코드나 문서 등의 변경 사항을 추적하고 기록하는 시스템
- 모든 변경 내역을 기록, 파일의 현재 상태뿐만 아니라 과거의 상태도 관리가 가능, 쉽게 이전 상태로 되돌릴 수 있음
- 버전 관리를 통해 협업 과정에서 누가, 언제, 무엇을 수정했는지를 추적할 수 있음

→ 안전하게 코드를 관리할 수 있음

**Git의 버전 관리 방식**

Git은 파일의 변경 사항을 기록하는 방식으로 스냅샷을 사용

- **스냅샷**이란?
    - 특정 시점의 파일 및 디렉토리 상태를 캡처한 것
- Git은 매 커밋마다 프로젝트 상태를 스냅샷처럼 저장한다.
- 스냅샷을 통해 프로젝트의 모든 변경 사항을 기록하고, 필요시 언제든지 해당 시점으로 돌아갈 수 있음

각 파일에 대한 변화를 저장하는 시스템

![출처 [https://git-scm.com/book/ko/v2/시작하기-Git-기초](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EA%B8%B0%EC%B4%88)](images\image1.png)

출처 [https://git-scm.com/book/ko/v2/시작하기-Git-기초](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EA%B8%B0%EC%B4%88)

시간순으로 프로젝트의 스냅샷을 저장(Git 방식)

![출처 [https://git-scm.com/book/ko/v2/시작하기-Git-기초](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EA%B8%B0%EC%B4%88)](images\image2.png)

출처 [https://git-scm.com/book/ko/v2/시작하기-Git-기초](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EA%B8%B0%EC%B4%88)

**버전 관리를 통해 얻고자 하는 것**

![images\image3.png](images\image3.png)

⇒ 파일의 변경 사항을 체계적으로 기록하고 관리하여 과거로 돌아가거나, 여러 사람의 작업을 병합하는 과정을 돕는 것

<aside>

한 줄 정리:

**파일의 변경 이력을 기록하고 필요할 때 이전 상태로 되돌릴 수 있게 관리하는 시스템**

</aside>

### 분산 버전 관리 시스템이란?

`Distributed Version Control System = Distributed VCS`

- 각 개발자가 **전체 저장소(코드 + 변경 이력)를 로컬에 모두 복제**해서 작업하는 구조

→ 즉, 중앙 서버에만 기록이 있는 것이 아니라, 모든 팀원이 전체 프로젝트의 버전 기록을 가지고 있어 각자의 로컬에서 작업이 가능하다

![[https://git-scm.com/book/ko/v2/시작하기-버전-관리란%3F](https://git-scm.com/book/ko/v2/%ec%8b%9c%ec%9e%91%ed%95%98%ea%b8%b0-%eb%b2%84%ec%a0%84-%ea%b4%80%eb%a6%ac%eb%9e%80%3F)](images\image4.png)

[https://git-scm.com/book/ko/v2/시작하기-버전-관리란%3F](https://git-scm.com/book/ko/v2/%ec%8b%9c%ec%9e%91%ed%95%98%ea%b8%b0-%eb%b2%84%ec%a0%84-%ea%b4%80%eb%a6%ac%eb%9e%80%3F)

장점:

- 서버에 문제가 생겨도 각자의 로컬 저장소에 버전이 보관되어 있으므로 복구 가능
- 인터넷이 없어도 로컬에서 커밋, 브랜치 등 대부분의 작업 가능
- 여러 사용자가 동시에 작업하고, 각자의 작업을 병합하는 과정이 유연함
- 협업이 필요할 때는 중앙 서버나 다른 사용자의 저장소와 동기화함

<aside>

한 줄 정리:

**모든 개발자가 동일한 저장소의 복사본을 가지고 독립적으로 작업하는 구조**

즉, 여러 개발자가 협업 시에 한 코드를 가지고 병렬적으로 진행할 수 있도록 해준다.

</aside>

### GitHub란?

**Git 저장소를 올려두는 웹 서비스(플랫폼)**

- git 저장소를 원격 저장하고 관리
- 협업 기능을 제공 (PR, Issue, Code Review)
- CI/CD, 테스트 및 배포 등 자동화 워크 플로우 기능 제공
- 웹에서 코드 확인 가능

→ Git으로 관리한 코드를 인터넷에 올려서 협업하는 공간

## 2. Git의 핵심 구조 및 흐름

Git은 다음 3단계 구조를 통해 변경 내용을 관리함

```jsx
Working Directory
        ↓
     Staging Area
        ↓
      Repository
```

Git에서 각 파일은 4가지 상태로 관리된다.

1. Untracked(추적되지 않음): Git이 아직 관리(추적)하지 않는 파일 (보통 새로 만든 파일)
2. Modified(수정됨): 파일이 수정되었으나, 아직 커밋으로 저장되지 않음
3. Staged(스테이징됨): 다음 커밋에 포함될 예정 (커밋할 파일로 선택된 상태)
4. Committed(커밋됨): 커밋으로 저장 완료 (버전으로 기록됨)
5. 

![출처: [https://whdrns2013.github.io/vcs/20241129_003_git_working_dir_stage_repository/](https://whdrns2013.github.io/vcs/20241129_003_git_working_dir_stage_repository/)](images\image5.png)

출처: [https://whdrns2013.github.io/vcs/20241129_003_git_working_dir_stage_repository/](https://whdrns2013.github.io/vcs/20241129_003_git_working_dir_stage_repository/)

이에 따라 Git 프로젝트는 [로컬]( = 내 노트북, 컴퓨터)에서는 세 가지 공간으로 상태를 관리함

1. 작업 디렉토리(Working Directory): **현재 작업 중인 파일이 있는 공간**
    - 내 컴퓨터에서 실제로 파일을 만들고/수정하는 공간
    - 아직 커밋으로 저장되지 않은 변경 사항이 있는 곳
    - 파일을 새로 생성하거나 수정하면, Git이 이를 감지
    - `git add`로 스테이징 영역으로 보낼 파일을 선택함
2. 스테이징 영역(Staging Area): **Commit을 하기 전에 파일을 준비하는 공간**
    - 커밋할 준비가 된 파일을 임시로 보관하는 공간
    - `git add`명령어로 수정된 파일을 스테이징
    - 커밋할 파일만 선택적으로 준비 가능
    - 이 단계에서는 아직 Git 기록에 저장되지 않음
3. 저장소(Repository): **Git의 실제 기록이 저장되는 공간**
    - `git commit` 명령어로 스테이징 영역에 있는 파일이 Git 기록으로 저장
    - 커밋된 파일은 프로젝트의 버전으로 기록됨
    - 저장소는 모든 커밋 기록을 보관하고 관리
    - 크게 두 가지 저장소를 사용
        
        
        | 저장소 | 설명 |
        | --- | --- |
        | Local Repository | 내 컴퓨터에 있는 Git 저장소 |
        | Remote Repository | 서버에 있는 Git 저장소 |
4. 원격 저장소(remote) [push 후] : 서버에 있는 Git 저장소
    - `git push` 명령어로 github 원격 저장소에 파일들을 저장
    - 인터넷 연결이 필요한 서버 저장소
    - 모든 작업자의 push된 코드를 모아두는 저장소

![images\image6.png](images\image6.png)

[핵심 흐름]

**코드 추가 및 수정 → add → commit → push**

### 협업에서 발생할 수 있는 문제: 충돌(Conflict)

- 팀원 A와 B가 같은 파일을 수정
- A가 먼저 push
- B가 pull 없이 push 시도

→ Git은 어떤 변경 내용을 우선 적용해야 하는지 자동으로 판단할 수 없는 상황

→ 이를 충돌(conflict)이라고 한다.

**충돌이 발생하는 상황**

1. 같은 파일을 여러 사람이 수정
2. 같은 위치의 코드를 수정
3. 서로 다른 브랜치에서 동일한 부분 변경

## 3. 브랜치(branch)란?

> 하나의 프로젝트 안에서 작업 흐름을 나누는 독립된 작업 공간
> 

![images\image7.png](images\image7.png)

이미지 출처: [[Git] 브랜치란? 초보자도 쉽게 이해하는 Git branch 개념](https://code-lab.tistory.com/entry/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98%EB%9E%80-%EC%B4%88%EB%B3%B4%EC%9E%90%EB%8F%84-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EB%8A%94-Git-branch-%EA%B0%9C%EB%85%90#google_vignette)

- 말 그대로 “가지”, 즉 코드의 작업 분기를 의미함
- 나무의 줄기에서 여러 갈래의 가지가 뻗어나오는 것처럼, 하나의 메인 프로젝트가 여러 갈래로 갈라져 나와 각자만의 버전 이력을 만들어 관리할 수 있음.
- 이 브랜치 덕분에 다양한 작업을 독립적으로 진행할 수 있고, 각각의 작업이 프로젝트 전체에 영향을 주지 않도록 관리할 수 있다.

즉, Git의 기본 기능은 **시간** 흐름에 따라 버전을 기록하는 것이고, 브랜치 기능을 통해 그 흐름을 여러 갈래로 나누는 것이다.

## 4. Git 기본 명령어

### 자주 사용하는 git 필수 명령어

- **Git 저장소 생성** `git init`
    
    현재 디렉토리를 Git 저장소로 초기화
    
    → `.git` 폴더가 생성되고  Git이 해당 폴더의 파일 변화를 추적하기 시작
    
- **저장소 복제 및 다운로드** `git clone`
    
    원격 저장소를 복사하여 내 컴퓨터에 가져오는 명령어
    
    → 이미 존재하는 프로젝트를 그대로 내려받을 때 사용
    
- **파일 추가** `git add`
    
    수정한 파일을 **staging area**에 올리는 명령어
    
    → 다음 커밋에 포함될 파일을 선택
    
- **Commit 생성** `git commit`
    
    **staging area**에 있는 파일들을 Git 기록으로 저장하는 명령어
    
    → 하나의 버전으로 현재 작업 상태를 기록
    
- **변경 사항 원격 서버 업로드** `git push`
    
    로컬 저장소의 커밋을 원격 저장소(GitHub)로 업로드하는 명령어
    
    → 팀원들과 변경 내용을 공유
    
- **원격 저장소의 변경 내용을 현재 디렉토리로 가져오기** `git pull`
    
    원격 저장소의 최신 변경 내용을 가져와 로컬에 반영하는 명령어
    
- **브랜치** `git branch`
    
    브랜치를 생성, 삭제, 조회하는 명령어.
    
    → 작업 흐름을 나누기 위해 사용한다.
    
- **브랜치 병합** `git merge`
    
    다른 브랜치의 변경 내용을 현재 브랜치에 합치는 명령어.
    

**Git 기본 작업 흐름**

```
clone → pull → 수정 → add → commit → push
```

---

## **출처**

Git이란? https://wikidocs.net/332810

버전 관리란? https://git-scm.com/book/ko/v2/%ec%8b%9c%ec%9e%91%ed%95%98%ea%b8%b0-%eb%b2%84%ec%a0%84-%ea%b4%80%eb%a6%ac%eb%9e%80%3F

스냅샷 https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EA%B8%B0%EC%B4%88

GitHub란? https://docs.github.com/ko/get-started/start-your-journey/what-is-github

충돌 개념 https://wikidocs.net/332848

Git 구조 https://wikidocs.net/332829