---
title: Microservicios PoC - 3 Parte
description: Microservicios PoC - 3 Parte
header: Microservicios PoC - 3 Parte
tags: arquitectura microservicios performance poc
comments: true
---

Seguimos con microservicios, en la primera parte se implmentaron 3 microservicios que se podrían llamar entre ellos. En la segunda parte se le incluyo un servicio para distribuir configuraciones desde un repositorio. En este momento nuestros servicios pueden obtener una configuración desde un repositorio, arrancar con dicha configuración, llamarse entre ellos y devolver un resultado.

Es momento de hacer que estos servicios puedan ser descubiertos, para ello utilizamos [Eureka](https://github.com/Netflix/eureka) que mediante una anotación en la clase pripincipal de nuestros servicios van a permitirles ser descubiertos. Todos ellos serán mostrados en el panel que provee el mismo [Eureka](https://github.com/Netflix/eureka) de modo que en todo momento podamos conocer los servicios que están levantados.

Hasta el momento se han empleado para la implementación:

- Java o Groovy
- [Gradle](https://gradle.org)
- [SpringBoot](https://spring.io/projects/spring-boot)
- [Feing](https://github.com/OpenFeign/feign)
- [Mockito](http://site.mockito.org)
- [RestAssured](http://rest-assured.io)
- [Spring Config](https://cloud.spring.io/spring-cloud-config/)
- [Eureka](https://github.com/Netflix/eureka)

El código puede encontrarse en [Github](https://github.com/manudevelopia/showltan) y la [configuración](https://github.com/manudevelopia/showltan-config) 