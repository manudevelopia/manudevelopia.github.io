---
title: Mapstruct y Page<ObjectDto>
description: Utilizando Mapstruct para generar una salida tipo Page<ObjectDto>  
header: Mapstruct y Page<ObjectDto>
tags: arquitectura mapstruct dto jpql
comments: true
---

Erase una vez una aplicación SpringBoot Groovy que tenía varias tablas, cada tabla tenía objetos, y los objetos eran Dto del modelo. 

La tabla de Clientes se llena de datos con la respuesta del servicio Rest de clientes. Este servicio se debe ser capaza de proveer los Dto de los Objetos soportando paginación y su gestión desde un navegador de páginas.

Para el mapeo de los datos a Dto se cuenta con mapstruct.

El objeto de vuelta de será tipo Page<ObjectDto>, con lo que previsiblemente será mapstruct quien se haga cargo de mapear la salida del servicio al Dto que se devuelva.

Nos proponemos hacer que Mapstruct se haga cargo del mapeo:

{% highlight java linenos %}
  @Mapper
  interface ObjectMapper {

      ClientMapper INSTANCE = Mappers.getMapper(ClientMapper.class)

      Page<ClientDto> clientsToPageClientDto()
      
  }
{% endhighlight %}

Pero al compilar comienzan los problemas

> error: No implementation type is registered for return type org.springframework.data.domain.Page\<com.example.dto.ClientDto\>.
> org.springframework.data.domain.Page<com.example.dto.ClientDto> clientsToClientsDto(org.springframework.data.domain.Page<com.example.model.Client> client);

Según parece hay añgunos problemas para gererar los Dto de esta manera [mapstruct/issues/607](https://github.com/mapstruct/mapstruct/issues/607) y no parece claro que sea factible la generación mediante este procedimiento, sin pasar por una interfaz funcional Java.

Revisando el problema en conjunto y tratando de buscar un a solución tengo claro que:

- Quiero usar el Page<ObjectDto> tal cual, sin wrappers.
- Quiero mantener la simplicidad, deshechando soluciones que solo aporten compleijdad

Teniendo en cuenta que si el servicio Rest sólo ha de devolver datos de la base de datos y no hay un procesamiento intermedio, salvo su mapeo a Dto, quizás pueda-deba traer este tipo de objeto de la base de datos directamente desde el repository.

La anotación @Query parerce una buena candidata para realizar esta acción

{% highlight java linenos %}
  @Repository
  interface ClientRepository extends JpaRepository<Client, Long> {

      @Query("""SELECT new com.example.dto.ClientDto(u.name, u.cif, u.addressLine1, u.addressLine2) 
                FROM Client AS u 
                ORDER BY u.name""")
      Page<ClientDto> findAllPagedAsDto(Pageable pageRequest)

  }
{% endhighlight %}

Bien parece que la cosa funciona, el @Service que consulta al @Repository recibe Page\<ClientDto\> y de ahí al @Controller, y finalmente se siver por el Rest directo a la tabla de Clientes tal y como era nuestro objetivo inicial.

Esta implementación nos permite mapear directamente desde la base de datos a un obtejo Dto, sin pasar por un mapeador, y con unos mínimos cambios centrados en nuestras necesidades. Adicionalmente servimos los datos ordenados por nombre tal y como sería deseable en una tabla de clientes.

Por contra perdemos cierto grado de automatización, ya que los cambios entre los objetos deben ser transladados manualmente a la query, la cual se ha optado por que utilize un constructor con todos los campos, para que así sea visible que campos lleva el Dto desde la query.