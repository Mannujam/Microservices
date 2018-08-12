# Microservices
Synechron Training

http://resources.way2learnonline.com/micro/

## Challenges
1) All local calls between APIs / services would become remote calls.
2) Loadbalancing → Issue → Network calls (hops)
3) Netflix → Ribbon API [Client side loadbalancer]
4) Netflix → Eureka [Discovery server(service)]
5) Netflix → hystrix [library] → Circuit breaker pattern. Every microserver should use this library for circuit breaker logic, incase to communicate other services.
6) Third party application talking to microservices, API gateway (proxy server)[ZUUL] should be the bridge between them.
7) Netflix → ZUUL itself will have its own LB.
8) Configuration server [Spring cloud configuration server]


Spring boot ZUUL [Netflix], Spring boot hystrix [Netflix], …


## XML injection Vs Java Injection
1) Type checking
2) Conditional injection

## Spring Boot
1) All beans related to jar are created.
2) Boot configures automatically.
3) Unnecessary jars should not be in classpath.
4) Comes in support of Mevan, Spring (pom.xml → boot specific code). Add all dependencies in pom.xml [spring-boot-starter-data-jpa]
5) Parent tag in pom.xml resolves version of the starter artifacts.


## Bean lifecycle
1) Bean constructor
2) Bean setter
3) Bean post processor

Activate profiles → java -D spring.profile.activate = dev

REST
Spring-MVC REST

## Eureka
Eureka --> REST API
Default port --> 8761
One Eureka per server

*** Note *** yml should be formatted with 2space indentation.

If only one eureka with different port then default, it will fetch the registry for default port. To stop that configure yml with eureka:
  client:
    fetch-registry = false 
    register-with-eureka = false
  instance:
    hostname: localhost
    
 Eureka will try to get the hostname --> oshostname

--> EnableEurekaClient - 

No Zone -->
eureka:
  client:
    service-url:
      defaultZone: http://localhost:5001

with Zones -->
eureka:
  client:
    service-url:
      z1: http://localhost:5001
      z2: http://localhost:5005


Self Preservation mode (server side) - When the heartbeat is not reached from microservices to Eureka, Eureka will go into self preservation mode.
By default SPM is 70% [not configurable]


