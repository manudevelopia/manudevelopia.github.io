---
title: Microservicios PoC - 5 Parte
description: Microservicios PoC - 5 Parte
header: Microservicios PoC - 5 Parte
tags: arquitectura microservicios performance poc
comments: true
---

Recapitulando lo visto hasta ahora en la PoC de microservicios, en la primera parte se implmentaron 3 microservicios que se podrían llamar entre ellos. En la segunda parte se le incluyo un servicio para distribuir configuraciones desde un repositorio. En la tercera parte se añadió [Eureka](https://github.com/Netflix/eureka) como servicio para descubrir las instancias levantadas de los servicios. La cuarta parte ha provisto de un sistema de respuestas por defecto para para los casos de caída de servicios.

Es turno de ver como afrontar la posibilidad de que uno o varios de nuestos microservicios no está disponible y como ha de comportarse el sistema en ese momento. Para nuestro caso concreto, el servicio usuarios llama a los servicios de películas y series, y uno o ambos no están disponibles.

Para manejar esta situación utilizaremos [Hystrix](https://github.com/Netflix/Hystrix), que al igual que sucedía con [Eureka](https://github.com/Netflix/eureka) mediante una anotación en nuestra case principal, otra para el método de llamada a servicio que se quiera cubrir y la definición de un método para el caso de indisponibilidad (fallbackMethod) podremos disponer de una estrategia para el caso en el que el servicio no esté disponible.

Volviendo a nuestro caso particular, en caso que un servicio no esté disponible se devolverán datos por defecto, así devolvemos algunas películas de la filmografía de Quentin Tarantino, que serán devueltas en cada petición del servicio usuarios mientras alguno o ambos servicios no estén disponibles.

Hasta el momento se han empleado para la implementación:

- Java o Groovy
- [Gradle](https://gradle.org)
- [SpringBoot](https://spring.io/projects/spring-boot)
- [Feing](https://github.com/OpenFeign/feign)
- [Mockito](http://site.mockito.org)
- [RestAssured](http://rest-assured.io)
- [Spring Config](https://cloud.spring.io/spring-cloud-config/)
- [Eureka](https://github.com/Netflix/eureka)
- [Hystrix](https://github.com/Netflix/Hystrix)

El código puede encontrarse en [Github](https://github.com/manudevelopia/showltan) y la [configuración](https://github.com/manudevelopia/showltan-config)