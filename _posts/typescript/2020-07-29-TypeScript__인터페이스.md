---
layout: post
title : TypeScript 인터페이스
categories: TypeScript
tags: [TypeScript]
comments : true
---

**타입스크립트 인터페이스**

##### 소개

기존 자바스크립트와는 다르게 타입스크립트는 인터페이스를 지원한다.  
타입스크립트의 인터페이스를 재활용을 하게 된다면 타입을 안전하게 사용할 수 있을뿐만이 아니라 
중복된 코드량도 줄여줄 수 있다. 

    function printLabel1(label: string ) :void {
        console.log(label);
    }

    printLabel2('hello interface');

    // 위의 코드를 인터페이스를 통해서 아래와 변경이 가능하다 
    
    interface LabeledValue {
        label: string;
    }

    // 파라미터 타입에 인터페이스 이름을 작성하는것으로 적용이 가능하다 
    // 파라미터가 1개이고 재사용을 안할꺼라면 쓰는게 더 번거로운데 1개 이상도 마찬가지로 적용이 되어
    // 여러줄을 인터페이스에 적으면 생략이 가능하다
      
    function printLabel2(labeledObj: LabeledValue):void {
        console.log(labeledObj.label);
    }

    printLabel2('hello interface');

##### Optinal Properties

위에 코드대로 작성할 경우 함수를 호출할 때 인터페이스에 적은 프로퍼티대로 아규먼트를 작성하지 않으면 에러가 발생하게 되는데 해당 에러를 방지하려면 옵셔날 옵션을 주면 방지할 수 있게 된다.  
(함수호출 시 넣는 아규먼트의 값이 있을수도 있고 없을수도 있다는 옵션이다)
옵션은 ? 인데 프로퍼티뒤에 ?를 넣으면 사용가능하다. 

    interface SquareConfig {
        color?: string;
        width?: number;
    }

    function createSquare(config: SquareConfig): { color: string; area: number } {
        let newSquare = { color: "white", area: 100 };
        if (config.clor) {
                // Property 'clor' does not exist on type 'SquareConfig'. Did you mean 'color'?
                // Error: Property 'clor' does not exist on type 'SquareConfig'
            newSquare.color = config.clor;
                // Property 'clor' does not exist on type 'SquareConfig'. Did you mean 'color'?
        }
        if (config.width) {
            newSquare.area = config.width * config.width;
        }
        return newSquare;
    }

    let mySquare = createSquare({ color: "black" });


##### ReadOnly Properties

한번만 값을 할당하고 싶다면 readOnly를 아래와 같이 사용하면 된다.

    interface Point {
        readonly x: number;
        readonly y: number;
    }

    let p1: Point = { x: 10, y: 20 };
    p1.x = 5; 
    // Cannot assign to 'x' because it is a read-only property.
    // 컴파일 에러 발생! 

##### Funciton Types

자바스크립트는 변수에 함수도 할당할 수 있다.  
그러니 당연하게도 타입스크립트도 가능한데 인터페이스에도 함수형 타입을 프로퍼티로서 가지는게 가능하다.

    interface SearchFunc {
        (source: string, subString: string): boolean;
    }

    let mySearch: SearchFunc;

    mySearch = function (source: string, subString: string) {
        let result = source.search(subString);
        return result > -1;
    };


##### Class Types

자바에서는 인터페이스를 쓰는 방식이 시그니처만 작성하고 실제 구현은 클래스가 구현하는 형태가 되는데 당연하게도 타입스크립트도 가능하다.  

    interface ClockInterface {
        currentTime: Date;
        setTime(d: Date): void;
    }

    class Clock implements ClockInterface {
        currentTime: Date = new Date();
        setTime(d: Date) {
            this.currentTime = d;
        }
        constructor(h: number, m: number) {}
    }


##### Extending Interfaces  

인터페이스가 인터페이스를 상속을 할땐 아래와 같이 extends 키워드를 통해 상속이 가능하다.

    interface Shape {
        color: string;
    }

    interface Square extends Shape {
        sideLength: number;
    }

    let square = {} as Square;
    square.color = "blue";
    square.sideLength = 10;


##### Hybrid Types

당연 ~~당연이라는 단어가 너무 많은거 같은데...~~ 하게도 함수역시 인터페이스를 통해서 클래스처럼 종합적으로 사용이 가능하다 

    interface Counter {
        (start: number): string;
        interval: number;
        reset(): void;
    }

    function getCounter(): Counter {
        let counter = function (start: number) {} as Counter;
        counter.interval = 123;
        counter.reset = function () {};
        return counter;
    }

    let c = getCounter();
    c(10);
    c.reset();
    c.interval = 5.0;