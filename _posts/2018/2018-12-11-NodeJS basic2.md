---
layout: post
title : NodeJS 기초2
categories: NodeJS
tags: [NodeJs,JavaScript]
---
**process - 어플리케이션 실행정보 객체**

* property
    * env                 : 애플리케이션 실행환경 ()
    * version             : Node.js 버전
    * arch, platform      : CPU와 플랫폼 정보
    * argv                : 실행 명령 파라미터   
    (node helloworld.js 3,5 시 process argv로 꺼내서 사용가능 var i = process.argv[2])
*  event
    * exit                : 애플리케이션 종료 이벤트
    * beforeExit          : 종료되기 전에 발생하는 이벤트
    * uncaughException    : 예외 처리되지 않은 예외 이벤트
* function 
    * exit                : 애플리케이션 종료
    * nextTrick           : 이벤트 루프 내 동작을 모두 실행 후 콜백 실행

**CODE**

    console.log(process.env)
    console.log(process.version)
    console.log(process.arch)
    console.log(process.platform)


**console - 콘솔(터미널) 출력 및 파일저장 또는 실행시간 측정 관련 객체**   
(로깅을 만들수 있다.)    

* loging function (level) 
    * console.log()
    * console.warn()
    * console.error()
    * console.inf%o()   

* **console 출력시 주의할점**   
    객체형 타입(object)은 console.log('var', obj)처럼 사용해야 잘보인다 
    console.log('var'+ obj)를 넣으면 object object 나온다

**CODE**

    console.time('TIMER');  // 시작시간 
    var sum = 0;
    for (var i = 0; i < 10; i++) {
        sum += i;
    }
    console.log('sum : ' + sum)
    console.timeEnd('TIMER') // 종료시간

    console.log("hello")
    console.warn("hello")
    console.error("hello")
    console.info("hello")
