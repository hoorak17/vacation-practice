# GitHub 사용법 실습 정리 (올리기 / 내리기 / 최초 업로드 / clone)

## 목적
GitHub와 로컬 PC를 연결하고  
코드를 **올리고(push)**, **내리고(pull/clone)**,  
**처음으로 GitHub에 업로드하는 과정**을 실습하며 정리한다.

이 문서 하나만 보면 다음을 다시 할 수 있도록 한다.
- GitHub 최초 업로드
- GitHub에서 프로젝트 내려받기(clone)
- push / pull 기본 흐름
- 중첩 저장소(.git 두 개) 방지

---

## 실습 환경
- Windows
- VS Code
- GitHub 개인 계정

---

## GitHub에 처음 코드 업로드하기 🏋️‍♂️ (최초 업로드)

> **이미 내 컴퓨터에 프로젝트 폴더가 있고,  
> 이걸 처음으로 GitHub repository에 올릴 때 사용하는 방법**

⚠️ 이 방법은 `git clone`과 다르다.  
- `git clone` : GitHub → 내 컴퓨터  
- 이 섹션 : **내 컴퓨터 → GitHub**

---

### 1️⃣ Git 저장소 초기화
```bash
git init
```

- 현재 폴더를 Git 저장소로 만든다
- `.git` 폴더가 생성된다

---

### 2️⃣ 업로드할 파일 추가
```bash
git add .
```

- `.`(점)은 **모든 파일**을 의미한다
- 특정 파일만 추가하고 싶다면:
```bash
git add index.html
```

---

### 3️⃣ 상태 확인 (선택)
```bash
git status
```

- 어떤 파일이 staging 상태인지 확인 가능

---

### 4️⃣ 히스토리(커밋) 생성
```bash
git commit -m "first commit"
```

- `-m`은 message의 약자
- `"first commit"`은 예시일 뿐, 아무 메시지나 가능

---

### 5️⃣ GitHub repository와 로컬 프로젝트 연결
```bash
git remote add origin https://github.com/hoorak17/vacation-practice.git
```

---

### 6️⃣ 연결 확인 (선택)
```bash
git remote -v
```

- 연결된 GitHub 주소가 출력되면 성공 🎇

---

### 7️⃣ GitHub로 최초 업로드
```bash
git push origin main
```

---

## GitHub ↔ 내 컴퓨터 연결 (clone)

> **아직 내 컴퓨터에 프로젝트가 없을 때만 사용**

### 올바른 사용 위치
- Desktop
- repos 폴더
- 아직 Git이 아닌 폴더

```bash
git clone https://github.com/hoorak17/vacation-practice.git
```

- 동일한 이름의 폴더가 생성된다
- `.git` 폴더가 자동으로 생성된다
- GitHub(origin)가 자동으로 연결된다

⚠️ **이미 `.git`이 있는 폴더(VS Code에서 연 프로젝트)에서 실행하면 중첩 저장소가 생긴다**

---

## GitHub에 올리기 (push)

> **이미 GitHub와 연결된 프로젝트에서 변경 사항 업로드**

```bash
git add .
git commit -m "커밋 메시지"
git push
```

---

## GitHub에서 내려받기 (pull)

> **이미 연결된 프로젝트에서 최신 변경 사항 가져오기**

```bash
git pull
```

---

## 실습 중 겪은 문제와 해결

### push가 거절되는 경우 (fetch first)
- GitHub repo를 먼저 만들고
- 로컬에서 `git init`을 따로 실행하면
- 서로 다른 히스토리가 생성되어 push가 거절된다

해결 방법:
```bash
git push origin master:main --force
```

---

### Pull Request(PR)가 뜨는 경우
- PR은 허가 요청이 아니다
- GitHub가 두 브랜치를 합칠지 안내하는 화면이다
- 개인 실습 repo에서는 무시해도 된다

---

### 파일이 안 올라간 것처럼 보이는 경우
```bash
git branch -M main
git push -u origin main
```

---

### Git 저장소 중첩 문제 (.git 두 개)
- repo 하위 폴더에서 다시 `git init` 또는 `git clone` 실행 시 발생
- 프로젝트당 `.git`은 하나만 존재해야 한다.

---
