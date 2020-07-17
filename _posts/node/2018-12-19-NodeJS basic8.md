---
layout: post
title : NodeJS 기초8
categories: NodeJS
tags: [NodeJs,JavaScript]
---

**비 구조화 할당**

비 구조화 할당은 배열이나 객체의 속성을 각각 변수에 담는 형태의 새로운 표현식이다.

기존 배열이나 객체의 값을 꺼낼때는 아래와 같았다

    // array
    var array = [1,2,3,4,5]
    var a1 = array[0]
    var a2 = array[1]
    
    console.log(a1)
    console.log(a2)

    // object
    var jsObject = {
        j1 : 1,
        j2 : 2,
        j3 : function() {
           console.log(this.j2 += 1);
        },
    }

    console.log(jsObject.j1)
    console.log(jsObject.j2)   // 프로퍼티도 가능
    console.log(jsObject.j3()) // 함수도 가능

비 구조화 표현식을 사용하면 조금 더 간결하게 가능하다

    // array
    const [na1,na2,na3,na4,na5] = [1,2,3,4,5] // 알아서 key : value 식으로 매칭되는 형태
    console.log(na1)
    console.log(na2)
    
    // 아래와 같이도 사용이 가능하다
    const newArray = [1,2,3]
    const [na1, na2, na3] = newArray
    
    console.log(na1)
    console.log(na2)
    console.log(na3)

    // object
    const newJsObject = {
            no1 : 1,
            no2 : 2,    
            no3() {
                console.log(no2 + 1) 
                // console.log(this.no2 + 1)
                // 비 구조화 할당은 this를 할당 받지 못한다 
            }
    }

    const {no1,no2,no3} = newJsObject;

    console.log(no1)
    console.log(no2)   // 프로퍼티도 가능
    console.log(no3()) // 함수도 가능
    // this들어간 코드를 사용하려면 객체이름을 다 써주면 가능하다 
    // 예시 : console.log(newJsObject.no3()) 


라이브러리의 자원을 가져올 때 무척 유용할것이다.

[//]: <> (rest 문법도 있다. )
[//]: <> (es5 에서 arguments로  아규먼트값들을 배열로 변환해서 꺼낼수 있다. )
[//]: <> (es6는 rest라는 문법을 통해 가능하다)
[//]: <> (rest는 console.log<x, ...y>와 같은 문법으로 다 꺼낼수 있다. 기억하자..!)








