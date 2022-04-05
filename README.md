# Git_practice
Person A가 자신의 디렉토리에서 작업을 하다가 branch A로 push를 하고, 이후 Person B가 자신의 디렉토리에서 작업을 하다가 branch B로 push한 경우를 simulating해보았다. 이후 merge작업을 통해서 branch A와 branch B가 병합되어 B가 마지막으로 commit한 내용으로 작업물이 합쳐졌다.
Person A는
HelloWorldFromA라는 텍스트 파일에 HelloWorld를 입력하였다.
Person B는
HelloWorldFromB라는 텍스트 파일에 HelloWorld\nHelloWorld를 입력하였다.
현재 merge 작업을 통해 branch A의 내용이 변경된 것을 확인할 수 있다.

## Branch
독립적으로 어떤 작업을 진행하기 위한 개념
동일한 소스코드를 기반으로 서로 다른 사람들이 개발을 하다보면 다양한 버전의 코드가 생길 수 있다. 이때 사용할 수 있는 것이 브랜치(Branch)이다.
각각의 브랜치는 다른 브랜치의 영향을 받지 않으며, 이는 여러 작업의 동시에 진행을 가능하게 한다.

$git init

$git remote add origin "https://github.com/ChoSeoyoung/Git_practice.git"

$git add . 

$git commit -m "Initial commit"

$git branch BranchName
  
$git push origin BranchName
