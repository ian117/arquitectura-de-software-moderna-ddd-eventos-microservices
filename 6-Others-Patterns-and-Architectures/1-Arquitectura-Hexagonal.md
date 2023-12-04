# Arquitectura Hexagonal ~ Puertos y Adaptadores

También es conocido como _puertos y adaptadores_ ya que:
+ Utiliza esos dos componentes para conseguir una total **independencia** del **core** de nuestra aplicación con las **capas exteriores**

+ Bases en el diseño guiado por el dominio (**DDD**)
    + Arquitectura de **cuatro capas**

+ **Intenta aislar** aún más el **core** de nuestro sistema con el exterior



### Puertos

+ Partes del sistema por las que **fluye** la **información** a capas **inferiores**

+ **No** representan **puertos físicos** de comunicación

+ **Interfaces** Java


### Adaptadores

+ **Implementación** específica de un **puerto**
    + Adaptador Amazon SQS
    + Adaptador HTTP
    + Adaptador Redis

+ No debe existir comunicación entre adaptadores

+ En java son **clases** que implementan las **interfaces** que representan los **puertos**

+ Deben ser **totalmente remplazables**


### Servicios de Aplicación

+ **Capa** de **aplicación** en **DDD**

+ Servicios que implementan casos de uso e interactúan con las capas externas

+ **No** contienen **lógica** de **dominio**


### Dominio

+ **Capa** de **dominio** de nuestro **sistema**
    + Entidades
    + Value Objects
    + Aggregates
    + Servicios de Dominio



.

.

![](/images/6-Others-Patterns--and-Architectures/Screenshot%20Capture%20-%202023-12-03%20-%2017-38-54.png)

.

.
## Conclusión


Lo que consigue es algo que siempre se busca en ingeniería del software

+ Intentar **aislar** nuestra **lógica central** de las **implementaciones concretas** de las **capas exteriores**

Una ventaja de la arquitectura hexagonal es que **junta 2 conceptos** útiles que son el **DDD** y el **Principio de Inversión de la dependencia**

Todo esto para conseguir un **sistema** en donde se puedan **reemplazar** los detalles **exteriores** de forma **fácil**  al mismo tiempo de tener un **modelo guiado** por el **dominio**