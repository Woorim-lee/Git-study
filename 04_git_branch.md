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
* `git merge [branch 이름]` 
  * ex ) branch가 *master* 와 *o2* 가 있을 때, *master* 에 *o2*를 병합하고 싶다면( = *o2* 브랜치의 내용을 *master*로 합치겠다라는 의미), 일단 *master* 가 head로 되어있어야 하고( = *master* 브랜치 상태가 된다), 그리고 그 상태에서 `git merge o2` 를 해준다 = *master* 브랜치에 *o2* 브랜치를 병합한다! 라는 의미 -> 병합된 새로운 버전 생성, master 브랜치 버전과 o2 브랜치 버전이 **공통의 조상**으로하는 *새로운*  커밋 생성
  * branch 변경(head가 가르키는)은 `git checkout branch명` 으로 사용
* `git reset --hard` merge 취소 -> 이전 버전으로 변경






## `conflict`

병합 시, 동일한 파일 내의 동일한 부분이 변경된 경우 git 이 확인을 요하는 기능



* **conflict** message

  * CONFLICT (content) : Merge conflict in 파일명

    Automatic merge failed; fix conflicts and then commit the result.

    `git status` 로 상태를 보면, `both modified : 파일명 메세지`가 나옴

  * conflict 발생 시 해결 순서

    1)  파일 내 들어가서 어떤 부분이 충돌(중복수정) 되었는지 확인 (각 branch 마다 중복 수정한 부분이 표시 되어있음)

    2) 올바르게 수정 후, git 에게 충돌을 확인(및 수정) 하였다는 의미로 `git add 파일명`  해줌

    3) `git commit` 해주면 파일이 충돌이 되었고 해결되었다 라는 내용을 확인가능s





## `2 way merge` vs `3 way merge`

| here | base (원본) | there | 2 way merge               | 3 way merge               |
| ---- | ----------- | ----- | ------------------------- | ------------------------- |
| A    | A           | A     | A                         | A                         |
| H    | B           | B     | ?? 충돌 (사람이 수정필요) | H                         |
| C    | C           | T     | ?? 충돌 (사람이 수정필요) | T                         |
| H    | D           | T     | ?? 충돌 (사람이 수정필요) | ?? 충돌 (사람이 수정필요) |

ex ) 두번째 행에 base와 there은 **B** (there에서 수정X), A는 **H** 로 수정된 것을 알 수 있음. 그러면, `3 way merge` 에서는 수정된 부분을 반영하여 merge 해준다.  즉, `3 way merge` 를 이용하면 `2 way merge` 와 비교하여 훨씬 더 많은 부분을 자동화 해줄 수 있다 !





## `git mergetool` 

> merge 하다 conflict이 일어났을 때, 병합을 전문적으로 해주는 도구를 통해 할 수 있음 (자동으로 충돌 된 부분의 데이터를 보여줌으로써 손쉽게 충돌 부분 확인 및 수정 가능하다!!)



##### 사용 툴 "p4merge"

1. [P4merge](https://www.perforce.com/downloads/visual-merge-tool)  다운로드

2. ` $ git config --global merge.tool p4mergetool`

   <span style="color:red">git의 전역설정으로 mergetool을 p4mergetool로 설정해서 사용하겠다</span> <span style="color:grey">라는 의미</span>

   `cat ~/.gitconfig` <span style="color:grey">가 어떻게 바뀌었는지 확인해보면, merge tool = p4merge 로 되어있음을 알 수 있음</span>

3. `$ git config --global mergetool.p4mergetool.cmd \
   "/Applications/p4merge.app/Contents/Resources/launchp4merge \$PWD/\$BASE \$PWD/\$REMOTE \$PWD/\$LOCAL \$PWD/\$MERGED"`

   <span style="color:grey">merge tool의 경로, 그리고 각 base파일의 경로, remote파일의 경로, local파일의 경로, merge된 파일 </span>

   `cat ~/.gitconfig` <span style="color:grey">를 다시 해보면, mergetool 이 p4mergetool로 설정되었고, 그 파일의 경로가 나온다!</span>

4. base : 공통의 조상 / local : 내가 있는 쪽! 현재 내가 속해있는 branch 가 local 임 / remote 저들이 있는곳.. 댕겨오려는 branch가 remote 임

   ![스크린샷 2021-07-18 오후 7.37.13](/Users/user/Desktop/스크린샷 2021-07-18 오후 7.37.13.png)

