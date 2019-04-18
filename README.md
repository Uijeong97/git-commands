# git-commands
[깃 명령어 정리]
================
##1. git concept
  git은 파일을 저장하는 것이 아니라 수정 내역 등 작업 이력을 저장한다!
  repository 는 실제 소스코드가 담겨있으면서 commit 내역 등의 작업 이력이 담겨있다.

  branch 를 merge 하려고 하는데 안된다 => 작업 이력이 달라서 그렇다.


##2. git repository
repository 는 실제 소스코드가 담겨있으면서 커밋 내역 등의 작업이력이 담겨있다.

  1. working directory  : 나의 작업공간(물리적 작업공간)
  2. storaging Area     : (working directory)-> git add ->(storaging Area)
  3. local Repository   : .git 에 있는 작업공간(github에 띄우기 전 작업공간)
  4. remote Repository  : github에 있는 작업공간


##3. git commands
● add, commit, push
(working directory)->  git add ->(storaging Area)-> git commit ->(local Repository)-> git push ->(remote Repository)

● reset, merge, fetch
(working directory)<- git reset <-(storaging Area)<- git merge ->(local Repository)<- git fetch <-(remote Repository)

● git pull: merge+fetch 모두 수행
(storaging Area)<- git merge ->(local Repository)<- git fetch <-(remote Repository)

● git reset: add, commmit 기록 되돌리기
git reset --hard [해쉬값]: 해당 해쉬값 기준으로 돌아간다. 그 이후의 log 들은 다 삭제


##3. git branch
###3.1 branch concept
말그대로 가지치기라고 생각하면 된다.
  안정적인 master branch 는 그대로 두고,
  가지를 쳐서 develop branch 와 bug fix branch 등으로 나누어 개발을 하거나 버그를 고칠 수 있다.
  새로운 branch들을 수정한 이후에는 master에서 가지들을 merge 한다.

● master branch : 디폴트 가지
  항상 안정화 되어있도록 유지해야한다.

###3.2 branch commands
● git branch
  브랜치 종류 보는 명령어, *master 이렇게 앞에 '*'은 지금 해당 브랜치 작업중임을 보여준다.
● git branch [develop]
  develop 이라는 브랜치를 생성하는 명령어
● git checkout [develop]
  develop 브랜치로 스위칭하는 명령어, develop 브랜치에서 작업을 하겠다는 선언
  스위칭 이후, add,commit 등을 하면 master에는 영향을 주지 않고 develop 에만 작업가능!!!
  우리도 브랜치 만들어서 해야돼 한번더 내 commit들 없애면 진짜 화낸다
● git branch -d [develop]
  debelop 이라는 브랜치를 제거하는 명령어
  병합이 끝나면 제거하자!!!!!!!!
  
###3.3 branch conflicts
브랜치를 만들다보면 충돌이 일어나서 push 가 더이상 안될 때!
● 해결방법
  충돌이 나면 1)어떤 파일에서 충돌이 일어났는지, 2)그 파일에 충돌난 코드를 표시를 해주는데
  일단 해당 파일을 열고 충돌난 코드를 확인해보자!
  그리고 어떤 코드를 사용할 지 수동으로 결정해주어야 한다!


##4. Remote Repository
네트워크 저장소에 어딘가 존재하는 저장소!
예를들어, 깃 허브 서버에 있는 저장소나 다른 저장소를 가질 수 있다.
● git remote
  현재 원격 저장소로 어떤것이 등록되어있는지 확인할 수있음.
● git remote show [origin]
  원격 저장소 자세히 확인 할 수 있음
● git remote add [test] [경로]
  원격 저장소를 추가할 수 있다.
● git remote rename [test] [temp]
  이름바꾸기(test를 temp로)
● git remote -v
  원격 저장소 확인
● git remote rm temp
  원격 저장소 삭제


##5. git log 관리
###5.1 git log commands
● git log
  최신 순서대로 commit 정보를 보여줌
  enter치면 스크롤이 내려가고 q누르면 빠져나온다.
● git log --stat
  commit 정보+
  라인수가 얼마나 변경되었는지 보여줌
● git log -p -[3]
  commit 정보+
  어떻게 변경되었는지(코드)+
  [3]줄 출력
● git log --pretty=online
  각각의 commit 내역들이 한줄씩 출력(딱 commit 정보만 간단하게)
● git log --pretty=format:"%h->%ar : %s" --graph
  해쉬[%h]->언제[%ar]->어떤메시지[%s]
  
