---
layout: post
title : MessageSource
categories: Spring
tags: [Spring]
comments : true
---

**MessageSource**   

스프링에서는 MessageSource 라는 기능을 통해서 다국어화 처리를 지원한다.   
(MessageSource는 applicationContext가 상속받았기 때문에 프로젝트 내부라면 어디든 사용 가능하다.)
MessageSource는 request의 Locale(country)에 따라서 각각 다르게 응답 할수 있다.   
물론 사용하기 위해선 빈 등록을 해주어야 한다.   
(스프링부트는 세팅이 되어 있어서 따로 빈 등록을 안해도 message.propertis를 다 읽기 때문에 바로 사용 할 수 있다.)   
프로젝트에 properties파일도 만들어주어야 하는데 아래에 같은 형식을 propertis을 만들어야 한다.

----
**propertis 파일 만들기**

default 예시
 - message.propertis

한국 예시   
- message_ko.propertis

영어 예시   
- message_en.propertis

---

**message.propertis 작성**

greeting = hello {0}

여기서 hello는 상수이며 숫자는 호출할때 주입한 아규먼트의 인덱스라고 보면된다. 

---

빈 등록 

    <bean id="messageSource" class="org.springframework.context.support.ResourceBundleMessageSource">
            <!-- Bean id랑 실제 클래스 경로(이름)	-->
    <property name="basenames">
			<value>'message.propertis path'</value>
            <!-- message.propertis의 경로를 지정한다 -->
	</property>
        <property name="defaultEncoding" value="utf-8"/>
        <!-- 한글깨짐 방지를 위해 utf-8을 기본으로 인코딩한다 -->
	</bean>

**스프링 부트는 위와같이 세팅 안해도 사용 가능하다**

---

메시지 사용

    @Component
    public class MessageTest() {
        
        @Autowired
        MessageSource messageSource;

        public String getGreting() {
            System.out.println(messageSource.getMessage('greeting', new String['Mr.Son'], {locale,KOREA}));
            // messageSource에 getMessage 메소드를 사용한다 
            // 가져올 메시지는 키값은 greeting이고
            // 넘기는 파라미터로는 Mr.Son이고 
            // locale은 KOREA이다 (message_ko.properties에서 greeting을 찾는다.)
        }

    }

결과 

    Hello Mr.Son


참고 블로그   
> <a href="http://javaslave.tistory.com/69">http://javaslave.tistory.com/69</a>   
> <a href="https://github.com/kenu/springstudy2013/blob/master/0325/1.SpringMessageSource.md">https://github.com/kenu/springstudy2013/blob/master/0325/1.SpringMessageSource.md</a>



