---
layout: post
title : NodeJS 기초7
categories: NodeJS
tags: [NodeJs,JavaScript]
---

**객체리터럴**

자바스크립트에서는 함수도 객체로서 활용 가능한데 이는 함수를 1급 객체로 취급하기 때문이다.  
그렇기에 객체 안에서도 프로퍼티 뿐만이 아니라 함수도 존재하는걸 볼수 있다.   
객체 리터럴(object literal)이라고 불리운다.

es5 객체 리터럴 

    var es5ValueCheck = function() {
            console.log(this.x + ' ' + this.y)
    }

    var draw = {
        x : 0,
        y : 0,
        init : function() {
            this.x = 10;
            this.y = 10;
        },
        es5ValueCheck : es5ValueCheck,
    };
    draw[z] = 0;


기존 es6에서는 아래와 같이 변했다   
(function이 생략 되었으며 또한 객체안에서 key와 Value가 같다면   
key만 적어도 value가 같이 생성이 되며 동적 생성 또한 가능하다)
    
    const es6ValueCheck = function() {
        console.log(`${this.x} ${this.y}`)
    }

    const newDraw = {
        x : 0,
        y : 0,
        init() {
            this.x = 10
            this.y = 10;
        },
        es6ValueCheck, 
        this[z] = 0;
    }


**Arrow function**

function 키워드로서 함수를 만들던 es5와는 다르게 es6은 화살표함수(Arrow function)이 추가 되었다.   
익숙치 않다면 익숙해질때까지 여러번 보는것이 좋을 것이다..!

    //es5 ver
    
    //함수 선언문
    funtion plus(a, b) {
        return a + b;
    }

    //함수 표현식
    var plus2 = function(a, b) {
        return x + y
    };

    //es6 ver
    //함수 표현식 
    const plus3 = (a, b) => {
        return x + y; //return 줄인다면 아래와 같은 형태가 된다.
    };

    const plus4 = (a, b) => a + b; // 또는 (a + b)로 가능하다 
    // 로직(처리)이 필요하면 중괄호 필요없으면 소괄호 혹은 괄호없이 적어도 리턴이 된다. 


화살표 함수 사용에 있어서 조심해야 하는 부분이 있는데 this를 사용할때는 조심해야 하는데 그 이유는 객체 안에서 함수를 사용할때 this가 액션에 바인드가 되는데 반해서 
화살표 함수는 그 객체 이름에 바인드가 된다.   
그래서 function 내부에서 this를 쓰도록 that = this 할당하는 것과 같은 일은 이제 화살표 함수를 쓰는것으로 대체 되었다.

쉽게말해 용도에 맞춰서 쓰자..! 
