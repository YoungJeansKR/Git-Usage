# Git-Usage
Git 사용법 정리
<br><br><br>

📍 기본
$ git add (파일명) 		// 특정 파일 Index(Staging area)에 추가
$ git add . 			 // 현재 및 하위 디렉토리 모든 파일 index 추가
$ git commit -m "(설명)"	// local repository에 추가
$ git push origin master // remote repository에 추가
<br><br><br>

📍 커밋 수정(amend)
로컬 저장소의 가장 마지막 커밋을 수정

git commit --amend -m "(설명)"
git commit --amend --no-edit //--no-edit 옵션은 설명 수정하지 않을 때
📍 버전확인
$ git --version
📍 커밋 이력 보기(log)
$ git log
이후 git checkout으로 시점을 변경하거나 reset 등으로 되돌리기 가능

📍 커밋 이력 보기2(reflog)
$ git reflog
HEAD@{idx} 이런식으로 모든 브랜치의 이력을 확인하고, reset을 하고 싶을 땐

git reset HEAD@{index}
으로 돌아가면 된다.
git log보다 압축적으로 로그 확인이 가능하다.

📍 커밋 메시지 변경
$ git commit --amend
입력하면 에디터가 열리면서 현재 커밋의 메시지를 수정할 수 있다.

커밋에 빠뜨린 파일 추가
아직 push를 하지 않은 상태에서 로컬 커밋에 파일 하나를 빠뜨렸다면,

$ git add [빠뜨린 파일]
이후에

$ git commit --amend --no-edit
이렇게 하면 빠뜨린 파일이 같이 커밋 된다.

📍 원격저장소 확인/연결
$ git remote -v

$ git remote add (이름) (url) // 원격저장소 추가

📍 브랜치 목록 보기
$ git fetch		  // 정보 업데이트
$ git branch  	  //local
$ git branch -a   //remote까지 확인
📍 파일 상태보기
$ git status
index(stage) 영역에 없으면 🟥빨간색 = add 안된 상태
index(stage) 영역에 있으면 🟩초록색 = add 된 상태

branch
📍 새 브랜치 만들기
$ git branch (브랜치명) 	   			   // 브랜치만 생성
$ git checkout (브랜치명)    			   // 해당 브랜치로 이동
$ git checkout -b (브랜치명) 			   // 현재 커밋에서 브랜치 생성하고 이동
$ git checkout (커밋아이디) -b (브랜치명)   //해당 커밋으로 이동 후 브랜치 생성
📍 마스터 브랜치로 돌아가기
$ git checkout master

📍 브랜치 목록 보기
$ git branch    //local
$ git branch -a //remote까지 확인
원격브랜치는 다음 명령어로도 확인 가능

git ls-remote origin
📍 브랜치 삭제
$ git branch -d (브랜치명) 			   //로컬 저장소에서 브랜치 삭제
$ git push origin --delete (브랜치명)    //원격저장소에서도 삭제
📍 main브랜치 이름 변경
git branch -m main master
git fetch origin
git branch -u origin/master master
git remote set-head origin -a

checkout과 reset/stash
📍checkout
다른 커밋 보기로 커밋 이력은 그대로 있는 상태에서 현재 보는 시점을 변경.

$ git checkout (커밋아이디)  // 커밋아이디는 git log로 확인
$ git checkout master	  // 최근 커밋 상태로 돌아오기
$ git checkout (브랜치명)   // 해당 브랜치로 이동
📍reset
로컬저장소에서 이전 커밋으로 돌아가고 이후 커밋은 add는 안 한 상태(unstage)로 만들기.
워크 스페이스에 작업하던 내용은 그대로 있음.

$ git reset (커밋 아이디)
$ git reset HEAD^		//한 커밋 이전
$ git reset HEAD^^		//두 커밋 이전
$ git reset HEAD^^^		//세 커밋 이전
이전 커밋으로 돌아가면서 이후 커밋 삭제(하드 리셋)

$ git reset --hard (커밋 아이디)
$ git reset --hard HEAD^^
✎ 이후 원격 저장소에는 삭제가 반영되지 않은 상태이므로 강제 커밋

$ git push origin master --force
✎ checkout은 커밋은 그래로 두고 HEAD(시점)만 이동하고, reset은 삭제까지 한다는 차이가 있음.
✎ reset 대신 revert를 사용할 수 있는데, revert는 기준 커밋 이후로 삭제하는 것이 아니라 현재까지의 이력을 남겨두고 과거 커밋으로 재수정해 커밋한 효과임.

$ git revert (커밋아이디)
📍 stash, commit 안 하고 checkout
checkout으로 다른 브랜치로 이동할 때 commit을 하라는 메시지가 나올 때가 있다. commit을 하고 싶지 않다면 stash를 이용한다.

$ git stash
stash를 하면 임시 저장소에 수정 파일이 저장된다.
꺼낼 때는

$ git stash list
작업하던 브랜치로 돌아와서 수정했던 내역을 stash에서 다시 가져올 때는

$ git stash apply // 최근 stash 가져오기
$ git stash apply [stash 항목] // stash list 중 특정 항목에서 가져오기 
저장소 내 파일 삭제
📍 로컬 영역에서 제거
$ git rm (파일명)
📍 리모트 영역에서 제거
$ git rm (파일명) --cached
$ git rm -r (폴더) --cached

✎ --cached는 리모트로 이미 push까지 했을 경우 붙이는 옵션
✎ 이후 commit하고 push 다시 해주면 remote에 반영됨

📍 처음부터 특정 파일 커밋 안 하기
.gitignore파일을 생성해 git에 추가하고 싶지 않은 파일이나 폴더 리스트를 입력

✎ .gitignore 파일 목록 검색

$ git ls-files -o -i --exclude-standard

-o : untracked files
-m : modified files
-d : deleted files
-c : cached files
-i : ignored files
--exclude-standard : .gitignore
저장소에서 코드 가져오기
📍 origin에서 코드 가져오기
$ git pull origin master
📍 원격 저장소에서 코드 가져오기
$ git clone (url) (저장할 폴더 이름)
📍 원격에서 로컬로 코드 가져오기
$ git fetch origin
📍 병합하기
master 브랜치 또는 원하는 브랜치로 이동 후 병합하고자 하는 브랜치를 병합

$ git checkout master
$ git merge (브랜치명)
📍 특정 브랜치를 다른 브랜치의 코드로 대체
$ git checkout (바뀔 브랜치)
$ git reset --hard (타깃 브랜치)
기타
📍 깃 메시지
.gitmessage.txt 작성 후 아래와 같이 설정하면 git commit 시 커스텀 메시지를 볼 수 있다.

git config --global commit.template .gitmessage.txt
.gitmessage.txt 예시

# <타입>: <제목>
# 본문
# 꼬리말
# 필요한 경우 주석 처리(#)를 지우고 사용. 이슈 트래킹을 위함
# Issues: #이슈번호
# Resolves: #이슈번호
# See also: #이슈번호
# ------------------
# <타입> 리스트
#   feat    : 기능 (새로운 기능)
#   fix     : 버그 (버그 수정)
#   design  : CSS 등 사용자 UI 디자인 변경
#   style   : 스타일 (코드 형식, 세미콜론 추가: 비즈니스 로직에 변경 없음)
#   refactor: 리팩토링
#   comment : 필요한 주석 추가 및 변경
#   docs    : 문서 (문서 추가, 수정, 삭제)
#   test    : 테스트 (테스트 코드 추가, 수정, 삭제: 비즈니스 로직에 변경 없음)
#   chore   : 기타 변경사항 (빌드 스크립트, 패키지 매니저 설정 수정 등)
#   rename  : 파일 혹은 폴더명을 수정하거나 옮기는 작업만인 경우
#   remove  : 파일을 삭제하는 작업만 수행한 경우
#   !HOTFIX : 급하게 치명적인 버그를 고쳐야하는 경우
#   !BREAKING CHANGE : CHANGE 커다란 API 변경의 경우
# ------------------
#     제목과 본문을 한 줄 띄워 분리하기
#     제목 첫 글자를 대문자로
#     제목은 영어 50자 이내 (한글은 25자 이내)
#     제목은 명령문으로 (적용 시, 이 커밋은 <커밋 메시지> 합니다)
#     제목 끝에 마침표(.) 금지
#     본문은 영어 72자 마다 개행 (한글은 36자 마다)
#     본문은 “어떻게” 보다 “무엇을“, “왜”를 설명한다.
#     본문에 여러줄의 메시지를 작성할 땐 “-”로 구분
# ------------------
#     꼬리말은 optional이고 이슈 트래커 ID를 작성합니다.
#     꼬리말은 “유형: #이슈 번호” 형식으로 사용합니다.
#     여러 개의 이슈 번호를 적을 때는 쉼표로 구분합니다.
#     이슈 트래커 유형은 다음 중 하나를 사용합니다.
#       - Fixes: 이슈 수정중 (아직 해결되지 않은 경우)
#       - Resolves: 이슈를 해결했을 때 사용
#       - Ref: 참고할 이슈가 있을 때 사용
#       - Related to: 해당 커밋에 관련된 이슈번호 (아직 해결되지 않은 경우)
#     ex) Fixes: #45 Related to: #34, #23
#-------------------
📍 깃 파일명 대소문자 구분
Git은 기본적으로 대소문자를 구분하지 않는 파일 시스템에서 동작하기 때문에, 파일명의 대소문자 구분을 하려면 다음 명령어를 실행한다.

git config core.ignorecase false 

📍깃헙 토큰 발행 방법
➡️ github 접속 및 가입
➡️ settings 
➡️ developer settings 
➡️ personal access tokens 
➡️ generate new tokens
✎ 토큰 설정 후 토큰 키를 복사한다음에 쉘에서 push할 때 비밀번호 작성하는 부분에 붙여넣어야 함
<br><br><br>

📍ssh key 설정 방법
shell에서 
$ ssh-keygen            //키 생성
$ cat ~/.ssh/id_rsa     //개인키
$ cat ~/.ssh/id_rsa.pub //공개키
✎ 이후 깃허브 프로필-세팅에서 ssh 공개키 등록
<br><br><br>

📍깃허브 push용 이름 및 이메일 세팅
$ git config --global user.name "username"
$ git config --global user.email "email@email.com"
✎ --global 옵션은 default로 전체 깃에 적용. 특정 프로젝트에서 이름 다르게 하려면 --global 옵션 빼고 하면 됨
<br><br><br>

