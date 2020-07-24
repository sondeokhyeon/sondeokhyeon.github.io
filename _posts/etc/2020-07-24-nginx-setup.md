---
layout: post
title : nginx
categories: 기타
tags: [기타, nginx]
comments : true
---

#### nginx

리액트로 실습 후 가장 많이 사용되는 웹서버인 nginx를 써보았다. 
간편한 세팅방법과 강력한 기능으로 많이 가장 많이 쓰인다는 글을 보았는데 사실 인 듯 하다 ㅎㅎ 

HostPC에 설치하고 싶지 않아서 그냥 docker로 설치를 설치했기에 (window에서 직접 실행을 안해봐서 window는 잘 모르겠다)여기다가는 그냥 했던 방법을 기술한다. 

적당한 폴더를 만들어서 docker-compose.yml을 만든 후 docker hub에서 nginx 검색한 후 거기 적혀 있는대로 작성하고 실행하면 되는데 필요해 따라서 수정해주면 될꺼 같다

      web:
      image: nginx
      volumes:
      - ./templates:/etc/nginx/templates
      ports:
      - "8080:80"
      environment:
      - NGINX_HOST=foobar.com
      - NGINX_PORT=80

(yml을 띄어쓰기를 제대로 안하면 오류가 나니까 적절한 확장프로그램을 사용하는게 좋다)

docker는 container를 내리면 데이터가 다 없어지므로 데이터를 보관하고 싶다면 volume기능(공유폴더)이 필수적이다.  
(volume을 활용하면 host에서 코딩하고 container에서 실행할 수 있다)  
윈도우 8.1에서 실행하는데 volume을 세팅이 잘 안되어서... 고생좀했다..  
(이 부분은 따로 작성했다..)

그리고 정상적으로 실행되는거 확인했는데
그냥 터미널로 명령어 쳐서 이리저리 옮겨다니는거보단 ssh로 하는게 편하고 좋을꺼 같아서 
vscode확장프로그램을 찾아보던 중 Remote - Containers를 발견했다 ~~와 쩐다~~

성공적으로 container 실행했고 성공적으로 확장프로그램을 설치를 하였다면   
vscode내에서 f1을 눌러보자 거기서 remote 만 쳐도 이러저러한 것들이 잔뜩 나오는데 
거기서 **remote-containers:aTTach To Running Container...** 을 누르면 실행중인 컨테이너가 나온다.  
컨테이너를 클릭하고 들어가면 에디터로 SSH 접속한거처럼 탐색기도 사용가능하고 터미널도 docker 터미널이 된다.  ~~헿 너무 좋아~~  

nginx 세팅 파일을 열어보면 아래와 같이 작성되어있다. (경로는 /etc/nginx/conf.d/)

    server {
      listen       80;
      listen  [::]:80;
      server_name  localhost;

      #charset koi8-r;
      #access_log  /var/log/nginx/host.access.log  main;

      location / {
            root   /usr/share/nginx/html;
            index  index.html index.htm;
      }

      #error_page  404              /404.html;

      # redirect server error pages to the static page /50x.html
      #
      error_page   500 502 503 504  /50x.html;
      location = /50x.html {
            root   /usr/share/nginx/html;
      }
      ....
    }



여기서 기존 location 주석처리하고(주석이 #이다) location을 수정한다. 

    location / {
        root 폴더경로
        index index 파일이름
    }


React를 빌드 후 생긴 파일을 경로와 파일이름을 잡아주면 실행이 잘 된다...아..?  
서브페이지에서 자꾸 404 에러 난다... -_-
찾아보니 location에 아래의 옵션을 주면 사라진다고 해서 넣어보니 오 정말 없어졌다

    try_files $uri $uri/ /index.html;

나중에 서브도메인도 세팅해봐야겠다