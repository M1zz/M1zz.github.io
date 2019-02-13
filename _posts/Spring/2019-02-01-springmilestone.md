---
title: "스프링을 시작하며"
categories:
  - Spring
tags:
  - springframework
  - springBoot
---

개발자로서의 커리어를 위해 기술스택을 쌓기위해 스프링을 공부하기로 시작했다. 이미 개발하고 있는 서비스가 스프링이기도 하고, 많은 서비스들이 스프링을 이용하여 제공되고 있다는 생각에 무작정 시작했다. 공부를 시작한지 2주 생각보다 헛돌며, 시간이 낭비된다는 생각이 강하게 들어 다시한번 목표를 상기하고 나아갈 방향을 다잡아야 할 시간. 이를 위해 글을 쓰며 생각을 정리한다.

1. 목표는 위대하게!  
제일 먼저 시작한 작업은 [깃헙 프로젝트](https://github.com/BroadleafCommerce/BroadleafCommerce)에 컨트리뷰션을 하는 것이었다. 하지만 생각보다 코드의 양이 방대하고 스프링을 아얘 모르기 때문에 스프링에 대해 공부하고 시작을 하자 마음먹었다. 그 다음 목표를 잡은게 내가 만드는 작은 쇼핑몰 이었다. 이를 위해서는 프로젝트를 구성하고 환경 설정을 해야하는데 이 조차 버거워 작은 게시판으로 목표를 변경했다. 하지만 이 또한 마찬가지의 문제. 결국 목표를 잡고 거꾸로 작은 것 부터 부러뜨리면서 가기로 정했다.

2. 시작인 반  
일단은 튜토리얼을 진행하고 기본 개념들과 용어들을 익숙하게 만들어야 했다.
스프링의 동작과정은 어떻게 되는지, 왜 스프링을 쓰는지, MVC 어떤 구조인 이해하고자 한다. m에서의 mysql과 jpa가 무엇인지 왜 쓰는지 공부하고, 기본 mvc모델을 이용해서 요청과 응답을 처리해보자.

3. spring을 공부하면서 어노테이션을 왜 쓰는지 어떻게 써야하는지 공부하자.

아래는 공부해야 할 스프링의 가이드를 나열한다.

[Building a RESTful Web Service](https://m1zz.github.io/spring/spring1/)  
~~Learn how to create a RESTful web service with Spring.~~

Scheduling Tasks  
Learn how to schedule tasks with Spring.

Consuming a RESTful Web Service  
Learn how to retrieve web page data with Spring's RestTemplate.

Building Java Projects with Gradle  
Learn how to build a Java project with Gradle.

Building Java Projects with Maven  
Learn how to build a Java project with Maven.

Accessing Relational Data using JDBC with Spring  
Learn how to access relational data with Spring.

Uploading Files  
Learn how to build a Spring application that accepts multi-part file uploads.

Authenticating a User with LDAP  
Learn how to secure an application with LDAP.

Messaging with Redis  
Learn how to use Redis as a message broker.

Messaging with RabbitMQ  
Learn how to create a simple publish-and-subscribe application with Spring and RabbitMQ.

Accessing Data with Neo4j  
Learn how to persist objects and relationships in Neo4j's NoSQL data store.

Validating Form Input  
Learn how to perform form validation with Spring.

Building a RESTful Web Service with Spring Boot Actuator  
Learn how to create a RESTful Web service with Spring Boot Actuator.

Messaging with JMS  
Learn how to publish and subscribe to messages using a JMS broker.

 Creating a Batch Service  
Learn how to create a basic batch-driven solution.

 Securing a Web Application  
Learn how to protect your web application with Spring Security.

 Building a Hypermedia-Driven RESTful Web Service  
Learn how to create a hypermedia-driven RESTful Web service with Spring.

 Accessing Data in Pivotal GemFire  
Learn how to build an application using Gemfire's data fabric.

 Integrating Data  
Learn how to build an application that uses Spring Integration to fetch data, process it, and write it to a file.

 Caching Data with Pivotal GemFire  
Learn how to cache data in GemFire.

 Managing Transactions  
Learn how to wrap key parts of code with transactions.

 Accessing Data with JPA  
Learn how to work with JPA data persistence using Spring Data JPA.

 Accessing Data with MongoDB  
Learn how to persist data in MongoDB.

 Serving Web Content with Spring MVC  
Learn how to create a web page with Spring MVC and Thymeleaf.

 Converting a Spring Boot JAR Application to a WAR  
Learn how to convert your Spring Boot JAR-based application to a WAR file.

 Creating Asynchronous Methods  
Learn how to create asynchronous service methods.

 Handling Form Submission  
Learn how to create and submit a web form with Spring.

 Building an Application with Spring Boot  
Learn how to build an application with minimal configuration.

 Using WebSocket to build an interactive web application  
Learn how to the send and receive messages between a browser and the server over a WebSocket

 Working a Getting Started guide with STS  
Learn how to import a Getting Started guide with Spring Tool Suite (STS).

 Consuming a RESTful Web Service with AngularJS  
Learn how to retrieve web page data with AngularJS.

 Consuming a RESTful Web Service with rest.js  
Learn how to retrieve web page data with rest.js.

 Consuming a RESTful Web Service with jQuery  
Learn how to retrieve web page data with jQuery.

 Enabling Cross Origin Requests for a RESTful Web Service  
Learn how to create a RESTful web service with Spring that support Cross-Origin Resource Sharing (CORS).

 Consuming a SOAP web service  
Learn how to create a client that consumes a WSDL-based service

 Accessing JPA Data with REST  
Learn how to work with RESTful, hypermedia-based data persistence using Spring Data REST.

 Accessing Neo4j Data with REST  
Learn how to work with RESTful, hypermedia-based data persistence using Spring Data REST.

 Accessing MongoDB Data with REST  
Learn how to work with RESTful, hypermedia-based data persistence using Spring Data REST.

 Accessing Data in Pivotal GemFire with REST  
Learn how to work with RESTful, hypermedia-based data persistence using Spring Data REST.

 Producing a SOAP web service  
Learn how to create a SOAP-based web service with Spring.

 Caching Data with Spring  
Learn how to cache data in memory with Spring

 Deploying to Cloud Foundry from STS  
Learn how to deploy a Spring application to Cloud Foundry from STS

 Spring Boot with Docker  
Learn how to create a Docker container from a Spring Boot application with Maven or Gradle

 Working a Getting Started guide with IntelliJ IDEA  
Learn how to work a Getting Started guide with IntelliJ IDEA.

 Creating CRUD UI with Vaadin  
Use Vaadin and Spring Data JPA to build a dynamic UI

 Service Registration and Discovery  
Learn how to register and find services with Eureka

 Centralized Configuration  
Learn how to manage application settings from an external, centralized source

 Routing and Filtering  
Learn how to route and filter requests to a microservice using Netflix Zuul

 Circuit Breaker  
Learn how to degrade gracefully services using Hystrix

 Client Side Load Balancing with Ribbon and Spring Cloud  
Dynamically support services coming up and going down without interrupting the client

 Testing the Web Layer  
Learn how to test Spring Boot applications and MVC controllers.

 Accessing data with MySQL  
Learn how to set up and manage user accounts on MySQL and how to configure Spring Boot to connect to it at runtime.

 Creating a Multi Module Project  
Learn how to build a library and package it for consumption in a Spring Boot application

 Creating API Documentation with Restdocs  
Learn how to generate documentation for HTTP endpoints using Spring Restdocs

 Messaging with Google Cloud Pub/Sub  
Learn how to exchange messages using Spring Integration channel adapters and Google Cloud Pub/Sub

 Building a Reactive RESTful Web Service  
Learn how to create a RESTful web service with Reactive Spring.

 Consumer Driven Contracts  
Learn how to with contract stubs and consuming that contract from another Spring application

 Accessing Vault  
Learn how to use Spring Vault to load secrets from HashiCorp Vault

 Vault Configuration  
Learn how to store and retrieve application configuration details in HashiCorp Vault

 Accessing Data Reactively with Redis  
Learn how to reactively interface with Redis and Spring Data

 Deploying a Spring Boot app to Azure  
Learn how to deploy a Spring Boot app to Azure.

 Building a Gateway  
Learn how to configure a gateway
