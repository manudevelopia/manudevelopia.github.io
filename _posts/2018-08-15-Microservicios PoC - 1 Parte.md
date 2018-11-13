---
title: Microservicios PoC - 1 Parte
description: Microservicios PoC - 1 Parte
header: Microservicios PoC - 1 Parte
tags: arquitectura microservicios performance poc
comments: true
---

Para la PoC planteada he pensado en un servicio que devuelva las películas y series de un usuario. Este servicio no escoden grandes pretensiones, de este modo nos centraremos en la arquitectura, conexión y monitorización de los microservicios.

El servicio se compone de tres microservicios:

- Users: devuelve para un usuario las películas y series
- Movies: devuelve películas para un usuario
- TvShows: devuelve series para un usuario

Estos tres microservicios se implmentan de forma semejante, utilizando SpringBoot sobre Java con Gradle. 

Para las llamadas entre servicios se implementan utilizando [Feing](https://github.com/OpenFeign/feign) por su gran sencillez.

Para el tema test se utiliza JUnit, Mockito para los test unitarios y RestAssured para los funcionales. 

Hasta el momento se han empleado para la implementación:

- Java o Groovy
- Gradle
- [SpringBoot](https://spring.io/projects/spring-boot)
- [Feing](https://github.com/OpenFeign/feign)
- [Mockito](http://site.mockito.org)
- [RestAssured](http://rest-assured.io)

El código se ha versionado y descansa en Github.