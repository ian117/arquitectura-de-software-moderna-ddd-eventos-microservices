# Event Driven Programming

Paradigma de programación en el que el **flujo** del **programa** viene determinado por **eventos**

+ Una **entidad publica** un **evento**
+ Otra **entidad** lo **consume**


Permite **procesamiento asíncrono** pero también es posible hacerlo síncrono 


Casi todos los sistemas operativos, APIs donde el usuario interactua (winwdows, browsers), funcionan así:
+ Esperan un evento (acción) del usuario


## Eventos de Aplicación

Todo **evento lanzado** en el contexto de una **aplicación** por una **entidad** para ser **procesada** por otra u **otras**

+ Input del usuario
    + Clicks
    + Input del teclado

+ **Condición** que se da en el sistema en un **momento** en concreto
+ Evento lanzado con el **resultado** de un **procesamiento**
+ Cualquier otra interacción posible


## Ejemplo

![](/images/4-Events/Screenshot%20Capture%20-%202023-11-30%20-%2015-26-24.png)

En una aplicación en donde se retira dinero, cuando se hace la llamada al **AccountController**, se hace el acceso al **Event Publisher** y este se encarga de hacer las llamadas correspondientes a las Clases correspondientes para proceder con los eventos, **TransferService** y **AlertService**

1. **TransferService** y **AlertService** se configuran para escuchar el evento **TransferCreated**
1. **AccountController** publica el evento **TransferCreated** cuando le llega una transferencia
1. El **Event Publisher** busca las entidades suscritas a ese evento y se lo emite
1. **TransferService** realiza la transferencia
1. **AlertService** comprueba que el importe es alto y emite una alerta


## Event Publisher

En el ejemplo anterior se hizo un ejemplo de la importancia del event publisher

El **Event Pusblisher** permite el **desacople** de los que hacen el evento y de los que lo reciben. (SOLID, **inversión** de la **dependencia**)

+ El **mecanismo** de **eventos** de la aplicación necesita 2 partes
    + Un **registro** por **parte** de las **entidades interesadas** al **evento**
    + Un **mecanismo** de **publicación** de **eventos** a las **entidades interesadas**

+ Ejemplo: **Spring Events**
    + Permite eventos síncronos y asíncronos

+ Ejemplo: **.NET**