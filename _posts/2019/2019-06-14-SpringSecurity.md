---
layout: post
title : security
categories: Spring, spring-security
tags: [Spring]
comments : true
---

**spring security1** 

스프링 시큐리트는 설정과 확장이 다양하기 때문에 학습하기 어렵지만 강력하고 유연한 보안 솔루션이기도 하다.  
기본적인 구조는 사용자의 인증(authentication)과 레벨에 권한(authoriztion)으로 이루어진다.  
URL에 요청에 따라 인증여부를 확인하고 로그인이 안되어있을 경우 로그인으로 이동한다.
인증을 실패하면 401(권한없음)에러가 발생하고 인증이 성공하면 권한을 확인하고 권한이 없으면 403(forbidden)코드가 부여되고 
권한까지 있는 경우 200 코드를 통해 정상적으로 응답할 것이다.

스프링 시큐리티는 authentication, Web URL의 authoriztion, Method 호출의 authoriztion 과 같이 채널 보안 등의 주요 기능을 제공한다.

Spring Security Dependency

artifactId : spring-security-core 
artifactId : spring-security-web
artifactId : spring-security-config
--- 위에 3가지는 필수 이며 태그 라이브러리가 사용이 필요하다면 아래의 것도 추가 해야 한다. ---
artifactId : spring-security-taglibs

Egov security Dependency
artifactId : egovframework.rte.fdl.security
--- egov의 경우 한가지만 위에것 하나만 추가해주어도 된다.  ---


security Filter 추가
filter는 Web.xml에 추가한다

    <!-- context.xml(spring 설정파일)을 스캔한다. -->
	<context-param>
		<param-name>contextConfigLocation</param-name>
		<param-value>classpath*:spring/context-*.xml</param-value>
	</context-param>
	
    <!-- Listener를 등록해준다. -->
	<listener>
		<listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
	</listener>

    <!-- springSecurity 필터를 생성한다. -->
    <!-- 모든 URL을 필터링 할수 있도록 URL패턴을 /*로 설정 -->
    <filter>
		<filter-name>springSecurityFilterChain</filter-name>
		<filter-class>org.springframework.web.filter.DelegatingFilterProxy</filter-class>
	</filter>
	<filter-mapping>
		<filter-name>springSecurityFilterChain</filter-name>
		<url-pattern>/*</url-pattern>
	</filter-mapping>


DelegatingFilterProxy의 역할

모든 request를 강제적으로 적용되도록 하는 servlet Filter이다. 
실제로 동작은 filter-name에 지정된 이름을 갖는 Spring Bean을 호출하는 역할을 한다. 
    
