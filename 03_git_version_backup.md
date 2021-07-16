# Git 버전관리

[생활코딩 Git 버전관리](https://opentutorials.org/course/3841)



Git은 버전정보를 `.git` 디렉토리에 저장



local repository 1 --> (push) --> remote repository

local repository 2 <-- (clone) <-- remote repository

local repository 2 --> (push) --> remote repository

local repository 1 <-- (pull) <-- remote repository

언제 어디서 작업을 하든지, 원격저장소(Git)를 통해, 작업이동성 극대화



##  Git hosting

> Github 사이트를 이용하여 버전관리
>
> Gitlab.com 도 추천, free private repositorues (무제한 용량/무제한 참여자) 가능



## 백업

1. 원격 저장소 생성
2. remote 정보 입력
3. git push 



## `git remote`

원격 저장소 정보 출력

* `git remote add` 
  
  * `git remote add [저장소별명] [저장소주소]`
  
  * `git remote add origin https://github.com/Woorim-lee/first.git`
  
    내 컴퓨터의 지역저장소가 위 https://~ 원격저장소 주소와 연결시킨 것
  
    **지역저장소는 여러 원격저장소에 연결 될 수 있음
  
    add 뒤에 `origin`은 원격저장소 별명 (origin은 관습적으로 사용하는)
* `git remote -v` : verbose(말이 많은), 상세 출력, 어떤 원격저장소에 연결되어있는지 확인할 수 있음



## `git push`

원격 저장소에 코드 백업

* `git push [저장소별명] [브랜치이름]`
  * `git push --set-upstream origin master` : 기본적으로 origin에, master 브랜치가 업로드 되도록 셋팅
  * `git push origin master`



## `git clone`

로컬 저장소에 복제

* `clone with HTTPS` 버튼으로 url 복사
* `git clone [저장소 주소] [디렉토리명]` 
  * 저장소 주소 뒤에 아무것도 적지 않으면 현재 이 명령을 시킨 이 디렉토리에 동일한 디렉토리가 생성됨 , 뒤에 디렉토리 명을 적으면 원하는 명으로 생성



## `git pull`

원격저장소의 버전을 지역저장소로 댕겨온다

* `git pull`

git pull -> 작업 > git add > git commit > git push 순서로 작업을 하면 됨 



## git 오픈소스

* `git clone [저장소 주소]` 로 가져올 수 있음
* git 을 사용할 수 있다는 것은 이제 앞으로 수많은 오픈소스를 다룰 수 있는 준비가 끝난 것!



## 수업을 마치며

* issue tracker (=to do list)
* 협업 : 동시에 작업하다가 생길 수 있는 conflict (충돌) 문제



