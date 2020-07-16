---
layout: post
title : NodeJS 기초15
categories: NodeJS
tags: [NodeJs,JavaScript]
comments : true
---

**Node JS의 내장 모듈5**     

노드에서는 이벤트는 기본적으로 이벤트리스너를 통해서 만들어진다.   
하지만 노드에서 미리 만들어놓은 이벤트 뿐만이 아니라 개발자가 스스로 이벤트가 발생할시 대응하는 이벤트리스너를 만들 줄도 알아야 한다.   


eventListener


    // Event 등록하기 

    const EventEmitter = require('events');
    // Event module 로드 한다.
    const myEvent = new EventEmitter();
    // 새롭게 이벤트를 만든다. 

    myEvent.addListener('발생!', () => {
        console.log('이벤트 발생')
    });

    myEvent.on('요청', () => {
        console.log('응답')
        // 계속 반복되는 이벤트를 등록하는 함수이다.
        // 요청시 응답 한다던가...?
        // addListener랑 동일한 개념이다.
    });
    
    myEvent.once('init', () => {
        console.log('초기화 되었습니다.')
        // 한번만 실행할 이벤트를 등록한다
        // init 이라던가 destroy 라던가..?
    });


    // 이벤트 호출하기 

    myEvent.emit('요청')
    // 커스텀 이벤트를 호출한다.
    myEvent.emit('init')
    // 커스텀 이벤트를 호출한다.


    // 이벤트 확인하기 

    myEvent.listenerCount('요청')
    // '요청' 이라는 이벤트로 몇개가 등록되어있는지 확인한다.


    // 이벤트 제거 하기 

    myEvent.removeListener('init')
    // 'init' EventListener를 지운다.


    // 이벤트 한번에 지우기 

    MyEvent.removeAllListener('요청')
    // '요청' 이라는 이벤트를 다 지운다.

    


