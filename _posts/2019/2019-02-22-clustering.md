---
layout: post
title : clustering
categories: node
tags: [REST API]
comments : true
---

**클러스터링**

노드는 기본적으로 CPU의 코어수랑 상관없이 싱글스레드로 동작한다.   
즉 자원이 많아도 사용 불가능 하다.   
멀티스레딩 언어와는 다르게 태생(자바스크립트)부터 멀티스레드가 아닌 노드는 이부분을 멀티 프로세싱으로 극복한다.   


      const cluster = require('cluster');
      const os = require('os');
      const cpus = os.cpus().length;
      const http = require('http')

      if (cluster.isMatser) {
         for(let i = 0; i < cpus; i+=1) {
            cluster.fork(i)
            // 워커(프로세스)를 생성한다
         }
      } else {
         http.createServer((req, res) => {
            res.end('response');
         }).listen(8888);
      }

      
      const cluster = require('cluster');
      const os = require('os');
      const numCPUs = os.cpus().length;
      const http = require('http')

      if (cluster.isMatser) {
         console.log('마스터 프로세스 아이디', process.pid);
         for(let i = 0; i < numCpus; i+=1) {
            cluster.fork(i)
         }
         cluster.on('exit', (worker, code, signal) =>{
            // 워커가 종료하면 뭐가 종료했는지 보여준다
            console.log(worker.process.pid, '워커가 종료되었습니다.')
         });
      } else {
         http.createServer((req, res) => {
            res.end('response');
            setTimeout(() => {
               process.exit(1);
            }, 1000);
         }).listen(8888);
         console.log(process.pid, '워커 실행')
      }







