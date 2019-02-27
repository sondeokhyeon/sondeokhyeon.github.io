---
layout: post
title: Bean Scoped
categories: Spring
tags: [Spring]
comments: true
---

**Bean Scoped**

Component Scan에 의해 IOC 컨테이너에 적재된 Spring Bean은 기본적으로 Singleton으로 컨테이너에 적재된다.  
대부분의 경우에는 Singleton으로 등록 후 사용해도 문제 없을거고 대부분 다 Singleton으로 개발 하고 있을것 보인다.  
하지만 호출할때마다 빈이 새롭게 등록되어야 한다면 @Scope를 지정해준다면 Singleton이 아닌 Prototype으로
IOC 컨테이너에 등록이 가능하다.

    @Component
    @Scope("prototype")
    public class Proto {

    }

Singleton은 Thread safe하지 않기 때문에 해당사항을 고려해서 개발이 이루어져야 한다.  
(전역 변수는 자제하자...)
