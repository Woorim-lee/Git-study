# Git

(**버전**을 통해) 코드 관리 도구



## SCM & VCS

* SCM : Source Code Management (소스 코드 관리)
* VCS : Version Control System (버전 관리 시스템)



# 생활코딩 git

[생활코딩 git 강의](https://opentutorials.org/course/3837)

* Git 은 반드시 개발자만 사용하는 것은 아니다. 소스코드를 넘어, 일반 문서를 사용하는 사용자에게도 유용하다.



### Git을 사용하는 목적

#### 1. 버전 관리 도구

* 변경 이력 트래킹
* 언제든 특정 시점으로 이동 가능

#### 2. 백업 도구 (코드 저장도구)

* 원격저장소(github),  지역저장소(내 컴퓨터)

* push : 지역저장소(my1)에서 원격저장소(github.com)로 내보내기 

* pull : 원격저장소(github.com)에서 지역저장소(my2)로 가져와서 작업하기

#### 3. 협업 도구

* 백업을 해놓으면 협업은 당연히 되는 것! 
* push 와 pull 을 통해 원격저장소를 매개로, 각자 컴퓨터에서 작업한 내용을 공유



### Git의 종류

* TortoiseGit : windows 에서만 사용가능 (윈도우탐색기에 기생하는 프로그램)

* GitHub Desktop : 단순함, 추후에 답답할 수 있음

* Sourcetree : 복잡함, 자유로움, 강력한 툴

* Git : git original program, 복잡해보임, 명령어를 통해 git 프로그램을 제어할 수 있음

  * git log : 현재까지 버전 목록 보여줘!
  * git status : 현재 관리하고있는 파일의 상태를 보여줘!
  * git commit -am "Message 10" : 새로운 버전 파일 추가 
  * git push : 업로드

  

## Git 버전 관리

> 중요 : Git은 **폴더 단위**로 코드를 관리

* 커밋 == 버전생성 == 스냅샷 촬영 == 현재 상태 저장



### `git init` : git 시작하기

특정 폴더를 git으로 관리 시작

* `(master)` 프롬프트에 표시
* `.git` 폴더 생성
  * `.git` 폴더 삭제 시, git 관리 중지 (`rm -r .git/` .git을 지우는 방법)



### `git status`

git에게 상태를 물어봄

* `git init` 직후

```
On branch master : master라고 하는 branch에 있어
No commits yet : 아직 commit 없어
nothing to commit (create/copy files and use "git add" to track)
: commit 할게 없어 (트래킹 하고 싶으면 `git add` 명령어를 사용해)
```

* `touch a.txt` 파일 생성 직후

```
Untracked files: 추적되지 않은 파일이 있어
  (use "git add <file>..." to include in what will be committed)
        a.txt (빨강)
: commit 될 수 있게 포함하고 싶으면 `git add <파일명>`을 사용해

nothing added to commit but untracked files present (use "git add" to track)
```

* `git add a.txt` 직후

```
Changes to be committed: commit 될 변경 사항이 있어
  (use "git rm --cached <file>..." to unstage)
        new file:   a.txt (초록)
```



![](C:\Users\USER\OneDrive\바탕 화면\210712_데이터사이언스과정\2021.07.14~15 git 특강\git_graphic_image.png)





### `git add [파일명]`

Staging Area(스냅샷 무대) 에 파일 추가



### `git commit -m "커밋 메세지"`

버전을 생성

* 커밋(버전) 구성 요소
  * 해시(Hash)
  * 작성자
  * 날짜
  * 커밋 메세지 : 버전에 대한 설명

````
[master (root-commit) 1437548] First commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 a.txt
````



### `git log`

버전(커밋)들의 히스토리(로그)



### `git config`

설정

* `git config` [설정할 내용] [설정할 값]
  * `git config user.name`
  * `git config user.email` 
  * `git config --global` 전역설정 (전체 바꾸는것)
  * `git config --global user.name 'Woorim Lee'`
  * `git config --global user.email 'woorim0806@gmail.com'`



### Git 명령어

* commit
  * 커밋은 git 저장소에 내 폴더(디렉토리)안에 있는 모든 파일의 스냅샷을 기록하는 것
  * git은 가능한 한 커밋을 가볍게 유지하고자 함, 변경사항만 ("delta"라고도 함) 저장 ->그래서 대부분의 커밋이 그 커밋 위의 부모 커밋을 가리킨다.
  * tag 
* branch 
  * 하나의 커밋과 그 부모 커밋들을 포함하는 작업 내역, 특정 커밋에 대한 참조(reference)
  * 브랜치를 많이 만들어도 메모리나 디스크 공간에 부담이 없기 때문에, 작은 단위로 잘게 나누는 것이 좋음
* checkout
  * 내가 사용할 브랜치를 지정해주는 것 
* cherry-pick
* reset
* revert
* rebase
  * 브랜치끼리 작업을 접목하는 방법
* merge
  * 두 별도의 브랜치를 합치기
  * git의 합치기(merge)는 두개의 부모(parent)를 가르키는 특별한 커밋을 만들어냄. 두개의 부모가 있는 커밋이라는 것은 "한 부모의 모든 작업내용과 나머지 부모의 모든 작업, 그리고 그 두 부모의 모든 부모들의 작업내역을 포함한다"라는 의미가 담겨있음





## Git 용어 정리

* `git init` : initialize repository
* `.git` : git repository
* `git status` : working tree status
* `git add` : add to staging area
* `git commit` : create version
* `git log` : show version , 나갈때는 `q` 버튼을 누른다.
* `git log --stat` : commit (버전)마다 관련되어있는 파일을 그룹핑해서 볼 수 있음.
* `nano 파일명` : 파일을 만들어서 저장, ctrl+x누르고(exit), y(저장-yes)누르고 엔터 (나오기)
* `cat 파일명`: 파일 내용을 화면에 출력
* `grep 검색하고 싶은 텍스트 파일명` : 파일 내에 검색하고 싶은 텍스트가 포함된 행 출력

* `git diff` : show changes, 이전 버전과의 차이점(수정사항)을 보여줌
* `git reset --hard "commit명"` : 버전 삭제, 마지막 버전에서 "commit명"으로 돌리는 방법
  * commit명 버전으로 되돌리겠다 (수정하던 파일도 모두 삭제, 가장 강력)
  * `git reset --soft` or `git reset --mixed` 는 버전만 삭제하고 수정하던 파일은 그대로 두겠다 정도로만 알고 있기
  * 매뉴얼 : `git reset --help`
  * 협업 시에는 공유 전 버전만 리셋 가능, 공유 후에는 리셋하면 안됨!
* `git revert` : 버전 되돌리기
  * 최신 버전에서 전 버전으로 `revert` 한다면, 최신 버전의 commit id를 `revert` 해야함
  * 역순으로 차례대로 `revert` 해야함
  * `revert` 는 각 버전(commit)마다의 사항만 되돌림 (그래서 역순으로 차례대로 해줘야함)

* `git log -p` : 버전마다 마지막 버전(최신 수정사항)을 보여줌

* `git checkout` : HEAD를 옮겨서 버전을 만든 시점으로 이동
* `git checkout master` : 가장 최신 상태로 다시 돌아가기(모든 파일이 최신상태로 복귀됨)

* `git add .` : 현재 디렉토리 밑에 있는 모든 파일을 add 해줌 (파일명 하나하나를 적어줄 필요는 없음)
* `git commit -am "버전명(commit message)"` : -**a**m 에서 a는 add의 약자로, add와 commit을 함께 해줌
  * untracked files 이 있는 경우에는 자동으로 add 되지 않음 주의! 

* `.gitignore` : 버전 관리가 필요없는 경우 만들기





## Git을 게임으로 배워보기

[Git Advanced](https://learngitbranching.js.org/?locale=ko)