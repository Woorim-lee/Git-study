# Git 공부
> git에 대한 공부 내용 정리
>
> 비전공자이기 때문에 선행학습으로 CLI (Command Line Interface) 학습이 필수였다.



---



### CLI (Command Line Interface)

* `pwd` print working directory, 현재 폴더 확인
* `ls` 폴더 안에 있는 파일 리스트
* `cd ~` 홈으로 돌아가기
* `cd ..` 상위 폴더로 이동
* `cd .` 현재 폴더
* `mkdir 폴더명` 폴더 생성
* `rm -rf` 하위 폴더 다 삭제 (주의!)
* `rm -r 폴더명` 폴더 삭제
* `rm 파일명.확장자` 파일 삭제
* `touch 파일명.확장자` 파일 생성
* `mv 파일명 폴더명` 파일 이동
* `mv 기존이름 변경이름` 파일명 변경
* `cp 파일명 경로` 파일 복사
* `ps aux` 현재 실행중인 프로그램 리스트
* `nano 파일명` 파일을 만들어서 현재 폴더에 저장
* `cat 파일명` 파일 내용을 화면에 출력
* `grep 검색하고싶은텍스트 파일명` 파일 내 텍스트를 검색하여 포함된 행 출력



---



[생활코딩 프로젝트 관리 참고](https://opentutorials.org/course/3838)

[Git 간편안내서 참고](http://rogerdudler.github.io/git-guide/index.ko.html)

[Git Book_한글](http://git-scm.com/book/ko/v2)



### Git 시작

> 폴더를 만들고, 그 안에 들어가서 git 시작을 하기 

1. `pwd` 현재 어디에 위치했는지 확인 ( `~` 명령으로 홈으로 이동)

2. `mkdir 폴더명` 폴더 생성

3. `cd 폴더명` 생성된 폴더로 이동

4. `git init` git 시작!



### 저장소 받아오기 

> 로컬 저장소에 원격 저장소를 복제해오기 (처음 1회, 이후부터는 `git pull` 사용)

1. `git clone 저장소주소`





### Git 의 처리 흐름 (3단계)

1. 파일 작업

2. `git status` 로 수정된, 추가된 파일 확인

3. `git add 파일명` 또는 `git add .` (디렉토리 안에 모든파일) 로 Staging area에 추가

4. `git status` 로 Staging area 위에 있는 파일 확인

5. `git commit -m "이번 확정본에 대한 메세지, 설명"` 변경된 파일이 Head 상에 반영 완료

​	아직 **원격저장소** 에는 반영되지 않은 상태!

| Working tree       | Index(Staging Area)     | Head                          |
| ------------------ | ----------------------- | ----------------------------- |
| 실제 작업하는 파일 | (`git add` 후) 준비영역 | (`git commit` 후) 최종 확정본 |





### 변경내용 원격저장소에 반영하기

> 변경 내용은 아직 로컬저장소에만 저장되어있고, 원격저장소에는 반영되지 않은 상태

1) `git push origin master` 

2) `git remote add origin 원격서버주소`

3) `git log` 를 통해 반영된 내용과 현재까지 `commit` 한 내용을 확인

4) `git remote -v` 어떤 원격저장소에 연결되어있는지 확인





### 원격저장소에서 로컬저장소로 가져오기

> 원격저장소에 업데이트 된 내용을 로컬저장소로 가져와서 작업 하기

1) `git pull origin master` 







---



##### 대단히 주관적이고 간결한 git 의 요약

로컬저장소에서 작업 -> `git status` -> `git add 파일명` -> `git commit -m "최종메세지"` -> 원격저장소에 작업내용 업데이트 `git push origin master` -> 원격저장소의 최신본을 로컬저장소로 가져오기 `git pull origin master` -> 로컬저장소에서 작업 -> ...의 반복



---







#### 이 외 유용했던 내용들 (계속 추가~!)

* Untracked 파일 삭제

`git rm`

* Tracked (git에 이미 push된 파일) 파일 삭제 (로컬 디렉토리에서는 삭제하지 않고, 원격 저장소 git에서만 삭제하기)

`git rm --cached 파일명`

`git commit -m "Delete 파일명`

`git push origin master`

*  비교 (파일의 어떤 내용이 바뀌었는지, commit 간의 비교/branch간의 비교도 가능!)

`git diff` : commit 된 파일 상태와 현재 수정중인 상태 비교

`git diff --staged` : commit 된 파일 상태와 add된 파일 상태 비교

`git diff [비교할 commit hash1] [비교할 commit hash2]` : commit 간의 상태 비교 (commit hash 이용)

###### ex ) git diff 048171 0c747d



