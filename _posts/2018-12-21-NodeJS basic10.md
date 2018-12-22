---
layout: post
title : NodeJS 기초10
categories: NodeJS
tags: [NodeJs,JavaScript]
---

**require / module**   

require 문법은 다른 JS파일에 자원을 가져올때 사용하는 문법이다  
다른 라이브러리에서 가져올때는 require를 썼었지만 직접 module로서 내보내려면 
export가 필요하다.

    //정의 
    const OK   = '성공'
    const FAIL = '실패.
    module.exports = {
        OK,
        FAIL
    }

    //사용
    const { OK, FAIL } = require('정의.js');
    console.log(Ok)
    console.log(FAIL)


export 타입에 상관없이(객체, 원시타입 등등) 다 내보낼 수 있다.   
export와 require로 인해 모듈화가 가능하다.   
해당 사항들은 react에서도 많이 쓰이므로 알고 넘어가면 매우 좋다!
