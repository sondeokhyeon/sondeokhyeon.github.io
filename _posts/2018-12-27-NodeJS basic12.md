---
layout: post
title : NodeJS 기초12
categories: NodeJS
tags: [NodeJs,JavaScript]
comments : true
---

**Node JS의 내장 모듈2**   

 - url(url 관련 모듈)   
       노드에서는 url을 두가지 형태로 파싱한다.   
       Node JS URL<a href="https://nodejs.org/api/url.html#url_url_strings_and_url_objects"> API </a>문서를 참고 하자.   
       한가지는 <a href="https://ko.wikipedia.org/wiki/WHATWG">WHATWG</a> (Web Hypertext Application Technology Working Group)에서 새롭게 정의한 API 형태 이고 하나는 Legacy API형태이다. 

        const url = require('url');
        const URL = url.URL;
        
        // WHATWG 형태 파싱
        const myBlogURL = new URL('http://sondeokhyeon.githubio/blog');
        console.log(myBlogURL)             // url 정보를 구조화 된 객체로 출력한다
        console.log(url.format(myBlogURL)) // url 정보를 출력한다 
       
        // Legacy 형태 파싱 
        const urlParsing = url.parse('http://sondeokhyeon.githubio/blog')
        console.log(urlParsing)

      - <a href="https://nodejs.org/api/url.html#url_the_whatwg_url_api">WHATWG 용 URL 관련 API 문서</a>   
      Constructor, hash, host, href, origin, port, searchParams, append, set 등 유용한 API가 문서에 있다.

      - <a href="https://nodejs.org/api/url.html#url_legacy_url_api">Legacy 용 URL 관련 API 문서</a>
      
      
