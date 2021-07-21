# pull request

> 독립적으로 진행되던 브랜치의 작업을 다른 브랜치에 병합해달라고 요청하는 기능
>
> 브랜치에서 만들어진 버전에 대해 동료들과 토론(코드리뷰)을 통해 코드의 품질을 높이는 작업을 할 수 있게 해주며, 충분히 검토가 끝나고 github.com 에 병합 버튼을 누르면 자동으로 브랜치가 병합됨
>
> 검토된 코드의 브랜치만 병합되므로, master 브랜치의 안정성을 높임

<br>

<br>

## pull request 의 두가지 방법

* 원격 repository 와 연결되어 있는 경우 (권한 O)

  * 내가 작업한 branch 를 다른 branch에 병합하기 전, 다른 사람의 의견을 듣고 싶을 때!

    

* 원격 repository 와 연결되어있지 않은 경우 (권한 X, 오픈소스의 경우)
  * 먼저, 원격 저장소를 복제 (fork) 
    * **fork** : 다른사람의 원격저장소를 내 원격저장소로 가져오는 것
  * 복제된 원격 저장소는 이제 내것이 되었으므로, 거기에 작업하고 push 하여 원격저장소를 업데이트 해 나감 (원본 레포지토리는 영향없음)
  * 내가 수정한 내용이 original 버전에도 유용하다고 판단이 되면, 내 원격저장소의 내용을 pull 해 가달라고 request 할 수 있음 (오픈소스 방식의 pull request)





### conflict

> pull request를 이용할 때, 같은 부분을 수정하여 충돌이 난 경우

* github 이 가지고 있는 editor 에서 처리하는 방법

  Use the <u>web editor</u> 를 클릭해서 웹에서 직접 수정할 수 있음

  

* command line 에서 처리하는 방법

  * step1

    ```
    git fetch origin
    git checkout -b branch이름 origin/브랜치이름
    git merge master
    ```

  * step2

    ```
    git checkout master
    git merge --no--ff branch이름
    git push origin master
    ```

    
