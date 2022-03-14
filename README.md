# Git_practice

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
