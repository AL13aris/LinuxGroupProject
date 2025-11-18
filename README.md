# LinuxGroupProject

# 협업 시작 가이드 및 워크플로우

## 🌟 1. 프로젝트 시작 준비: 로컬 환경에 저장소 복제 (Clone)

모든 팀원은 이미 Git 설치 및 SSH 키 설정을 완료했다고 가정합니다. 아래 단계를 따라 GitHub의 중앙 저장소를 자신의 리눅스 로컬 환경으로 복제합니다.

### 1.1. 저장소 SSH 주소 확인 및 복사

가장 안전하고 편리한 SSH 방식을 사용하여 저장소 주소를 복사합니다.

- **GitHub 접속**: 웹 브라우저를 열어 LinuxGroupProject 저장소 페이지에 접속합니다.
- **주소 복사**:
  - `<> Code` (코드) 버튼을 클릭합니다.
  - SSH 탭을 선택합니다.
  - 표시된 주소(`git@github.com:AL13aris/LinuxGroupProject.git`)를 복사합니다.

### 1.2. 로컬 환경으로 저장소 복제 (Clone)

복사한 주소를 사용하여 저장소 전체를 자신의 리눅스 컴퓨터로 다운로드합니다.

```bash
# 1. 저장소를 다운로드할 원하는 디렉터리로 이동 (예: ~/Projects)
cd ~/Projects

# 2. 복사한 SSH 주소를 사용하여 저장소 복제 명령어 실행
git clone git@github.com:AL13aris/LinuxGroupProject.git

# 3. 프로젝트 폴더로 이동하여 작업 준비
cd LinuxGroupProject
```

**결과 확인**: 복제가 완료되면, 로컬 폴더에 처음에 관리자가 올린 README.md 파일이 포함된 main 브랜치의 내용이 그대로 복사됩니다.

### 1.3. 원격 연결 상태 확인

로컬 저장소가 원격(GitHub)과 올바르게 연결되었는지 확인합니다.

```bash
# 1. 원격 저장소 이름 확인 (기본적으로 'origin'으로 설정됨)
git remote -v
# 출력: origin  git@github.com:AL13aris/LinuxGroupProject.git (fetch)
#       origin  git@github.com:AL13aris/LinuxGroupProject.git (push)

# 2. 로컬/원격 브랜치 목록 확인
git branch -a
# 출력: 로컬 브랜치 'main'과 원격 추적 브랜치 'remotes/origin/main'이 보일 것입니다.
```

## 🚀 2. 협업 워크플로우: 기능 개발 및 기여 방법

**중요한 개발 규율**: 팀원 6명 모두 절대 main 브랜치에서 직접 작업하지 않습니다. 모든 작업은 새로운 **기능 브랜치 (Feature Branch)**에서 진행해야 합니다.

### 2.1. 새로운 기능 브랜치 생성 및 이동

자신이 맡은 작업이나 기능에 맞는 이름으로 브랜치를 생성하고 바로 이동합니다.

```bash
# 브랜치 이름 형식: feature/기능-설명-간단히 (예: feature/image-resize-function)
git checkout -b feature/새로운-브랜치-이름
```

### 2.2. 작업 수행, 추가 (Add), 커밋 (Commit)

코드 수정 작업을 완료한 후, 변경 사항을 로컬 저장소에 기록합니다.

```bash
# (자신의 기능을 구현하는 코드 수정 작업 수행)

# 1. 모든 변경 사항 스테이징 영역에 추가
git add .
# 또는 특정 파일만 추가: git add 파일명

# 2. 변경 사항 커밋 (커밋 메시지는 '유형: 설명' 형식 권장)
git commit -m "feat: 구현한 기능에 대한 명확한 설명"
```

### 2.3. 원격 저장소로 푸시 (Push)

로컬에 커밋된 내용을 원격(GitHub)의 자신의 브랜치로 업로드합니다.

```bash
# 자신의 브랜치를 원격(origin)으로 푸시
git push origin feature/새로운-브랜치-이름
```

### 2.4. Pull Request (PR) 요청 및 병합 (Merge)

GitHub 웹사이트를 통해 main 브랜치로 병합해 달라는 요청(Pull Request)을 생성합니다.

1. **GitHub 접속**: 브라우저에서 LinuxGroupProject 저장소 페이지로 이동합니다.
2. **Pull Request 생성**: 방금 푸시한 브랜치 이름 옆에 표시되는 "Compare & pull request" 버튼을 클릭하거나, Pull requests 탭으로 이동하여 새 PR을 생성합니다.
3. **대상 브랜치 확인**: **Base (대상)**는 main 브랜치, **Compare (소스)**는 작업 브랜치(feature/...)로 설정되었는지 확인합니다.
4. **코드 리뷰 요청**: PR 설명 작성 후, 팀원들에게 코드 리뷰를 요청하고 승인(Approve)을 받습니다.
5. **최종 병합**: 관리자(저장소 생성자)가 코드 리뷰를 확인하고 최종적으로 main 브랜치로 병합(Merge)합니다.

## 💡 3. 다음 작업 시작: main 브랜치 동기화

PR이 승인되고 main에 병합된 후, 다음 작업을 시작하기 전에는 반드시 main 브랜치로 돌아와 최신 변경 사항을 받아와야 합니다.

```bash
# 1. main 브랜치로 이동
git checkout main

# 2. 원격 main의 최신 내용을 로컬로 가져와 동기화
git pull origin main

# 3. 새로운 작업을 위해 2.1 단계부터 다시 시작합니다.
git checkout -b feature/다음-새로운-작업
```
