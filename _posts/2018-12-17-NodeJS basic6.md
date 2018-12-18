---
layout: post
title : NodeJS 기초6
categories: NodeJS
tags: [NodeJs,JavaScript,기초,입문]
---

최신에 Node의 문법은 ECMA6로 작성한다   
ECMA6는 지원하지 않는 브라우저(ie8은 ES3 스펙 이라고 하며 ie9는 es5 스펙이라고 한다)도 있기 때문에 프론트 개발 할때는 신경(트랜스파일러를 쓰던가... 최신 브라우저만 쓰게 하던가...)써야 한다

**var**   
기존 자바스크립트는 변수를 var라는 키워드로 선언 및 초기화가 가능했다    
(var는 function-scoped이다)   
하지만 ECMA2015(ES6)에서 새로 만들어진 문법으로 목적에 따라 변수를 선언 및 초기화 할 수 있도록 새롭게 만들어 졌다.  
(let과 const는 block-scoped 기반이며 공통점으로는 동일한 변수명으로 재선언이 불가능하다는 점을 가지고 있다.)   

> 참고 https://gist.github.com/LeoHeo/7c2a2a6dbcf80becaaa1e61e90091e5d

**const**   
const는 constant(상수)라는 뜻처럼 말 그대로 한번 바뀌지 않는 상수이다.   
(상수 이기에 선언과 초기화 한번에 이루어져야 한다) 
(객체 안에 있는 값은 변경 가능하다)  

    const a = 1; // 가능
    const b = 2; // 가능
    a = 3;       // error 

**let**   
let은 const 와는 다르게 재할당이 가능하다 

    let a = 1   // 가능
    let a = 2   // error
    a = 3       // 가능

**Template String**   

ES6에서 새롭게 추가된 문법으로 새로운 문자열이 추가되었다.   
사용법은 싱글 쿼테이션('') 혹은 더블 쿼테이션("")이 아닌 문자열은 백틱(``) 으로 감싸는것으로 사용이 가능하다.   
기존에는 문자열을 아래와 같이 만들었다 

    var age = 10
    var name = '홍길동'
    var introduction = '제 이름은' + name +'이고 나이는' + age + '입니다.' // 연산자 활용
    console.log(introduction)

템블릿 문자열은 이런식으로 사용이 가능하다   
(쿼테이션이나 연산자나 기호가 없어져서 가독성이 더 좋다)

    let age = 10
    let name = '홍길동'
    const introduction = `제 이름은 ${name} 이고 나이는 ${age}입니다.`    // 백틱으로 감싼다
    console.log(introduction)











