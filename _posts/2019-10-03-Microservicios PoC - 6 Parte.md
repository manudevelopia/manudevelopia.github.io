---
title: Microservicios PoC - 6 Parte
description: Microservicios PoC - 6 Parte
header: Microservicios PoC - 6 Parte
tags: arquitectura microservicios performance poc
comments: true
---

Recapitulando lo visto hasta ahora en la PoC de microservicios, en la primera parte se implmentaron 3 microservicios que se podrían llamar entre ellos. En la segunda parte se le incluyo un servicio para distribuir configuraciones desde un repositorio. En la tercera parte se añadió [Eureka](https://github.com/Netflix/eureka) como servicio para descubrir las instancias levantadas de los servicios. La cuarta parte ha provisto de un sistema de respuestas por defecto para para los casos de caída de servicios. En la quinta entrega se proporcióno al servicio de una respuesta definida en caso que un servicio no estuviese disponible.

Nustro servicio es capaz de dar un respuesta definida cuando alguno de los servicios a los que consulta no está dispoble, pero no tenemos una idea gráfica de lo que está pasando en ese servicio. Para ello en esta parte vamos a añadir [Hystrix Dashboard](https://github.com/Netflix-Skunkworks/hystrix-dashboard) que nos va a permitir monitorizar en vivo el estado del servicio permitiéndonos ver el número de llamadas, estado del circuito, y otras métricas relevantes.

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
- [Hystrix Dashboard](https://github.com/Netflix-Skunkworks/hystrix-dashboard)

El código puede encontrarse en [Github](https://github.com/manudevelopia/showltan) y la [configuración](https://github.com/manudevelopia/showltan-config)