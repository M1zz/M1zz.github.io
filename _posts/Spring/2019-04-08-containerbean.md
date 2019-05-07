---
title: "스프링에서 컨테이너와 빈"
categories:
  - Spring
tags:
  - springframework
  - container
  - bean
---
# 컨테이너와 빈에관하여
스프링에서 계속 듣는 말이 바로 컨테이너와 빈이다.
빈과 컨테이너에 대한 개념이 없으니 설명을 이해할 수가 없었다. 용어의 의미와 개념을 알아보자.

먼저 스프링 프레임워크와 컨테이너, 빈의 구조도를 보자.
![spring_structure](/assets/img/spring/spring_structure.png)

그림에서 나타나듯이 사용자가 요청을 하면 그 요청은 먼저 서버에 도달한다. 서버에 들어온 요청은 서블렛 컨테이너에게 전달되고, 스프링 MVC에서 결국 DI컨테이너, 빈에 도달한다.


구조상으로 보았을 때 서블릿 컨테이너(Tomcat) > 스프링 컨테이너(Spring Container, IoC Container, DI Container) > 빈(Bean)이 존재한다.

서블릿 컨테이너는 서블릿 클래스들을 관리한다. 스프링MVC도 서블릿 클래스 중에 하나이다.
스프링MVC 내부에 DispatcherServlet이 있으며, Spring MVC로의 모든 요청과 응답은 DispatcherServlet이 관리하고 있다.
실제 내부적으로는 핸들러가 @RequestMapping 어노테이션을 기반으로 적절한 컨트롤러에게 던져준다.

## 서블릿 컨테이너
서블릿 컨테이너는 개발자가 웹서버와 통신하기 위하여 소켓을 생성하고, 특정 포트에 리스닝하고, 스트림을 생성하는 등의 복잡한 일들을 할 필요가 없게 해준다. 컨테이너는 servlet의 생성부터 소멸까지의 일련의 과정(Lifer Cycle)을 관리한다. 서블릿 컨테이너는 요청이 들어올 때마다 새로운 자바 스레드를 만든다. 우리가 알고 있는 대표적인 Servlet Container가 Tomcat 이다. 톰켓같은 was가 java파일을 컴파일해서 Class로 만들고 메모리에 올려 servlet객체를 만든다.

## 서블릿 생명주기
init() - 서버가 켜질때 한번만 실행
service - 모든 유저들의 요청을들을 받는다.
destroy() - 서버가 꺼질대 한번만실행

## IOC와 DI
IoC(Inversion of Control) : 개발자는 JAVA코딩시 New 연산자, 인터페이스 호출, 팩토리 호출방식으로 객체를 생성하고 소멸시킨다. IOC란 인스턴스의 생성부터 소멸까지의 객체 생명주기 관리를 개발자가하는 대신 스프링(컨테이너)가 관리한다.

DI(Dependency Injection) :	IoC를 실제로 구현하는 방법으로서 의존성있는 컴포넌트들 간의 관계를 개발자가 직접 코드로 명시하지 않고 컨테이너인 Spring이 런타임에 찾아서 연결해주게 하는 것이다.

Spring Container는 Bean들의 생명주기를 관리한다. Spring Container는 어플리케이션을 구성하는 Bean들을 관리하기위해 IOC를 사용한다. Spring 컨테이너 종류에는 BeanFactory와 이를 상속한 ApplicationContext가 존재한다. 이 두개의 컨테이너로 의존성 주입된 빈들을 제어하고 관리할 수 있다.

1. 사용자가 URL을 클릭하면 HTTP Request를 Servlet Container에 보낸다.
2. Servlet Container는 HttpServletRequest, HttpServletResponse 두 객체를 생성한다.
3. 사용자가 요청한 URL을 분석하여 어느 서블릿에 대한 요청인지 찾는다.
4. 컨테이너는 서블릿 service() 메소드를 호출하며, POST, GET여부에 따라 doGet() 또는 doPost()가 호출된다.
5. doGet() or doPost() 메소드는 동적인 페이지를 생성한 후 HttpServletResponse객체에 응답을 보낸다.
6. 응답이 완료되면 HttpServletRequest, HttpServletResponse 두 객체를 소멸시킨다.

## 스프링컨테이너

스프링은 객체를 관리하는 컨테이너를 제공한다. 스프링은 컨테이너에 객체를 담아, 필요할때 객체를 가져와 사용할 수 있도록 하며, 이러한 컨테이너 역할을 수행하는 인터페이스로 BeanFactory와 ApplicatuinContext가 존재한다. 컨테이너와 관련된 주요 인터페이스의 관계는 다음과 같다.

BeanFactory <- ApplicationContext <- WebApplicationContext 각각 화살표 방향으로 ApplicationContext은 BeanFactory 인터페이스를 구현하였고, WebApplicationContext  인터페이스는 ApplicationContext 를 구현 하였다.

## 빈(Bean)이란

Bean(빈)이란 스프링이 관리하는 인스턴스이다.
스프링에서는 개발자가 직접 인스턴스를 생성, 호출, 삭제하는 것이 아니다. 스프링이 제공하는 컨테이너를 통해서 관리되는 인스턴스를 우린 Bean(빈)이라 부른다.

즉 스프링 컨테이너에 의해 만들어 지고 관리 되는 자바 객체를 빈이라 부른다.

스프링 빈과 자바 일반 객체와의 차이점은 없다. 다만 스프링 컨테이너에서 만들어지는 객체를 스프링 빈이라고 부를 뿐이다.

이 둘의 차이 점 중 하나는 빈은 싱글톤의 디자인 패턴으로 구현되어있다. 싱글톤 디자인 패턴이란. 하나의 클래스가 하나의 인스턴스에 대해 최초 한번만 생성을 하고 다시 호출될 때 기존의 생성된 인스턴스를 사용한다.

## 싱글톤 패턴을 쓰는 이유

고정된 메모리 영역을 얻으면서 단 한번의 new로 인스턴스를 생성하고 한개의 인스턴스를 사용하기 때문에 많은 요청에도 메모리의 사용이 늘어나지 않는다.

싱글톤으로 만들어진 클래스의 인스턴스는 전역 인스턴스이다.
그러므로 다른 클래스의 인스턴스들이 데이터를 공유하기 쉽다.

DBCP(DataBase Connection Pool)처럼 공통된 객체를 여러개 생성해서 사용해야하는 상황에서 많이 사용된다. (쓰레드풀, 캐시, 대화상자, 사용자 설정, 레지스트리 설정, 로그 기록 객체등)

+ 인스턴스가 절대적으로 한개만 존재하는 것을 보증하고 싶을 경우 사용한다.
+ 두 번째 이용시부터는 객체 로딩 시간이 현저하게 줄어 성능이 좋아지는 장점이 있다.

## 싱글톤 패턴의 문제점

싱글톤 인스턴스가 너무 많은 일을 하거나 많은 데이터를 공유시킬 경우 다른 클래스의 인스턴스들 간에 결합도가 높아져 "개방-폐쇄 원칙" 을 위배하게 된다. (=객체 지향 설계 원칙에 어긋남) 따라서 수정이 어려워지고 테스트하기 어려워진다.

또한 멀티쓰레드환경에서 동기화처리를 안하면 인스턴스가 두개가 생성된다든지 하는 경우가 발생할 수 있다. 그러므로 꼭 필요한 경우아니면 지양해야한다.


참고 :  
[https://jojoldu.tistory.com/28](https://jojoldu.tistory.com/28)
[https://minwan1.github.io/2017/10/08/2017-10-08-Spring-Container,Servlet-Container/](https://minwan1.github.io/2017/10/08/2017-10-08-Spring-Container,Servlet-Container/)
[https://endorphin0710.tistory.com/93](https://endorphin0710.tistory.com/93)
[https://jeong-pro.tistory.com/86](https://jeong-pro.tistory.com/86) 멀티쓰레드 환경에서 안정하게 인스턴스 만드는 법을 위해 참고할만하다.
[https://deoki.tistory.com/17](https://deoki.tistory.com/17)
