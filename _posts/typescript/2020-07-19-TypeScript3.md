---
layout: post
title : TypeScript3
categories: TypeScript
tags: [TypeScript]
comments : true
---

**타입스크립트3**

타입스크립트는 타입을 정적으로 고정하는 아래와 같이 선언하여 사용한다. 

    let isDone : boolean = false; 
    // 변수는 var 키워드가 이나라 es6의 let을으로 변수를 선언한다 
    // 이름은 isDone이고 타입은 boolean만 저장이 가능한데 할당한 값은 false이다. 
    // 즉 자바의 boolean isDone = false; 동일하다

타입스크립트의 타입1

    // Boolean
    let isDone : boolean = false; 

    // Number
    let decimal: number = 6;
    let hex: number = 0xf00d;
    let binary: number = 0b1010;
    let octal: number = 0o744;
    let big: bigint = 100n;

    // String 
    let color: string = "blue";
    color = "red";

    let fullName: string = `Bob Bobbington`;
    let sentence: string = `Hello, my name is ${fullName}.

타입스크립트 타입2  

    // Array
    let list: number[] = [1, 2, 3];
    let list: Array<number> = [1, 2, 3];

    // Tuple 
    let x: [string, number]; // 튜플은 배열 생성시 선언한 타입의 순서와 갯수가 맞아야 에러가 안난다.
    // x = [10, "hello"]; // 이렇게 할당하며 에러난다
    x = ["hello", 10]; // OK

    // Enum 
    enum Color {
        Red,
        Green,
        Blue,
    }

    let c: Color = Color.Green;
    // 상수 집합?같다. 
    // Enum은 위와같이 선언할 경우 내부에 Index가 생기는데 
    // 이 Index로 인해 Key : value 와 같은 구조가 된다.
    // key하고 Value를 동일하게 하려면 

    enum Color {
        Red: 'Red',
        Green: 'Green',
        Blue: 'Blue',
    }

    // 위와 같이 선언하면 된다. 

    // Null And Undefined
    let u: undefined = undefined;
    let n: null = null;






--- 
