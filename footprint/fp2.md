# 👨‍💻 우분투랑 친해지기 🥰
- 목표 : 우분투 명령어 익히기 및 간단한 실습
- 2020.05.05 ~ 2020.05.08

## 우분투 기본 패키지 설치
- apt update && apt upgrade : 우분투 업그레이드
- apt install vim : VI에디터 설치
- apt install net-tools : 통신 패키지 설치 
- apt install sudo : sudo 명령어 설치
  <p align = 'center'>
    <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/f2-2.JPG">
    (잘 설치가 된 것을 볼 수 있다.)
  </p>
  
## 우분투 기본 명령어
- ls : 해당 디렉토리에 있는 파일의 목록 나열
- cd : 디렉토리를 이동
- pwd : 현재 디렉토리의 전체 경로를 출력(print working dirictory)
- rm : 파일이나 디렉토리를 삭제
- mv : 파일과 디렉토리의 이름을 변경하거나 위치 이동
- mkdir : 새로운 디렉토리 생성
- rmdir : 디렉토리 삭제
- cat : 텍스트로 작성된 파일을 화면에 출력
- touch : 크기가 0인 새 파일을 생성, 이미 존재하는 경우 수정시간을 변경

## 파일과 디렉토리의 소유 및 허가권
- /는 최상위 디렉토리인 루트디렉토리를 의미하며 모든 디렉토리의 시작점입니다.
- home 디렉토리는 리눅스 사용자들의 개인공간입니다.
- 보통 일반사용자는 별도의 설정이 없는 경우 home 및에 자신의 아이디로 된 디렉토리가 배정됩니다.
<p align = 'center'>
     <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp2/f2-3.JPG">
</p>

## 디렉토리 및 파일에 대한 실습
- 사용자를 생성해서 아래의 그림처럼 디렉토리와 파일을 만들어보자!
<p align = 'center'>
     <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/f2-1.png">
     <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp2/f2-5.JPG">
</p>

- su ko를 이용해서 내 계정(ko)으로 진입
- ls와 cd를 사용해서 home/ko 디렉토리로 이동 후
- mkdir을 이용해서 document, download, bin, workspace 디렉토리 생성
- workspace디렉토리로 이동해서 touch 명령어를 통해 Hello.txt 파일 생성

## 느낀점
- Windows prompt 명령어와 비슷한 점이 많아서 쉽게 익힐 수 있었습니다.
- 마치 해커가 된 느낌..? 👨‍💻👨‍💻
