---
layout: post
title : TypeScript3
categories: TypeScript
tags: [TypeScript]
comments : true
---

**타입스크립트3**

#### 클래스

##### readonly

    // 클래스의 속성에 readonly 키워드를 사용하면 아래와 같이 접근만 가능합니다.
    class Developer {
    readonly name: string;
        constructor(theName: string) {
            this.name = theName;
        }
    }
    let john = new Developer("John");
    john.name = "John"; 
    // error! name is readonly.



--- 
