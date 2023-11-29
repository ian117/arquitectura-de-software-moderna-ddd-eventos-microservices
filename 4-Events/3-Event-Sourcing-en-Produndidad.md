# Event Sourcing en Profundidad

+ Son **acciones** que han sucedido en el **pasado**

+ Los eventos deben ser **entidades inmutables**

+ Nunca deben ser eliminados o modificados, tan solo **insertados**

+ Para **desechar** una acción realizada por un evento, debemos de **lanzar** otro **evento** que **revierta** los cambios

+ Permiten conocer el estado del sistema en un punto en concreto del pasado
    + Ejecutar los eventos hasta el punto deseado



## Campos de un Evento

+ **ID** del evento para reconocer qué acción se está aplicando
+ **TimeStamp** para tener una referencia temporal de cuando se aplicaron
+  **Detalles** del evento que dependerá del evento lanzado y las necesidades

![](/images/4-Events/Captura%20de%20pantalla%202023-11-29%20135022.png)


## Evento de borrado

+ El **borrado** del evento el **lógico**, nunca físico

![](/images/4-Events/Captura%20de%20pantalla%202023-11-29%20135413.png)



### DDD Y Event Sourcing

+ Los eventos **no** se **limitan** a las operaciones de un **CRUD**

+ Si se usa DDD, los eventos son **expresiones** del **lenguaje ubicuo**

+ Eventos de un partido de tenis
    + Start
    + Finish
    + Point
    + Warn


### Proyección de Datos a partir de eventos

Si necesitamos mostrarle al usuario información basada en eventos se hace algo así

1. **Consulta** de eventos, filtrados por el ID de reserva y ordenados por timestamp

1. Creamos una nueva instancia de la entidad

1. Aplicamos los **eventos en orden**

1. Devolvemos la entidad que representa el estado actual


Un ejemplo es el de reservar habitaciones de un hotel, en el que se recopilan los eventos referentes a esta acción

Después se recorren hasta que la entidad tiene su último estado recopilado

![](/images/4-Events/Screenshot%20Capture%20-%202023-11-29%20-%2013-59-49.png)


### Problemas de Eficiencia

Un detalle al tener demasiados eventos es la eficiencia del sistema

Ya que recorrer eventos tiende a tomarlos y aplicarlos desde el primero (inicio de los tiempos) hasta el último (actualidad) tiende a ser deficiente

+ En entidades con muchos eventos, podría ser **lento ejecutarlos todos**
    + Ejemplo de un carrito de una web de compras
    + No tiene sentido aplicar todos los eventos desde el incio de los tiempos

+ Uso de **snapshots**
    + Representación del estado de la entidad en un momento concreto del pasado
    + Se recomienda para estos casos

+ Para obtener el estado actual ejecutamos los eventos a partir de la **última snapshot**
    + Ahorra tiempo de procesamiento

+ Gestionar **snapshots** implica **procesamiento** y **espacio**
    + Usar en situaciones dónde la ganancia sea sustancial
    + Más **Eficiencia** necesaria