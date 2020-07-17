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

 - util(유틸 모듈)   
    util 모듈은 Node Js의 API를 지원하도록 준비된 내장 모듈이다.   
    유용한 함수가 여럿 준비되어 있다. 

        const util = require('util');
        const crpyto = require('cryto');
  
        const dontusenme = util.deprecate((x, y) => {
          console.log(x + y)
        }, '이 함수는 2018년 12월 까지만 지원합니다' );

        dontusenme(1, 2);
        // 결과 
        // 3
        // DeprecationWarning: 이 함수는 2018년 12월 까지만 지원합니다.
        
        // 해당 함수는 API를 만들때 쓰일만한 함수이다 참고~
 
        const randomBytesPromise = util.promisefy(crypto.randomBytes);
        const pdkdf2Promise = util.promisefy(crypto.pbkdf2);
        
        randomBytesPromise(64)
          .then((buf) => {
            const salt = buf.toString('base64')
            return pdkdf2Promise('패스워드', salt, 651395, 64, 'sha512')
          })
          .then((key) => {
            console.log(Key.toString('base64'))
          })
          .catch((err) => {
            console.error(err)
          })

          (async () => {
              const buf = await randomBytesPromise(64);
              const salt = buf.toString('base64');
              const key = pdkd2Promise('패스워드', salt, 651395, 64, 'sha512')
          })
    
  - fs모듈

        const fs = require('fs');

        // 파일 쓰기
        const writeStream = fs.createWriteStream('./text.txt');
        // 파일 wirteStram을 준비한다.

        writeStream.on('finish', () => {
          // 파일쓰기가 끝나면(finish) 발생하는 이벤트
          console.log('파일 쓰기 완료')
        })

        writeStream.write('테스트입니다.')
        writeStream.write('테스트입니다2.')
        writeStream.end(); 
        // 스트림을 닫는다.

        // 파일 읽기
        const readStream = fs.createReadStream('./text.txt', {highWaterMark : 16}); 
        // highWaterMark는 바이트 숫자를 지정

        const data = [];
        // 배열을 준비
        readStream.on('data', (chunk) => {
            //데이터를 읽을(스트림 리드)할 때 발생하는 이벤트(data)
            data.push(chunk)
            //배열에 청크(버퍼)를 담는다
            console.log(chunk, cunkh.length)
            //버퍼와 버퍼의 크기를 출력한다
        })

        readStream.on('end', () => {
          // 데이터를 다 읽으면 발생하는 이벤트(end)
          console.log('end', Buffer.concat(data).toString());
        })

        readStream.on('error', (err) => {
          // 데이터를 청크를 읽는 도중 혹은 무언가 에러가 발생하였을 경우 발생하는 이벤트
          console.log(err)
        })


        //파일 복사 
        //스트림을 연결해서 넣어준다.
        const fs = require(fs);

        const readStream  = fs.createReadStream('readme.txt');
        const writeStream = fs.createWriteStream('write.txt');
        readStream.pipe(writeStream);
        // 스트림을 이어준다.
        // stream은 연속적으로 파이핑을 해줄수 있다.
        // pipe.pipe식으로...

        //파일 복사2
        const readStream = fs.copyFile('./readme2.txt, './write2.txt', (err) => {
          console.log(err)
          //위와 동일한 방식이다.(스트림을 파이핑(이어주는)하는방식)
        });