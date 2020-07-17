---
layout: post
title : NodeJS 기초16
categories: NodeJS
tags: [NodeJs,JavaScript]
comments : true
---

**Node JS의 내장 모듈6**     

노드를 공부하는 사람들은 대부분 http 통신을 하는 서버를 만들고 그 위해서 동작하는 어플리케이션을 만들기 위해 학습을 할것이다.(물론 예외는 있다)   
이때 사용하는 모듈이 http 모듈이며 http 모듈로 인해 노드는 쉽게 웹서버를 만들수 있다. 

**직접 응답**

    const http = require('http'); 
    // http 자원을 준비한다 

    http.createServer((req, res) => {
        console.log('응답완료')
        // 서버를 만든다 
        // 요청은 req(request)에 바인딩 되며
        // 응답은 res(response)에 바인딩 된다.
        res.end('<h1>Hello Node World</h1>')
        // 응답으로 html을 리턴한다
    }).listen(8888, () => {
        console.log('서버 동작중...');
    });

**파일 응답**

index.js

    const http = require('http'); 
    const fs = require('fs');
    // 파일스트림 자원을 준비한다.

    http.createServer((req, res) => {
        fs.readFile('./index.html', (err, data) => {
            // .(현재폴더)에서 index.html을 찾는다.
            // data에 바인딩 된다.
            if (err) {
                console.error(err)
            }
            res.end(data);
            // 응답으로 파일스트림으로 준비한 data를 리턴한다
        });
    }).listen(8888, () => {
        console.log('8888 서버 동작중...');
    });

**index.html**

    <!DOCTYPE html>
    <html lang="en">

    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>Document</title>
    </head>

    <body>
        <h1>hello Node World!!!!!!!!!!</h1>
    </body>

    </html>