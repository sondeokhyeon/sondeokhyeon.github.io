---
layout: post
title : 도커 window8 Volume
categories: 기타
tags: [기타, 도커]
comments : true
---

도커 window8 Volume 문제 

Window8 또는 8.1을 쓰는데 요즘 ~~누가 윈도우8을 쓰나~~ Docker를 Volume이 마운팅이 안되어서 고생했다.  
검색해도 잘 나오는거 봐서는 윈도우 10에서는 잘 발생안하는것으로 보인다...  
(실제로 원격으로 리눅스에서 똑같이 세팅을 했는데 잘되었다... docker쓸 때 윈도우 안 좋다고 하더니.. 리얼이었다. 흑흑)

      version : "3.3"
      services:
         web:
            image: nginx
            volumes: 
                  - //D/project/docker/templates:/templates
            ports: 
                  - "8080:80"
            environment: 
                  - NGINX_PORT=80


위와 같이 docker-compose.yml을 작성 후 실행했는데 기능은 문제가 없는데 자꾸 볼륨이 마운팅이 안되었다.   
검색만 2시간넘게 진행한 결과 VM 기본 세팅 경로가 이상해서 였다는 사실을 알게되었다...~~아놔~~  
그래서 해당 값을 수정했더니 이제는 정상적으로 작동한다!  
(동적으로 소스코드를 넣고 뺴고 싶은데 Volume이 작동을 안하면 매우번거로우니 해결해야 할 문제였다.. )

자세한 방법은 URL통해서...   
역시나 답은 구글링! 특히 [스택오버플로우](https://stackoverflow.com/questions/44054058/docker-volumes-mounting-on-windows-8-is-not-working?answertab=active#tab-top)이다.  

실행할 때 환경변수도 필요한 모양인데 해당파일 방법도 위에 적혀 있다.  
(COMPOSE_CONVERT_WINDOWS_PATHS=1 이 필요한 모양이다... )