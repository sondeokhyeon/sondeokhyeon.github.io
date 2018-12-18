---
layout: post
title : NodeJS 기초3
categories: NodeJS
tags: [NodeJs,JavaScript]
---

**util**    
 유틸리티 모듈을 이용해서 형식 문자열을 작성할 수 있다. 그리고 클래스 간에 상속 관계를 만들 수 있다.   

 util 사용시 require를 이용해서 import 후 사용한다    
    function   
        - util.format(format[,%s, %d]) (printf와 비슷하다)   
        - util.inherits(child,parent) (상속 기능)


    var util = require('util')

    var str1 = util.format('%d + %d = %d', 1, 2, (1 + 2));
    console.log(str1)
    var str2 = util.format('%s  %s ', 'hello', 'world!');
    console.log(str2)

    // inherits  상속 
    function parent() { }

    parent.prototype.sayHello = function () {
        console.log('hello world, from parent class!')
    }

    var obj = new parent();
    obj.sayHello();

    function child() { }

    util.inherits(child, parent)

    var ojb2 = new child();
    ojb2.sayHello();


**Event**   
Event란?   
    이벤트(event)는 어떤 사건 의미한다. 
    브라우저에서의 사건이란 사용자가 특정 액션(행동)을 했을때 같은을 의미한다. 
    >http://webclub.tistory.com/340

- node에서 이벤트란?    
  - 클라이언트의 접속 요청
  - 소켓에 데이터 도착
  - 파일 오픈/읽기 완료

- 이벤트 처리
   - 비동기 처리
   - 리스너 함수

EventEmitter  
- ReadLine module
  - class : interface
       - rl.close()
       - rl.pause()
   - events
       - event:'close'
       - event:'line'
       - event:'pause'
       - event:'resume'
       - event:'SIGCONT'
       - event:'SIGINT'

이벤트 리스너란?   
이벤트에 대응되는 함수이다. 

이벤트 핸드로는 개수는 기본 10가지인데 아래의 함수를 이용하면 변경 가능하다   
emitter.setMaxListeners(n)   
emitter.getMaxListeners(n)

리스너 다루기   
emitter.addListener(event, listner) (이거 많이 봤다...)   
emitter.on(event, listner)   (이벤트 시마다 동작하는 함수이다.)   
emitter.once(event, listner) (이벤트를 한번만 동작할 시킬때 사용한다)   

커스텀 이벤트 (이벤트객체에만 사용 가능)   

    var customEvent = new event.EventEmitter();        //custom 이벤트를 준비

    customEvent.on('tick',function() {
    console.log('custom event test')
    });

    customEvent.emit('tick')

    // 커스텀 이벤트, 상속 

    var Person = function(){};

    var util = require('util')
    var EventEmitter = require('events').EventEmitter;
    util.inherits(Person, EventEmitter)

    var p = new Person();
    p.on('howAreYou', function(){
    console.log('custom event inherit)
    });

    p.emit('howAreYou)


    function test() { }
    setTimeout(test, 5000)

    process.on('exit', function () { 
    //exit는 프로그래밍 종료될때 실행할수있도록 준비한다. 
    console.log('Emitter on program exit')
    //지속적으로 동작한다.  
    });

    process.once('exit', function () {
        console.log('Emitter once program exit')
         //한번만 동작한다.
    });

    emitter.removeListener(event, listener) 
    // 이벤트 삭제 
    emitter.removeAllListener(event, listener) 
    // 모든 이벤트 삭제

    process.on('uncaughtException', function (code) { 
        // 이벤트로 예외처리도 가능하다
        console.log('uncaughtException')
    });
