# Git_Practice
git의 기본적인 사용방법을 다룬다.


## 사용자 정보 등록, 기본적인 설정
<pre><code>
$git config --global user.name “홍길동”
$git config --global user.email “hong@gil.dong”
$git config --global color.ui true
</code></pre>
    --global: 현재 로그인한 계정에 전체 설정
    --local: 현재 저장소 로컬 설정


## 지역 저장소 초기화
우선 해당 디렉토리로 이동한다.
<pre><code>
$cd hello
</code></pre>
다음 명령어 실행결과, .git파일이 생성되는데 해당 파일에 히스토리 정보가 관리된다.
참고적으로 .gitignore을 이용하여 관리 대상 파일 선택 적용 가능하다.
<pre><code>
$git init
</code></pre>


## 저장공간의 논리적 분할
<img width="458" alt="작업공간의 논리적 분할" src="https://user-images.githubusercontent.com/74875490/164912054-b1d87ef5-4ea3-4bab-b27c-fe962adaa61d.png">
-working directory(작업 공간): 실제 파일을 수정하거나 생성하는 공간이다. 현재 작업 중인 소스코드들을 담고 있으며, 작업 폴더에서 .git 디렉토리를 제외한 나머지 부분이다.
-staging area(임시 저장 공간, 인덱스, 스테이지): commit하려는 파일의 추적 상태 정보들만 기록한다. stage가 만들어진 이유는 commit을 빠르게 처리하고, 충돌을 관리하기 위해서이다.
-repository(실제로 저장하는 공간): 스테이지에서 대기하고 있던 파일들을 버전으로 만들어 저장하는 곳
    - Local repository: 현재 내가 사용하고 있는 내 디바이스에 저장되는 저장소
    - Remote repository: 원격 서버에 저장되고 관리되는 저장소


## 스테이지 영역에 추가
<img width="440" alt="깃 add 예제" src="https://user-images.githubusercontent.com/74875490/164915186-e80dd01f-f948-4bbc-a4e6-5ac809fe719a.png">
각각 현재 디렉토리의 모든 변경 내용을 스테이징 영역으로 넘기고 싶을 때, 특정파일(hello.html)을 넘기고 싶을 때이다.
<pre><code>
$git add . 
$git add hello.html
</code></pre>
add한 내용을 취소하고 싶다면
<pre><code>
$git reset하면 된다.
</code></pre>

## commit(staging area->repository)
<img width="288" alt="깃 commit 취소 예제" src="https://user-images.githubusercontent.com/74875490/164915610-703988e1-c475-434e-bd05-0e5b9a2ae8e7.png">
<pre><code>
$git commit -m 'add hello.html'
</code></pre>
add와 커밋을 동시에
<pre><code>
$git commit -a -m 'add hello.html'
</code></pre>
commit한 내용을 취소 하고 싶다면 다음과 같이 커밋ID를 사용하거나 HEAD~i를 사용하면 된다.
HEAD~i의 의미는 위에서 i번째를 삭제한다는 의미이다.
<pre><code>
$git reset --hard 커밋ID
$git reset --hard HEAD~1
</code></pre>


## 커밋 로그 확인
다음과 같이 여러 옵션을 붙일수도 있다.
<pre><code>
$git log
$git log --oneline --all --graph
$git log --oneline -1
</code></pre>
commit 내용을 자세히 확인
<pre><code>
$git show
</code></pre>

## Local repository->Remote repository
main branch로 올린다.
<pre><code>
$git push -u origin main
</code></pre>


## Local repository<-Remote repository
pull명령어와 fetch명령어가 있다. pull명령어는 fetch와 merge가 합쳐진 명령어라고 생각하면 이해가 쉽다.
<pre><code>
$git fetch 원격저장소 이름
$git fetch origin
$git pull
</code></pre>

## 현재 브랜치 확인
-v를 붙이면 조금 더 자세한 내용까지 볼 수 있다.
<pre><code>
$git branch
$git branch -v
</code></pre>

## 새 브랜치 만들기
testing이라는 새 브랜치를 만들어보자. 하지만 다음 명령어 실행 후에도 HEADER는 현재 브랜치의 최종 commit을 가리킨다. checkout 명령어를 통해서 testing branch로 HEADER를 옮길 수 있다. 또한 checkout -b 옵션을 통해서 branch를 만들고 현재 HEADER의 위치를 옮기는 것을 동시에 진행할 수도 있다.
<pre><code>
$git branch testing
$git checkout testing
$git checkout -b testing
</code></pre>


## master/testinng 브랜치 상황
testing 브랜치에 추가 작업을 한 후, commit을 한다.
이후 다시 main 브랜치로 돌아오자. 주의할 점은, 브랜치를 전환하면 작업 디렉터리 내용도 함께 바뀐다.

## 병합
만약 testing 브랜치의 내용이 성공적이어서 testing 브랜치의 내용으로 main 브랜치를 통합하고 싶으면 어떻게 해야할까?
먼저, main 브랜치로 이동한 후, git merge 가져오고자하는 브랜치이름으로 병합해야한다.
<pre><code>
$git checkout main
$git merge testing
</code></pre>

## 고급기능
### 특정 커밋을 참조하는 이름 붙이기
<pre><code>
$git tag tag_name: 가장 최근 커밋에 이름 붙이기
$git tag tag_name commit_checksum: 특정 커밋에 이름 붙이기
$git tag -a tag_name: 간단한 메세지를 입력할 수 있도록 편집기가 열림
$git show tag: 누가 언제 어떤 메세지를 입력했는지 확인가능
</code></pre>

### 마지막 커밋 수정하기
<pre><code>
$git commit --amend
</code></pre>

### reset과 revert
<img width="597" alt="reset revert" src="https://user-images.githubusercontent.com/74875490/164915937-eabb3948-127b-41c3-bdb0-b1e9963a9ec4.png">
<img width="292" alt="reset revert 예제" src="https://user-images.githubusercontent.com/74875490/164916118-dc1db963-864f-4cdd-b92e-8de021126620.png">
공개된 커밋을 안전하게 변경하려면 git revert가 git reset에 비해 더 안전하다.
git revert 명령은 이전 커밋을 남겨 두지만 git reset 명령은 이전 커밋을 남기지 않기 때문이다.
<pre><code>
$git revert
$git reset
</code></pre>

### 특정 파일을 최종 커밋 시점으로 되돌리기
<pre><code>
$git checkout HEAD -- filename
</code></pre>

### 브랜치 이력을 확인하면서 병합하기
git rebase 명령어는 새로운 base를 만드는 명령어이다. git merge를 통해서 그래프를 병렬적으로 병합한다면, git rebase를 통해서 선형으로 결합한다. 따라서 git merge에 비해 그래프 모양을 단순하게 관리할 수 있다.
rebase는 Pull-Request 과정에서도 활용된다. 내가 PR하기 전에 다른 사람이 PR한 내용을 반영하기 위해서 프로젝트에서 fetch 한 후, rebase 명령어를 통해서 새로운 base를 만들 수 있다.
<pre><code>
$git rebase 커밋ID
</code></pre>