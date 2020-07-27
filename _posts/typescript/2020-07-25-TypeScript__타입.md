---
layout: post
title : TypeScript Basic Types
categories: TypeScript
tags: [TypeScript]
comments : true
---

**타입스크립트 타입**

타입스크립트는 타입을 정적으로 고정하는 아래와 같이 선언하여 사용한다. 

    let isDone : boolean = false; 
    // 변수는 var 키워드가 이나라 es6의 let을으로 변수를 선언한다 
    // 이름은 isDone이고 타입은 boolean만 저장이 가능한데 할당한 값은 false이다. 
    // 즉 자바의 boolean isDone = false; 동일하다

타입스크립트의 Boolean, Number, String

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

타입스크립트 Array, Enum, 

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


타입스크립트 Any, Unknown, void 

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
