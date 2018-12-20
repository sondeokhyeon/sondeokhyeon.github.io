---
layout: post
title : NodeJS 기초1
categories: NodeJS
tags: [NodeJs,JavaScript]
---
*NodeJS란?*

자바스크립트 엔진을 기반으로 만들어진 서버 사이드 플랫폼이다!    
즉 웹브라우저에서 동작하던 자바스크립트로 서버 개발 할수 있게 만드는 플랫폼이다.   
(일렉트론을 쓰면 응용소프트웨어도 만들수 있다 os도 안타는..)  
특징으로는 단일 스레드, 뛰어난 확장성, 비동기 I/O 등이있다.  
기본적으로 노드를 사용하기 위해서는 노드를 설치를 해줘야 하며 npm도 설치해줘야 한다  
(npm은 node package manager의 약자)  
<a href="https://nodejs.org/en/">공식 홈페이지</a>에서 다운로드 가능하다 
버전은 LTS버전(안정화버전)과 최신버전이 있다   
용도에 맞춰 다운로드 후 설치하는데 설치도중 설치 옵션 중 Add To Path를 체크 후 설치하도록 하자   
(리눅스는 설치방법이 다르다 <a href="https://nodejs.org/en/download/package-manager/">참고</a>)  
os에 맞춰서 설치가 완료되면 terminal 혹은 cmd에 node 를 쳐보자 오류가 없다면 정상적으로 설치완료!

### node 주요 기본모듈
별도의 설치 과정 없이 사용할 수 있는 모듈로 Node.js와 함께 설치된다. 

프로세스 환경
os, process, cluster

파일과 경로, URL
fs, path, URL, queryString, stream

네트워크 모듈
http, https, net, dgram, dns 

전역객체 - global 모듈에 속하는 객체와 함수로 모듈 로딩 과정없이 사용할 수 있다.   
console - console을 으용하여 콘솔화면에 내용을 출력할 뿐만 아니라 실행 시간을 측정할 수 있다.   
util    - 유틸리티 모듈을 이용해서 형식 문자열을 작성할 수 있다. 그리고 클래스 간에 상속 관계를 만들 수 있다.   
event   - 이벤트를 다루는 EventEmitter의 특징과 이벤트를 다뤘으며 유틸리티 모듈의 상속을 이용해서 커스텀 이벤트로 다룰 수 있다.   
timeout - 타이머 함수인 setTimeout()이나 setInterval() 함수를 이용해서 일정 시간 뒤에 동작하거나 주기적으로 동작하는 기능을 작성할 수 있다.   
Buffer   
require   
__filename   
__dirname   
module   
export   

---

### console Hello World
    console.log('hello World')

### 웹 응답 Hello World 
    const http = require('http');

    http.createServer(function (request, response) {
        response.writeHead(200, { 'Content-type': 'text/html' });
        response.end('<h1>Hello World</h1>')
    }).listen(3000);