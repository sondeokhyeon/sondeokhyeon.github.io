---
layout: post
title : TypeScript 클래스
categories: TypeScript
tags: [TypeScript]
comments : true
---

**타입스크립트 클래스**

이전의 자바스크립트는 Prototype을 기반으로하여 상속 이뤄졌었다
하지만 ECMAScript6 부터는 class 문법을 지원하게 되어 class기반으로 개발을 할수 있게 되었는데 타입스크립트는 자체 기능을 통해서 class의 기능이 향상 되었다.

##### 기본 구조

    class Greeter {
        greeting: string;
        constructor(message: string) {
            this.greeting = message;
        }
        greet() {
            return "Hello, " + this.greeting;
        }
    }

    let greeter = new Greeter("world");

##### 상속 

extends 키워드를 통해서 상속이 가능하다!

    class Animal {
        move(distanceInMeters: number = 0) {
            console.log(`Animal moved ${distanceInMeters}m.`);
        }
    }

    class Dog extends Animal {
        bark() {
            console.log('Woof! Woof!');
        }
    }

    const dog = new Dog();
    dog.bark();
    dog.move(10);
    dog.bark();


다형성을 지원함으로 아래와 같이도 코드 구성이 가능하다.  
하지만 코드를 보면 알 수 있지만 Animal을 상속받은 클래스들은 super를 통해서 바인딩하는것을 볼 수 있다. 

    class Animal {
        protected name: string;
        constructor(theName: string) { this.name = theName; }
        move(distanceInMeters: number = 0) {
            console.log(`${this.name} moved ${distanceInMeters}m.`);
        }
    }

    class Snake extends Animal {
        constructor(name: string) { super(name); }
        move(distanceInMeters = 5) {
            console.log("Slithering...");
            super.move(distanceInMeters);
        }
    }

    class Horse extends Animal {
        constructor(name: string) { super(name); }
        move(distanceInMeters = 45) {
            console.log("Galloping...");
            super.move(distanceInMeters);
        }
    }

    let sam = new Snake("Sammy the Python");
    let tom: Animal = new Horse("Tommy the Palomino");

    sam.move();
    tom.move(34);

접근제한자가 있어 모든 접근을 허용할건지 하위 클래스에서 접근을 허용할것인지 내부 클래스에서만 접근일 허용을 할 것인지 설정할 수 있다.

외부에서 모든 접근을 허용한다면 public  
외부에서 모든 접근을 거부한다면 private (파생 클래스조차 불가능)  
하위 클래스(파생된)접근 허용한다면 protected

라는 키워드를 통해서 허용/제한 할 수 있다. 


