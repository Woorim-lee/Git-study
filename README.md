# Git 공부
> git에 대한 공부 내용 정리

[Git 간편안내서 참고](http://rogerdudler.github.io/git-guide/index.ko.html)

1. Git 시작
1)  폴더를 만들고, 그 안에 들어가서 git 시작을 하기 

`pwd` 현재 어디에 위치했는지 확인 ( `~` 명령으로 홈으로 이동)

`mkdir 폴더명` 폴더 생성

`cd 폴더명` 생성된 폴더로 이동

`git init` git 시작!

2. 저장소 받아오기
1) 로컬 저장소에 원격 저장소를 복제해오기 (처음 1회)

`git clone 저장소주소`



* 파일 명 변경

`mv 기존이름 변경이름`


* 파일 이동

`mv 파일명 폴더명`


* 파일 복사

`cp 파일명 경로`


* Untracked 파일 삭제

`git rm`


* Tracked (git에 이미 push된 파일) 파일 삭제 (로컬 디렉토리에서는 삭제하지 않고, 원격 저장소 git에서만 삭제하기)

`git rm --cached 파일명`

`git commit -m "Delete 파일명`

`git push origin master`


