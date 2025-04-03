# team-collabo-usefork
팀협업가이드-fork 사용 방식

## 구조
Base Remote (upstream) - 원본 레파지토리
- main 

Forked Remote (origin) - 각자 포크해간 레파지토리
- main (develop)
- feature_기능1
- feature_기능2
- bug_기능1
- ...

## 흐름
### 초기세팅 
1. Base Remote main 브랜치에서 프로젝트 초기세팅 (폴더 및 파일들 만들기)
2. 각 팀원들이 Fork 해가기
3. 각 팀원들은 Forked Remote를 Local로 세팅하기
   1) 내 작업 pc에 폴더 생성
   2) git init
   3) git remote add origin <forked_remote_url>  -- 포크해온 내 레파지토리의 이름은 origin
      git remote add upstream <base_remote_url>  -- 원본 레파지토리의 이름은 upstream
      git remote => 현재 등록된 원격지 확인
   4) git pull origin main

### 기능별 개발 
1. 각자 할 일(feat, bug, 등)을 Issue로 등록하기(원본레파지토리) => 이슈번호 확인
2. Local에서 브랜치 생성 및 해당 브랜치로 이동 (feature/#이슈번호, bug/#이슈번호, 등등)
   1) git checkout -b <branch_name>
   2) git branch (브랜치이동이 잘되었는지 확인)
3. 작업하기(기능 구현 및 버그 수정 등)
4. 작업 파일(변경사항 파일) commit하기 (commit 메세지에 #이슈번호 달기)
   1) git add <파일 및 .>
   2) git commit -m '#이슈번호 ~~'
5. Forked Remote(origin) 으로 push 하기 (feature/#이슈번호 브랜치로)
   1) git push origin <branch_name> 
6. PR(Pull Request) 날리기 (upstream/main <- origin/feature/#이슈번호)
7. 다같이 코드리뷰 하며 PR 승인 & merge (또는 특정 인원수 이상 승인시 자동으로 merge 되도록)
8. upstream/main에 병합되어있는 최신작업물을 origin/main으로 merge 하기 + local/main으로 내려받기 
   1) Sync fork
      - git fetch upstream
      - git checkout main
      - git pull upstream main
      - git push origin main
   2) git checkout main
   3) git pull origin main

// 그 이후부터 위의 "기능별 개발" 부분 반복
