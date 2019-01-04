---
layout: post
title : NodeJS 기초14
categories: NodeJS
tags: [NodeJs,JavaScript]
comments : true
---

**Node JS의 내장 모듈4**     

 - fs(File System 모듈)   
    브라우저상에서 돌아가는 자바스크립트와는 다르게 Node는 직접 OS상의 File System 접근이 가능하다.

        const fs = require('fs'); 

        // 파일 쓰기 
        fs.writeFile('./test.txt, '문자입력' (err,data) => {
          if(err) {
            console.error(err)
          }
        });

        // 파일 읽기
        fs.readFile('./test.txt', (err, data) => {
            if(err) {
                console.error(err)
            }
            console.log(data.toString());
            // toString()을 안해주면 버퍼가 출력된다. 
        })


