### stash를 사용해 현재 브랜치 작업 내용 임시 저장하기
------------------

### 문제상황
실수로 A라는 브랜치에서 개발을 진행하고 B라는 브랜치로 저장해야할 경우가 생겼다. 
commit을 할순 없어서 해결방법을 찾아봤다.

-------------

### 해결방법

git stash 사용
git stash는 현재 작업을 임시로 stash 스택을 생성해서 저장해준다. 
git stash로 현재작업을 저장한뒤, 변경해야할 브랜치로 check out 한뒤 임시저장한 내용을 다시 내려받고 커밋하면된다.

`git stash` : 스택에 새로운 stash 저장

`git stash list` : 스택에 저장된 Stash목록들 확인

`git stash apply` : 가장 최근에 저장한 stash를 가져와 적용해준다.

`git stash drop` : 가장 최근에 저장한 stash를 삭제해준다.
