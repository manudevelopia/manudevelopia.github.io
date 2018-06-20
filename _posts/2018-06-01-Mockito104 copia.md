---
title: Mockito 104
description: Mockito primeros pasos
header: Mockito 104
tags: testing mockito performance
---

Ahora tengo otro problema, uso Dozer y con @Mock sobre el maper el mapeo no es correcto, seguramente por que al tratarse de un mock no se tiene información sobre como realizar el mapeo, tal y como se describe en el xml de mapeos, con lo que el resultado del mapeo no es apto para continuar con el test.

{% highlight java linenos %}
    @Mock
    DozerBeanMapper mapper; ->
{% endhighlight %}

Utilizando @Spy e indicandole dónde encontrar el xml con la relación de mapeos lograremos que el mapper opere como se espera.

{% highlight java linenos %}
    @Spy
    DozerBeanMapper mapper;

    @Before
    public void setUp() {
        mapper.setMappingFiles(Arrays.asList("dozer-bean-mappings.xml"));
    }
{% endhighlight %}

En el enlace de 'Lecturas' se indican otras vías alternativas a @Spy, del cual también se indica 
que ha de usarse según que casos.

Lecturas
https://stackoverflow.com/a/49939545/3229871

