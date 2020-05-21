# 🛠 웹서버 구축하기 (feat. Debian, nginx, php) 😎
- 목표 : 간단한 웹서버 환경 구축
- 2020.05.18 ~ 2020.05.21

## 웹페이지는 어떻게 우리에게 보여지게 되는 것일까?
- 우리가 브라우저에서 특정한 파일(웹페이지)를 원한다고 명령하면 HTTP를 통해 웹서버에 파일을 요청합니다.
- 올바른 HTTP Request가 웹서버에 도착하면 HTTP 서버는 요청된 파일(홈페이지)를 HTTP response로 보냅니다.
- 즉, 웹서버를 구축한다는 것은 사용자에게 파일(홈페이지)을 서비스 받을 수 있도록 하는 것입니다!
- 웹서버는 하드웨어 형태로 존재하는게 일반적이지만, 클라우드를 활용하면 무형의 웹서버를 굴릴 수 있습니다!
  <p align = 'center'>
   <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp4/fp4_0.png">
  </p>

## 클라우드를 위한 리눅스 웹서버의 종류
- 대표적으로 <b>Apache</b>와 <b>Nginx</b>가 있습니다.
- <b>Apache</b>
  - Apache는 가장 유명한 웹 서버 프로그램이며, 강력한 확장성과 긴 역사에 의한 많은 레퍼런스가 특징입니다.
  - Java/spring 기반 웹에선 Apache Tomcat이 거의 필요하기 때문에 국내 웹 서버의 대다수를 차지합니다.
  - Thread-Process 구조로 클라이언트 request 하나당 thread 하나로 처리합니다. 그렇기 때문에 요청이 많아질수록 자원낭비가 심해져서 성능이 몹시 저하됩니다.
  - 이때문에 [C10k Problem](https://en.wikipedia.org/wiki/C10k_problem)와 같은 이슈가 존재합니다.
  <p align = 'center'>
   <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp4/fp4_1.gif">
   </p>
- <b>Nginx</b>
  - Nginx는 위에서 얘기한 C10K Problem을 해결하기 위해 나온 오픈소스 웹 서버 프로그램입니다.
  - Nginx는 Event-Driven구조로 여러개의 커넥션을 모두 잡아와서 Event-Handler에 넣고 먼저 처리되는 것부터 로직을 실행합니다.
  - 역사가 오래되지 않았지만 좋은 성능으로 아파치와의 점유율 싸움에서 지지 않고 있습니다.
  <p align = 'center'>
   <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp4/fp4_2.gif">
  </p>
  - <b>Nginx로 웹서버를 구축해봅시다!</b>
  
## Debian-buster + Nginx로 웹서버를 만들기
- 우선 docker를 실행시키고 Debian-buster 컨테이너를 만듭니다.
- Debian-buster를 쓰는 이유는 안정적이며 최신의 OS환경을 가지고 있기 때문입니다.
  ```
  $ docker run -it --name [컨테이너 명] -d -p 80:80 dabian:buster
  ```
- run 명령어는 create + start + attach를 가집니다.
- -p 80:80에서 앞의 80은 host port를 뒤의 80은 container port를 의미합니다.
- Windows와 docker 사이에 Oracle VirtualBox가 존재하기 때문에 요청이 바로 도커 컨테이너로 진입할 수 있도록 Port Forwarding을 해줍시다.
  <p align = 'center'>
   <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp4/fp4_4.JPG">
  </p>
- ctrl+p+q로 debian-buster를 dettach한 후 컨테이너가 잘 만들어졌나 확인해봅시다.
  ```
  $ docker ps -a
  ```
  <p align = 'center'>
   <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp4/fp4_3.JPG">
   (필자는 debserver라는 이름으로 만들었다.)
  </p>
- davian-buster에 attach해서 기본 패키지들을 설치한 뒤 nginx를 설치합시다.
  ```
  $ apt update                  // apt 저장소 업데이트
  $ apt upgrade                 // 패키지를 최신 패키지로 업그레이드
  $ apt install vim             // vim editor 설치
  $ apt-get install net-tools   // 네트워크 관련 정보 조회기능
  $ apt install sudo            // sudo 명령어 설치
  
  $ apt-get install nginx       // nginx 설치
  ```
- 잘 설치가 되었다면 service명령어를 통해서 nginx를 구동시킵니다.
  ```
  $ service nginx start
  $ service nginx status        // 잘 구동되는지 확인하는 명령어
  ```
- 웹 브라우저를 켜고  ```localhost``` 로 들어가서 nginx가 잘 구동되는지 확인해봅시다.
  <p align = 'center'>
   <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp4/fp4_9.JPG">
  </p>

- 이제 php를 연동시켜봅시다. 7.4은 불안정하니 7.3으로 설치하겠습니다.
  ```
  $ apt-get -y install php7.3 php-mysql php-fpm php-cli php-mbstring php -curl php-gd
  ```
- 이제 nginx와 연동해봅시다. 몇 가지 파일을 수정해야합니다. 첫번째로 default 파일입니다.
  ```
  $ cd /etc/nginx/sites-available
  $ vim default
  ```
  <p align = 'center'>
   <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp4/fp4_5.JPG"><br>
    (노란부분이 주석처리가 되어있는데 주석을 뺴주면 된다.)
  </p>
- 다음 수정 파일은 php.ini입니다.
- vim에서 ```/```를 사용해서 원하는 키워드로 빠르게 이동할 수 있습니다.
  ```
  $ cd /etc/php/7.3/fpm
  $ vim php.ini
  ```
  <p align = 'center'>
   <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp4/fp4_6.JPG"><br>
   (OFF -> ON)
   <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp4/fp4_7.JPG"><br>
   (1 -> 0)
  </p>
- 연동이 잘 되었는지 확인하려면 nginx를 restart하고 php를 start해주면 됩니다.
  ```
  $ service nginx restart
  $ service php7.3-fpm start
  ```
- 이제 간단한 파일을 만들어서 브라우저에 띄워봅시다!
  ```
  $ cd /var/www/html
  $ vim test.php
    <?php
    phpinfo();
    ?>
  ```
 <p align = 'center'>
   <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp4/fp4_8.JPG">
  </p>
  
 ## 느낀점 
 - 간단한 방법으로 가상환경에서 웹서버를 만들어보니 신기했습니다. 다양하게 확장해서 사용해보고 싶습니다.
 - 가면 갈수록 느끼지만 리눅스OS는 대단한 물건이네요!
