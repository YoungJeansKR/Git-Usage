# Git-Usage

* Git 사용법 정리

<br/>

📍 기본
```
$ git pull origin main    // origin에서 코드 가져오기
$ git add .               // 현재 및 하위 디렉토리 모든 파일 index 추가
$ git commit -m "text"    // local repository에 추가
$ git push origin main    // remote repository에 추가
$ git push origin -f main // remote repository에 추가(강제)
```

<br/>

📍 원격저장소 확인/연결
```
$ git remote add origin (url) // 원격저장소 추가
$ git remote rm origin        // 원격저장소 제거
$ git remote -v               // 원격저장소 주소 확인
```

<br/>

📍 처음부터 특정 파일 커밋 안 하기
```
.gitignore파일을 생성해 git에 추가하고 싶지 않은 파일이나 폴더 리스트를 입력
.gitignore 파일 목록 검색
-o : untracked files
-m : modified files
-d : deleted files
-c : cached files
-i : ignored files
--exclude-standard : .gitignore
```

<br/>

📍 커밋 수정(amend)
```
$ git commit --amend -m "(설명)"
```

<br/>

📍 커밋 이력 보기(log)
```
$ git log //이후 git checkout으로 시점을 변경하거나 reset 등으로 되돌리기 가능
```

<br/>

📍 브랜치 목록 보기
```
$ git fetch   // 정보 업데이트
$ git branch  //local
```

<br/>

📍 파일 상태보기
```
$ git status
index(stage) 영역에 없으면 🟥빨간색 = add 안된 상태
index(stage) 영역에 있으면 🟩초록색 = add 된 상태
```

<br/>

📍 새 브랜치 만들기
```
$ git branch (브랜치명) 	   			          // 브랜치만 생성
$ git checkout (브랜치명)    			         // 해당 브랜치로 이동
$ git checkout -b (브랜치명) 			         // 현재 커밋에서 브랜치 생성하고 이동
$ git checkout (커밋아이디) -b (브랜치명)   //해당 커밋으로 이동 후 브랜치 생성
```

<br/>

📍 브랜치 삭제
```
$ git branch -d (브랜치명) 			   //로컬 저장소에서 브랜치 삭제
$ git push origin --delete (브랜치명)    //원격저장소에서도 삭제
```

<br/>

📍checkout
```
$ git checkout (커밋아이디)  // 커밋아이디는 git log로 확인
$ git checkout master	  // 최근 커밋 상태로 돌아오기
$ git checkout (브랜치명)   // 해당 브랜치로 이동
```

<br/>

📍 원격 저장소에서 코드 가져오기
```
$ git clone (url) (저장할 폴더 이름)
```

<br/>

📍 원격에서 로컬로 코드 가져오기
```
<br>$ git fetch origin
```

<br/>

📍 병합하기
```
$ git checkout master
$ git merge (브랜치명)
```

<br/>

📍 특정 브랜치를 다른 브랜치의 코드로 대체
```
<br>$ git checkout (바뀔 브랜치)
<br>$ git reset --hard (타깃 브랜치)
```
