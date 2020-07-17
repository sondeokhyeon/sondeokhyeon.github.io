---
layout: post
title : NodeJS 기초13
categories: NodeJS
tags: [NodeJs,JavaScript]
comments : true
---

**Node JS의 내장 모듈3**     

 - crypto(암호화 모듈)   
   데이터를 암호화를 해야하는 경우가 있다 그럴 때 사용하는 모듈이다.

        // 단방향 암호화 
        const crypto = require('crypto'); 
        crypto.createHash('sha512').update('아규먼트').digest('base64'))
        // 해쉬화(단방향) 방식으로 암호화한다
        // 비밀번호는 할떄 적당하다 


        // 양방향 암호화
        const crypto = require('crypto');
        const cipher = crypto.createCipher('aes-256-cbc' 'keyValue');

        // 암호 모듈을 만든다 알고리즘 방식 aes-256-cbc 방식으로 만든다
        // 암호의 키값도 지정한다 (키값은 복호화 할때도 쓰인다)
        // (참고 http://brownbears.tistory.com/302) 

        let result = cipher.update('비밀번호', 'utf8', 'base64')
        // 비밀번호(utf-8)를 base64 암호문으로 바꾼다

        result += cipher.final('base64');
        // 암호화를 마무리 짓는다 그후 암호화 값은 변수에 담긴다 

        const decipher = crypto.createDecipher('aes-256-cbc', 'keyValue')
        let result2 = decipher.update(result, 'base64', 'utf8')
        // ase64 암호문을 비밀번호(utf-8)으로 바꾼다
        result2 += decipher.final('utf-8');
        // 암호화를 마무리 짓는다 그후 암호화 값은 변수에 담긴다 


  <a href="https://nodejs.org/api/crypto.html">공식 API</a>