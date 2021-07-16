# Git branch & Conflict

같은 뿌리에서 나왔지만 서로 다른 역사를 써가고 있는 버전, 이를 효율적으로 관리해줄 수 있는 기능

branch와 branch를 병합할 때 *충돌*의 문제점 : 같은 파일내에 같은 부분을 수정한 경우 > 병합하는 사람에게 수정 요청!

## `git branch`
* `git branch` : 브랜치의 목록을 보여줌, 현재는 `master` 밖에 없고, 이는 `master` 브랜치 위에서 작업을 한 것이라는 의미
* `git log --all --graph --oneline` 을 실행시켜, 현재까지의 작업 상황을 알 수 있고, `HEAD`가 `master`를 가르키고 있음을 알 수 있음.
* `git branch [브랜치명]` : 브랜치명으로 새로운 브랜치를 생성


## `git checkout`
* `git checkout [브랜치명]` : 브랜치명 버전으로 `HEAD`가 변경됨. 그 당시의 버전(작업 내용)으로 바뀜


## `git merge`
브랜치를 나누어 작업했다가 다른 브랜치에서 작업한 내용과 합쳐야 하는 이슈가 생겼을 때 !

* `base` : merge 가 필요한 branch의 공통된 조상, 그 `base`를 바탕으로 새로운 버전을 만들 수 있음 (병합 커밋=merge된 commit)

* `git merge [branch 이름]` :  