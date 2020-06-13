# 🚢 Docker 200% 활용하기 😎
- 목표 : Image생성과 Dockerhub 활용하기
- 2020.06.08. ~ 2020.06.12.

## Docker의 장점을 가장 잘 살리는 방법
- Docker의 가장 큰 강점은 Environment에 구애받지 않고 Applicaition을 실행할 수 있다는 것입니다.
- Docker는 하드웨어와 OS가 고정되어있다고 가정하고, 그 위에 Image를 덮어서 실행환경을 관리합니다.
- 그렇다면 내 Container를 Image로 만들어서 다른 곳에서 작업하는 팀원에게 전달하면 간편하게 테스팅을 할 수 있겠네요!?
- 이렇게 Image화 하는 것을 Dockerizing이라고 합니다!
<p align = 'center'>
    <img src = "https://github.com/koptimizer/my_Cloud-studio/blob/master/pics/fp6/fp6_1.png" width = "600px"><br>
  </p>

## Image의 천국 : DockerHub
- Github이 오픈소스의 성지이듯, DockerHub는 Docker image들의 성지입니다.
- 각종 Docker Image가 존재하고 모두가 접근가능한 public image의 수는 약 3.6m 이상입니다!
- 그 누구라도 자신의 Image를 올릴 수 있습니다.
- 간단하게 Dockerizing을 해보고 DockerHub에 업로드해봅시다!
<p align = 'center'>
    <img src = "https://github.com/koptimizer/my_Cloud-studio/blob/master/pics/fp6/fp6_2.png"><br>
    (도커는 사실상 업계의 표준이 되었다.)
  </p>
  
## How to Dockerizing?
- 우선 Docker image가 저장될 폴더를 만들고 사용권한의 쓰기 및 읽기 속성을 체크해줍니다.
  <p align = 'center'>
   <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp6/fp6_3.JPG">
   </p>
   
- 해당 디렉토리로 이동해서 Dockerfile을 생성하고 원하는 환경을 코딩합니다. (확장자X)
- Dokcerfile의 언어는 구글의 go입니다.
  <p align = 'center'>
   <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp6/fp6_4.JPG">
   </p>
- Docker terminal을 켜고 해당 디렉토리로 이동한 뒤 Dockerfile을 빌드해줍니다.<br>
``` $ docker build --tag [계정명]/[이미지명]:0.1```
  <p align = 'center'>
    <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp6/fp6_5.JPG">
  </p>
- Dockerfile이 이미지로 잘 빌드되었는지 확인하기 위해 해당 이미지로 컨테이너를 만들어봅시다.
- ```$ docker run --name mydocker -d -p 80:80 [계정명]/[이미지명]:0.1```
    <p align = 'center'>
      <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp6/fp6_7.JPG">
   </p>
- 컨테이너가 잘 가동되는지 확인하기 위해 브라우저를 켜서 localhost로 들어가 봅시다!
   <p align = 'center'>
    <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp6/fp6_8.JPG">
   </p>
   
## Dockerhub에 push하기
- https://hub.docker.com/
- Docker hub에 회원가입한 뒤, 이메일 인증을 완료해줍니다.
- Docker terminal에서 ```$docker login```을 통해 Username과 password를 입력해줍니다.
    <p align = 'center'>
    <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp6/fp6_9.JPG">
   </p>
- Docker Hub에 위에서 만들어본 image를 push해줍니다.
- ```$ docker push [계정명]/[이미지명]```
    <p align = 'center'>
    <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp6/fp6_11.JPG">
   </p>
- 그 후 Docker Hub 사이트에 들어가보시면 잘 push된 것을 확인해 볼 수 있습니다.
  <p align = 'center'>
    <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp6/fp6_10.JPG">
   </p>
   
## 발생했던 이슈들
- 딱히 어려움은 없었으나... 이메일 인증을 안하면 Docker Hub에서 push가 잘 되었는지 확인이 안되네요. 이메일인증 필수!

## 느낀점
- 도커가 컨테이너 스킬의 표준으로 자리잡을 수 있었던 이유를 느껴볼 수 있었습니다.
- 배포와 테스트 관점에서 정말 편리한 기술이라는게 다시 한번 체감되었습니다.
