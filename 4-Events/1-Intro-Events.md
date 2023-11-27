# Events

Un evento es **algo que ha sucedido** en el **pasado**

Son **entidades inmutables**

+ Froma básica de **interacción en el mundo real**
    + **Menos usado** en el **software**, donde es más frecuente el estado

+ Es una forma de representar la **información a más bajo nivel**
    + Ofrecen más información que el simple estado final de una entidad

+ No nos perdemos nada de lo que sucede en nuestro sistema


### Representación Visual

Aquí vemos que en un sistema tradicional siempre veremos el estado **final / actual** de un **sistema**


En cambio en una **representación** con **eventos** vamos a ver el **paso a paso** que existió en las acciones. 

En este caso en la elección de un usuario para agregar items al carrito de compras


IMagen1
IMagen2



### Dónde Aplicar Eventos

+ **Event Sourcinig**
    + _Persistencia de eventos_, en lugar del estado actual
    + Se ejecutan los eventos para **obtener** el **estado** en **cierto momento**
    + Se puede combinar con CQRS

+ **Event Driven Programming**
    + Eventos de una Aplicación
    + Una entidad los produce y los lanza, otra los recibe y los procesa
    + Procesamiento **Asíncrono**


+ **Event Driven Architecture**
    + Se centra en la **comunicación** entre **distintos subsistemas**

    + Utilizar protocolos de **comunicación de mensajería** como **Kafka** en vez de los de comunicación directa como HTTP con llamadas hacia APIs