---
layout: post
title : Component Scan
categories: Spring
tags: [Spring]
comments : true
---

**Component Scan**   

Spring을 사용하는데 있어 중요한 개념은 DI와 IOC일것이다.   
DI와 IOC가 이뤄질려면 IOC컨테이너안에 자원(스프링 빈)들이 준비되어야 한다.

빈은 원래 XML에 각각 등록을 해줘야 하지만 패키지를 등록하면 컴포넌트 스캔을 통해 어노테이션을 등록하는것만으로 컨테이너에 등록된다.

컴포넌트 스캔이 되는 것은 @Component, @Controller, @Service, @Respository, @Configuration @Bean 등 어노테이션이다.   
기본적으로 컴포넌트 스캔은 BasePackage기반으로 이뤄진다.

Pacakge가 따로 있다면 스캔이 이뤄지지 않기에 따로 빈으로서 등록해줘야 한다.   
(IOC컨테이너에 적재되지 않아 DI가 이뤄지지 않는다(에러발생))   

<a href="https://dzone.com/articles/spring-spring-boot-and-component-scan">등록방법</a>   






