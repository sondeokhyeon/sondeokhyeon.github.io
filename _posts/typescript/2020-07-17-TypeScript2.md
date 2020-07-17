---
layout: post
title : TypeScript2
categories: TypeScript
tags: [TypeScript]
comments : true
---

**타입스크립트2**

타입스크립트는 컴파일을 실행환경이 인식을 가능하고(ts-node 같은거 말고...) 실행이 가능하다.  
이때 옵션을 다양하게 줄 수 있다.  

터미널에서 tsc --help 치면 다양한 옵션이 나온다 참고 하면 될 듯한데 몇가지만 적어보자~


##### 컴파일 옵션 

    --init    // tsconfig.json 만들어준다 옵션이 나열되어있으므로 주석을 풀면된다.          
    --target  // ECMAScript 버전을 지정 es6, es5, es2015, es2016...
    --lib     // 컴파일 시 참조할 라이브러리를 선택 es5, es6, dom...
    --module  // 컴파일 시 모듈 시스템 지정한다  common, amd, none ...
    --watch   // ts파일을 감시모드 저장하면 알아서  true/false
    --removeComments // 주석들은 제거하여 컴파일 해준다.  true/flase
    --sourceMap      // 소스맵을 만들어준다 true/false
    --outDir         // 컴파일 된 자바스크립트 저장할 경로  ./dist/
    // 등 다양한 옵션이 있다...

 
##### tsconfig.json

위에 명령어로 컴파일 을 할수도 있지만 tsconfig.json 있을경우 해당 파일에 있는 옵션대로 컴파일 해준다.  
위에와 마찬가지로 옵션을 줄 수 있는데 위의 옵션은 compilerOptions 안에 key-value형태로 작성하면 된다. 

    {
        "compilerOptions": {
            "watch" : true,
            "target" : "es6",
            ... 
        },
        "include": [
            "./src/**/*.ts" // src폴더안에 있는 모든 폴더에 모든 ts파일이 컴파일 대상이된다.
        ], 
        "exclude" : [
            "node_moduels" // 컴파일 제외 대상을 지정한다
        ]
    }
    
##### config 관련 유용한 링크
[공식문서](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)  
[번역문서](https://typescript-kr.github.io/pages/compiler-options.html)

--- 
