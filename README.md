# Git_Practice

## 사용자 정보 등록, 기본적인 설정
$git config --global user.name “홍길동”
$git config --global user.email “hong@gil.dong”
$git config --global color.ui true

## 지역 저장소 초기화
우선 해당 디렉토리로 이동한다.
$cd hello
$git init
위 명령어 실행결과, .git파일이 생성되는데 해당 파일에 히스토리 정보가 관리된다.
.gitignore을 이용하여 관리 대상 파일 선택 적용 가능하다.

# 저장공간의 논리적 분할
-working directory(작업 공간): 실제 파일을 수정하거나 생성하는 공간이다. 현재 작업 중인 소스코드들을 담고 있으며, 작업 폴더에서 .git 디렉토리를 제외한 나머지 부분이다.
-staging area(임시 저장 공간, 인덱스, 스테이지): commit하려는 파일의 추적 상태 정보들만 기록한다. stage가 만들어진 이유는 commit을 빠르게 처리하고, 충돌을 관리하기 위해서이다.
-repository(실제로 저장하는 공간): 스테이지에서 대기하고 있던 파일들으 버전으로 만들어 저장하는 곳
    - Local repository: 현재 내가 사용하고 있는 내 디바이스에 저장되는 저장소
    - Remote repository: 원격 서버에 저장되고 관리되는 저장소

## 스테이지 영역에 추가
현재 디렉토리의 모든 변경 내용을 스테이징 영역으로 넘기고 싶을 때
$git add . 
특정 파일을 스테이징 영역으로 넘기고 싶을 때
$git add hello.html

## commit(staging area->repository)
$git commit -m 'add hello.html'

## 커밋 로그 확인
$git log

## 로컬 레포지토리->원격 레포지토리
$git push -u origin main