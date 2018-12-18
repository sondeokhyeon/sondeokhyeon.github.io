---
layout: post
title : NodeJS 기초5
categories: NodeJS
tags: [NodeJs,JavaScript]
---

**REPL**   

REPL(레플)이란?  
Read(읽기), Evaluate(평가), Print(출력), Loop(반복)   

자바스크립트는 REPL의 연속으로 이뤄지는데   
아래와 같이 선언 및 할당할 시에 undefined가 나오는건 REPL이 이뤄지고 있기 때문이다. 

    var a = 1; //code
    undefined  //result
    a;         //code
    1          //result
    function b() { 
        return "hello world";
    }         //code
    undefined //result

**이벤트 루프**

태스크 큐에 등록되어 있는 이벤트를 호출스택으로 이동 시켜주는 기능?이다 

**호출 스택(콜스택)** 

자바스크립트의 이벤트는 Stack형태로 저장된다 

    function first() {
        console.log('first')
    }
    function second() {
        console.log('second')
    }
    function third() {
        console.log('third')
    }


**태스트 큐**

특별한 이벤트    
ex   
setTimeout, setInterval, setImmediate,Promise, resolve, reject, async, await, 이벤트 리스너 콜백 등과 같은 특별한 이벤트가 태스크 큐에 등록된다.   
태스크큐는 하나만 있는것이 아니라 내부적으로 여러개가 존재하며 각각 다른 이벤트들이 저장된다. 

**Event Driven**   

이벤트 루프는 여러개의 태스크 큐(태스크 큐는 내부적으로 여러개가 존재 한다)에 우선 순위를 파악해서 호출 스택으로 이동(실행) 해주며 이는 이벤트기반(Event Driven)으로 이뤄진다. 이와 같이 태스크큐에 있는 작업들을 바꿔주는 이벤트 드리븐은 **논블로킹 IO**에 의해서 이뤄진다.   

쉽게 말해 싱글스레드 구조에 의해서 논블로킹IO을 통해서 이벤트 드리븐이 발생한다..!



