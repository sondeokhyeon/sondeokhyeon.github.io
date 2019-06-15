---
layout: post
title : Environment
categories: Spring
tags: [Spring]
comments : true
---

**Environment**   

Environment는 실행 환경(Application) 이라고 보면 된다.    

실행 환경(로컬, 개발, 테스트, 스테이징, 알파, 베타, 운영 등등)에 따라 Application의 기능을 다르게 일부 다르게 사용이 필요(DB를 서버 환경에 따라 다르게 접속 한다던가, 일부 환경에서만 테스트 코드를 실행한다던가...)한 경우 해당 기능이 필요로 하기 때문에 스프링은 해당 기능을 지원 한다. 

쉽게 말해 실행 환경에 따라 고유의 값(환경 변수)을 세팅하고 그 변수의 값으로 분기처리 한다고 보면된다.   
환경 변수는 ApplicationContext 가지고 있는 기능 중 Environment를 가지고 있다.    
Environment 안에는 profile을 가지고 있다. 

세팅 방법 
profile 세팅은 아래와 같이 가능하다 

    options : -Dspring.profiles.active='환경변수'  

 
실제 IDE 내부에서 세팅은 아래의 글을 참조 하자    
<a href="https://www.lesstif.com/pages/viewpage.action?pageId=24445381">이클립스</a>   
<a href="https://stackoverflow.com/questions/50938383/how-to-set-jvm-arguments-in-intellij-idea">인텔리제이</a>

어노테이션으로 쉽게 profile 사용도 가능하며 

    @Configuration
    public class HelloServiceConfig {

        @Configuration
        @Profile("default")
        static class DefaultHelloConfig {
            @Bean
            HelloService helloService() {
            return new DefaultHelloService();
            }
        }

        @Configuration
        @Profile({"dev", "prod"})
        static class DevHelloConfig {
            @Bean
            HelloService helloService() {
            return new WorldHelloService();
            }
        }
    }

혹은 아래와 같이 사용 가능하다.

    @RunWith(SpringRunner.class)
    @SpringBootTest
    @ActiveProfiles("dev")
    public class SpringProfilesTests {

        @Autowired
        private HelloService helloService;

        @Test
        public void profilesTest() {
            assertThat(helloService.hello("wonwoo")).isEqualTo("hello world wonwoo!");
        }
    }

해당 소스는 <a href="http://wonwoo.ml/index.php/post/1933">머루의개발블로그</a>에서 샘플로 가져온 것 입니다.   
상세하게 내용도 잘 적어주셔서 관심이 있다면 꼭 들어가서 보시길..












