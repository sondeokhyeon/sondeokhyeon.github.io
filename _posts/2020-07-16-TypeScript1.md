---
layout: post
title : TypeScript1
categories: TypeScript
tags: [TypeScript]
comments : true
---

**타입스크립트**

타입스크립트는 마이크로소프트사에서 개발한 자바스크립트 확장언어로서 타입스크립트로 개발하고 자바스크립트로 컴파일하여 실행되는 언어인데 살짝 맛(?)본 느낌상 타입스크립트는 정적으로 지정하는 언어라기 보다는 타입을 정의하고 지정하여 재사용성을 높이고 동적으로 바인딩 되어 맞지않는 타입으로 인해 발생할 오류를 미연에 방지하고 IDE의 어시스턴트를 활용하여 보다 생산성을 올려 개발하는 언어라고 볼 수 있겠다.  
(그래서 타입스크립트으로 개발할 시 VSCode나 WebStorm을 쓰는게 아니라면 생산성이 안 좋다고 하나보다)

### 설치방법

타입스크립트는 기본적으로 Node.js가 설치가 되어있어야 사용 할 수 있다.  
기본적으로 Node.js을 설치하면 자동으로 설치되는 npm 또는 yarn을 통해서 타입스크립트를 설치하는 것으로 사용 가능하다.  
설치는 아래의 명령어로 가능하다.

    npm install -g typescript
    // 또는 
    yarn add global typescript

### 사용법 
설치가 잘 되었다면 terminal에서 tsc를 쳐보자.  
그렇게 해서 아래와 같이 나온다면 사용할 준비는 끝이다.  
(버전이나 문구들이 다르게 나올 수 있을 것이다.)

    Version 3.6.3
    Syntax:   tsc [options] [file...]

    Examples: tsc hello.ts
            tsc --outFile file.js file.ts
            tsc @args.txt
            tsc --build tsconfig.json

    Options:
    -h, --help                                         Print this message.
    -w, --watch                                        Watch input files.
    --pretty                                           Stylize errors and messages using color and context (experimental).
    --all                                              Show all compiler options.
    -v, --version                                      Print the compiler's version.
    --init                                             Initializes a TypeScript project and creates a tsconfig.json file.
    ....


--- 
### 유용한 링크  
[공식홈페이지](https://www.typescriptlang.org/)  
[awesome-typescript-korean](https://github.com/typescript-kr/awesome-typescript-korean)