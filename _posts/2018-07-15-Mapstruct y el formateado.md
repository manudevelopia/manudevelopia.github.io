---
title: Mapstruct y el formateado
description: Utilizando Mapstruct para gestionar el formateo numérico
header: Mapstruct y el formateado
tags: arquitectura mapstruct formateo numérico
comments: true
---

La aplición SpringBoot Groovy que tenía varias tablas y cada tabla tenía objetos, sigue creciendo y conforme a ello se plantean nuevos retos.

Por exigencias del guión, un @Controller recibe los datos de un formulario que contiene como caracteres datos numéricos formateados utilizando ',' como separador decimal y '.' como separador de miles.

En un primer momento se podría pensar que que podemos usar el objeto del modelo que crea el formulario, ya que prácticamente todos los campos coinciden en número, pero los tipos numéricos y caracteres numericos formateados se van a encargar de quitarnos rápido este pensamiento. También cambría pensar que los números habrían de llegar al controller ya trasnformados, en formato numérico que al fin y al cabo es lo que son.

Si queremos atender al guión y que nuestro controller atienda peticiones con datos númericos formateados, nuestro controller debe ser capaz de tratar con ello.

Para ello el objeto que recibe los datos del formulario será exclusivo para este fin, utilizará String como tipo para recibir estos datos numéricos formateados, directamente del formulario, para luego transformarlo al tipo destino Double.

Para el mapeo de objetos se utiliza [Mapstruct](http://mapstruct.org) y vamos a utilizar [numberFormat](http://mapstruct.org/documentation/stable/reference/html/#implicit-type-conversions) para convertir el dato.

{% highlight java linenos %}
  @Mapper
  interface ObjetoMapper {

      ObjetoMapper INSTANCE = Mappers.getMapper(ObjetoMapper.class)

      @Mapping(source = "number" , target = "number", numberFormat = "###,###.##")
      Objeto objectoFormToObjeto(ObjetoForm objetoForm)
    
  }
{% endhighlight %}


Lecturas
https://docs.oracle.com/javase/tutorial/i18n/format/decimalFormat.html
http://mapstruct.org/documentation/stable/reference/html/#implicit-type-conversions)
