# GitHub 사용법 실습 정리 (올리기 / 내리기 / 연결)

## 목적
GitHub와 로컬 PC를 연결하고  
코드를 올리고(push), 내리고(pull/clone) 하는 기본 흐름을 익힌다.  
실습 중 겪은 문제들과 해결 방법을 함께 정리한다.

---

## 실습 환경
- Windows
- PowerShell / Git Bash
- GitHub 개인 계정

---

## GitHub ↔ 내 컴퓨터 연결 (최초 1회)

### 권장 방법: GitHub에서 내려받으며 시작
```bash
git clone https://github.com/hoorak17/vacation-practice.git
```

- 동일한 이름의 폴더가 생성된다
- `.git` 폴더가 자동으로 생성된다
- GitHub(origin)가 자동으로 연결된다

---

## GitHub에 올리기 (push)
```bash
git add .
git commit -m "커밋 메시지"
git push
```

---

## GitHub에서 내려받기 (pull)
```bash
git pull
```

---

## GitHub에서 처음 내려받기 (clone)
```bash
git clone <GitHub_저장소_URL>
```

- 최초 1회만 사용
- 이후에는 `git pull`만 사용

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
- repo 하위 폴더에서 다시 `git init`을 실행하면 발생한다
- 프로젝트당 `.git`은 하나만 존재해야 한다

---

## 핵심 요약
- 처음 연결: `git clone`
- 올리기: `git add → git commit → git push`
- 내리기: `git pull`
