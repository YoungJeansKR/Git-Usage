# Git-Usage
* Git 사용법 정리
<br><br>

📍 기본
<br>$ git add (파일명)     // 특정 파일 Index(Staging area)에 추가
<br>$ git add . 			 // 현재 및 하위 디렉토리 모든 파일 index 추가
<br>$ git commit -m "(설명)"	// local repository에 추가
<br>$ git push origin master // remote repository에 추가
<br>$ git push origin +master  // remote repository에 추가(강제)
<br><br>

📍 origin에서 코드 가져오기
<br>$ git pull origin master
<br><br>

📍 원격저장소 확인/연결
<br>$ git remote -v
<br>$ git remote add (이름) (url) // 원격저장소 추가
<br><br>

📍 처음부터 특정 파일 커밋 안 하기
<br>.gitignore파일을 생성해 git에 추가하고 싶지 않은 파일이나 폴더 리스트를 입력
<br>.gitignore 파일 목록 검색
<br>-o : untracked files
<br>-m : modified files
<br>-d : deleted files
<br>-c : cached files
<br>-i : ignored files
<br>--exclude-standard : .gitignore
<br><br>

📍 커밋 수정(amend)     //로컬 저장소의 가장 마지막 커밋을 수정
<br>git commit --amend -m "(설명)"
<br>git commit --amend --no-edit //--no-edit 옵션은 설명 수정하지 않을 때
<br><br>

📍 커밋 이력 보기(log)
<br>$ git log     //이후 git checkout으로 시점을 변경하거나 reset 등으로 되돌리기 가능
<br><br>

📍 브랜치 목록 보기
<br>$ git fetch		  // 정보 업데이트
<br>$ git branch  	  //local
<br>$ git branch -a   //remote까지 확인
<br><br>

📍 파일 상태보기
<br>$ git status
<br>index(stage) 영역에 없으면 🟥빨간색 = add 안된 상태
<br>index(stage) 영역에 있으면 🟩초록색 = add 된 상태
<br><br>

📍 새 브랜치 만들기
<br>$ git branch (브랜치명) 	   			   // 브랜치만 생성
<br>$ git checkout (브랜치명)    			   // 해당 브랜치로 이동
<br>$ git checkout -b (브랜치명) 			   // 현재 커밋에서 브랜치 생성하고 이동
<br>$ git checkout (커밋아이디) -b (브랜치명)   //해당 커밋으로 이동 후 브랜치 생성
<br><br>

📍 브랜치 목록 보기
<br>$ git branch    //local
<br>$ git branch -a //remote까지 확인
<br><br>

📍 브랜치 삭제
<br>$ git branch -d (브랜치명) 			   //로컬 저장소에서 브랜치 삭제
<br>$ git push origin --delete (브랜치명)    //원격저장소에서도 삭제
<br><br>

📍checkout
<br>$ git checkout (커밋아이디)  // 커밋아이디는 git log로 확인
<br>$ git checkout master	  // 최근 커밋 상태로 돌아오기
<br>$ git checkout (브랜치명)   // 해당 브랜치로 이동
<br><br>

📍 원격 저장소에서 코드 가져오기
<br>$ git clone (url) (저장할 폴더 이름)
<br><br>

📍 원격에서 로컬로 코드 가져오기
<br>$ git fetch origin
<br><br>

📍 병합하기
<br>master 브랜치 또는 원하는 브랜치로 이동 후 병합하고자 하는 브랜치를 병합
<br>$ git checkout master
<br>$ git merge (브랜치명)
<br><br>

📍 특정 브랜치를 다른 브랜치의 코드로 대체
<br>$ git checkout (바뀔 브랜치)
<br>$ git reset --hard (타깃 브랜치)
<br><br>

📍깃헙 토큰 발행 방법
<br>➡️ github 접속 및 가입
<br>➡️ settings 
<br>➡️ developer settings 
<br>➡️ personal access tokens 
<br>➡️ generate new tokens
<br>✎ 토큰 설정 후 토큰 키를 복사한다음에 쉘에서 push할 때 비밀번호 작성하는 부분에 붙여넣어야 함
<br><br>

📍ssh key 설정 방법
<br>shell에서 
<br>$ ssh-keygen            //키 생성
<br>$ cat ~/.ssh/id_rsa     //개인키
<br>$ cat ~/.ssh/id_rsa.pub //공개키
<br>✎ 이후 깃허브 프로필-세팅에서 ssh 공개키 등록
<br><br>

📍깃허브 push용 이름 및 이메일 세팅
<br>$ git config --global user.name "username"
<br>$ git config --global user.email "email@email.com"
<br>✎ --global 옵션은 default로 전체 깃에 적용. 특정 프로젝트에서 이름 다르게 하려면 --global 옵션 빼고 하면 됨

