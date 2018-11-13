---
title: Microservicios PoC
description: Microservicios PoC
header: Microservicios PoC
tags: arquitectura microservicios performance poc
comments: true
---

Revisando el tema de microservicios plantedo en un [post anterior]() en el que se referenciaba el blog [En mi local funciona](http://enmilocalfunciona.io) me he propuesto realizar la imlpementación de una prueba de concepto tomando como base la serie que en el blog hay dedicada a [microservicios](http://enmilocalfunciona.io/tag/microservicios/) 

Para ello me propongo replicar parcialmente el concepto explicado en la serie 'Arquitectura de microservicios ' para montar un servicio sencillo que conste de varios microservicios que se consulten entre ellos.

Revisando el tema técnico, en la aproximación incial me gustaría utilzar los siguientes elementos:

- Java o Groovy
- [Gradle](https://gradle.org)
- [SpringBoot](https://spring.io/projects/spring-boot)
- [Eureka](https://github.com/Netflix/eureka)
- [Spring Config](https://cloud.spring.io/spring-cloud-config/)
- [Hystrix](https://github.com/Netflix/Hystrix)
- [Turbine](https://github.com/Netflix/Turbine)
- [Feing](https://github.com/OpenFeign/feign)
- [Mockito](http://site.mockito.org/)

El código se versionará y finalmente descansará en Github.