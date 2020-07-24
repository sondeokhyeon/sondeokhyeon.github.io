---
layout: post
title : 도커 명령어
categories: 기타
tags: [기타, 도커]
comments : true
---

#### docker

1. images - 소유하고 있는 images들을 확인

2. build - docker image화 Dockerfile 필요
   [doc](https://docs.docker.com/engine/reference/commandline/build/)  
   docker build [option] path | url
3. create - image를 container로 만듬  
   [참고](http://pyrasis.com/book/DockerForTheReallyImpatient/Chapter20/05)  
   docker create -it --name name -p hostport:containerport image:version
4. start - container 를 실행할때 사용

5. run - create와 strat를 한번에 실행

6. stop - container를 정지

7. kill - container process를 죽임

8. pull - docker image를 가져옴

9. commit - docker container를 이미지화 시킴

10. push - docker image를 hub에 올림

11. inspect - 실행중인 container의 상태를 확인 가능

12. exec - 실행중인 container에 command를 실행 (ex docker exec -it <container-id> /bin/bash || docker exec <container-id> nginx reload)

13. port - 실행중인 포트를 확인

14. ps - 실행중인 container를 확인

15. ps -a - 모든 container를 확인

16. rm - container를 삭제

17. rmi - image를 삭제

18. login - docker hub login

#### docker-compose

19. docker-compose      - docker-compose를 실행한다 (컨테이너들 같이 시작) (-d 옵션을 주어서 데몬형태로 실행해야 한다)

20. docker-compose down - docker-compose를 종료한다 (컨테이너들 같이 종료)

