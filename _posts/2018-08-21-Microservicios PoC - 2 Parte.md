---
title: Microservicios PoC - 2 Parte
description: Microservicios PoC - 2 Parte
header: Microservicios PoC - 2 Parte
tags: arquitectura microservicios performance poc
comments: true
---

Continuamos con el tema de microservicios, en la primera parte se implmentaron 3 microservicios que se podrían llamar entre ellos. Así através del servicio de Users, se llamaba a Movies y TvShows devolviendo para un suario un a lista de películas y series para un usuario dado.

Estos servicios disponen de configuración propia que les permite ser levantados de forma independiente. En este sentido la gestión de la configuración está ligada al propio servicio. En un entorno cambiante no sea todo lo ágil que fuera deseable. 

En este sentido [Spring Config]() nos ofrece centralizar la configuración de nuestros microservicios y permitir su gestión como si de código se tratase desde un repositorio Git. Así cualquier cambio de confirguración estará inmediatamente disponible para las aplicaciones y en estás se podrán definir estrategias que actúen frente a estos cambios.

En esta segunda parte se implementará la gestión de la configuración de los microservicios mediante - [Spring Config]() y se versionará dicha configuración desde un repositorio git adicional al del propio proyecto. Si bien Spring Config permite que la configuración esté dentro del propio repositorio o desde una ubicación, me parece más interesante su gestión versionada separada.

Hasta el momento se han empleado para la implementación:

- Java o Groovy
- Gradle
- [SpringBoot](https://spring.io/projects/spring-boot)
- [Feing](https://github.com/OpenFeign/feign)
- [Mockito](http://site.mockito.org)
- [RestAssured](http://rest-assured.io)
- [Spring Config](https://cloud.spring.io/spring-cloud-config/)

El código se versionará y finalmente descansará en Github.