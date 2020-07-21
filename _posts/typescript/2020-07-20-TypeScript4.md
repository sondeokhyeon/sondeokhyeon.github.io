---
layout: post
title : TypeScript3
categories: TypeScript
tags: [TypeScript]
comments : true
---

**타입스크립트4**

타입스크립트의 타입4

    // any 타입 
    // any 타입은 모든 타입을 할당할 수 있는 타입이다. 
    // 일반적인 let과 동일하다고 보면된다. 
    let any1: any = 1;
    let any2: any = '2';
    let any3: any = true;
    let any4: any = undefined ;
    let any5: any = null;
    let any6: any = new Object();

    // unknown 타입 
    let unknown1: unknown = 1;
    let unknown2: unknown = "2";
    let unknown3: unknown = false;
    let unknown4: unknown = undefined;
    let unknown5: unknown = null;
    // unknown 타입은 Any타입과 마찬가지로 모든 타입을 할당할 수 있다 
    // 차이점은 오퍼레이션을 지원하지 않는다.
    // unknown1.tostring(); // 이러면 에러다 
    // parseInt(unknown2);  // 이것도 에러다

    // void 타입 
    function void1() : void {
        console.log('이것이 보이드다아아아')
    }
    // 변수에는 undefined와 null만 할당하고 리턴할 타입이 없다면 보이드로 타입지정이 가능하다

    // never 타입 
    // 함수의 끝에 절대 도달하지 않는다는 의미를 지닌 타입

    function neverEnd(): never {
        while (true) {
         ....   
        }
    }

--- 
