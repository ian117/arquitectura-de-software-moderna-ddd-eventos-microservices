# Domain Driven Design ~ DDD

DDD se centra en la importancia de **entender** bien el **dominio** de nuestro problema para crear buen software

+ En contraste al enfoque **tradicional**, centrado en los **datos** que tratamos

.

En el proceso del DDD, para identificar el proceso del dominio se utilizan diversas estrategias:

+ Lenguaje Ubicuo, brainstorming
+ Identificación de los **contextos acotados**
+ **Mapeo de contextos**

.

➡️ Todo esto se hace con el fin de **separar** la **lógica** de **aplicación** (casos de uso) de la **lógica** de **dominio**

+ Los **casos de uso** varían mucho más frecuentemente

.

.

## Capas del DDD

![](/images/2-Domain-Driven-Design/Captura%20de%20pantalla%202023-11-23%20214732.png)

Se basa en la arquitectura tradicional, pero con la **lógica de negocio** dividida en **2**

+ En la capa de **aplicación** y **dominio**

.

#### Capas

+ **Presentación**: Capa que **recibe la petición** de la interfaz del usuario en un cliente.
Se **comunica** con la capa de **aplicación** para ejecutar un **caso de uso** en concreto
Es muy común que esta capa sean los **Controllers / Controladores**

.

+ **Aplicación**: Esta capa ejecuta el caso de uso haciendo **uso** de la **capa de dominio** para **ejecutar lógica** (que necesite) para ese caso de uso.
Esta capa interactua con la capa de infraestructura para temas como framework, login y acceso

.

+ **Dominio**: Contiene la **lógica inherente** al dominio **del problema**
Esta capa interactua con la de infraestructura, pero no para detalles específicos de implementación (acceso a datos, framework), si no para temas necesarios muy en concreto (login...)
Esta capa debe de interactuar lo más mínimo con esta capa y con cualquier otra.
El **dominio debe de estar lo más aislado posible**

.

### Modelar el Dominio

Para modelar el dominio de nuestra aplicación, para empezar, necesitamos establecer 4 cosas.

+ **Entidades**
    + Elementos del dominio con entidad propia
    + Comportamiento + datos

+ **Value Objects**
    + Elementos que almacenan solo datos
    + Creados para representar de forma más clara los atributos de las entidades

+ **Aggregates**
    + Conjunto de entidades y value objects con un sentido común

+ **Domain Services**
    + Elementos del dominio con lógica que no tiene cabida en ninguna de las entidades
    + Usualmente se usan para coordinar multiples aggregates, pero no solo son para eso