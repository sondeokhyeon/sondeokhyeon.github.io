---
layout: post
title : NodeJS 기초5
categories: NodeJS
tags: [NodeJs,JavaScript,기초,입문]
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

이벤트 루프란? 태스크 큐에 등록되어 있는 이벤트를 호출스택으로 이동 시켜주는 기능을 한다

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
ex setTimeout, setInterval, setImmediate,
Promise, resolve, reject, async, await, 이벤트 리스너의 콜백 등과 같은 특별한 이벤트가 등록된다. 






