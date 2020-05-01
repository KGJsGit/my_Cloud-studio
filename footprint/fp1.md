# 🖐Hello, Docker!🚢
- 2020.04.27 - 2020.04.30

## 가상환경 구축 및 리눅스 설치
- 처음에 VirtualBox을 이용해서 ubuntu를 설치했으나, 전가상화방식의 VMware 특성상 굉장히 느렸습니다.
- 넉넉하게 컴퓨터자원을 할당해주어서 그나마 수월하게 할 수 있었습니다.
- 더 좋은 방법을 없을까???...
  <p align = 'center'>
    <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/ubuntu.JPG"><br>
    (너무 느려서 돌아버림...)
  </p>

## Docker
- 도커는 Immutable Infrastructure라는 패러다임에서 출발한 프로젝트입니다.
  - Immutable Infrastructure : 호스트 OS와 환경을 분리해서 한 번 설정한 환경은 변하지 않는다는 개념
- 도커의 가상화 방식
  - Docker 엔진위에 서버운영을 위한 프로그램과 라이브러리만 docker 이미지에 설치하고 OS자원은 호스트OS와 공유합니다.
  - 즉, 하드웨어를 가상화하는 계층이 없기 때문에 속도가 무진장 빠릅니다. (호스트 OS와 거의 동일할 정도...)
- 도커의 장점
  - 도커는 서비스 운영환경을 이미지를 사용하기 때문에 이미지 자체만 관리하면 됩니다.
  - 도커는 이미지 하나로 다른 환경을 계속 찍어낼 수 있습니다. 따라서 자동확장(Auto scaling)을 손쉽게 서비스합니다. 
  - 가볍고 강건하며, 테스트가 매우 쉽습니다.
  - 인터넷이 연결되어 있다면 docker hub에서 이미 만들어진 다양한 이미지를 받아오거나 배포할 수 있습니다!

## Docker 설치 및 실습
- [docker](https://github.com/docker/toolbox/releases)를 다운로드하여 실행 -> docker quickstarter & oracle VirtualBox 생성
  <p align = 'center'>
    <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/docker1.JPG"><br>
    (고래가 나오면 성공!)
  </p>
- docker를 이용해서 docker hub의 ubuntu 이미지 설치
  <p align = 'center'>
    <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/doc1.JPG"><br>
    <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/doc3.JPG"><br>
    (VirtualBox와는 비교도 안되게 빠르다!!)
  </p>
- 마찬가지로 mysql까지 설치하고 확인!
  <p align = 'center'>
    <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/doc4.JPG">
    <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/doc5.JPG"><br>
    (컨테이너 위에서 정상 작동하는 mysql)
  </p>
  
## 느낀점
- 도커가 왜 컨테이너 스킬의 업계표준으로 자리잡을 수 있었는지 간접적으로 느낄 수 있었습니다.
- 하나의 서버에 다수의 프로그램을 올릴 때에 도커를 이용하면 훨씬 쾌적하겠네요!! 적용해봐야겠습니다.

