---
layout: post
title : NodeJS 기초11
categories: NodeJS
tags: [NodeJs,JavaScript]
commnet : true
---

**Global 객체**
  
브라우저 쓰이는 JavaScript에서는 전역 객체는 window이다.    
하지만 Node.js 에서는 window를 쳐보면 나오지가 않는데 Node.Js에서는 전역 객체가 Global로 바뀌었기 때문이다. 

**Node에서 Window객체의 자원을 사용하려면 global로 대신해서 사용하자**


## Node JS의 내장 모듈
require를 통해서 변수에 담아 사용한다

    const modules = require('modules')
    
모듈 종류 

 - os(운영체제 관련 모듈)
 
        const os = require('os'); // os 모듈 준비
        os.arch()     // 아키텍처
        os.platfrom() // OS종류
        os.type()     // OS.Type()
        os.homedir()  // homedirectory
        os.tempdir()  // tempdirectory
        os.cpus()     // CPU정보 

-   path(경로관련 모듈)

        const path = requrie('path'); // path 모듈 준비
        path.sep                      // 운영체제 경로 구분자
        path.dirname(__filename)      // 파일의 경로 
        path.extname(__filename)      // 확장자 이름
        path.basename(__filename)     // 파일 이름
        path.parse(__filename)        // 구조화 출력
[//]: <>  (path.relative<'c:\\temp', 'c:\\'>   // 상대경로 추적)
[//]: <>  (path.join<__dirname, '..', '..'>    // 경로합치는 함수(절대경로 인식안됨)
[//]: <>  (      path.resolve<__dirname, '..', '..'> // 경로합치는 함수(절대경로 인식됨)
[//]: <>  ( <중간에 /이 있으면 최상위로 인식>)
        
