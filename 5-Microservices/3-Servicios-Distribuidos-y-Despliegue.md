# Servicios Distribuidos % Despliegue

Unas de las principales beneficios a la hora de usar microservicios, es la posibilidad de:

+ Realizar despliegues optmizados
+ Escalados Independientes

Entonces, ala hora de construir estos, queremos que se cumplan 2 caracteristicas de estos

+ Escalabilidad
+ Disponibilidad

## Escalabilidad y Disponibilidad

+ **Escalando** nuestro sistema conseguimos **mayor disponibilidad**

+ **Escalabilidad Vertical**
    + Necesidad de mayor potencia en un nodo
    + Tareas pesadas, que necesitan mucha memoria, etc

+ **Escalabilidad Horizontal**
    + Mayor capacidad de **procesamiento paralelo**. Procesamos más peticiones en el mismo tiempo
    + **Eliminamos** puntos **únicos** de **fallo**

#### Puntos Únicos de Fallo

Son **piezas** si falla por cualquier motivo, el **sistema entero** deja de funcionar

+ Intentar que los puntos únicos de fallo, sean menores posibles

+ Los que existan, que sean muy **robustos**


## Servicios Distribuidos - Interacción HTTP

+ **Despliegue en múltiples maquinas**, las cuales, pueden ser dinámicas
    + ¿Dónde reside el servicio que quiero llamar?

+ **Múltiples instancias del mismo servicio**
    + ¿A cual de ellos realizo la petición?


### Multiples Máquinas - Interacción HTTP

Ejemplo de registro: **Eureka**

Esto es un ejemplo de solución al despliegue en multiples máquinas

Usando un registro, los microservicios le preguntan al registro la dirección y el puerto del servicio que quieren consultar

Esto es un **punto único de fallo**

![](/images/5-Microservices/Screenshot%20Capture%20-%202023-12-02%20-%2014-05-19.png)

##### Multiples Máquinas - Interacción HTTP - Load Balancer 

En los casos en los cuales se tengan **multiples instancias** de un **servicio**, se usa un **load balancer** para poder **gestionar** los **redireccionamientos**

![](/images/5-Microservices/Screenshot%20Capture%20-%202023-12-02%20-%2014-08-14.png)



### Multiples Máquinas - Interacción por Mensajes

+ **No existe** el **problema** anterior de **múltiples máquinas** (¿Donde reside el servicio a llamar?)

+ Los microservicios **no necesitan** saber nada de los demás
    + Se **subscriben** a  los eventos que les interesan
    + **Publican** los eventos necesarios

+ ⚠️ El **servicio de mensajes** también es un **punto único de fallo**

### Multiples Instancias - Interacción por Mensajes

+ Tampoco existe el problema dado de multiples instancias cuando se usa interacción por mensajes

+ El mensaje será procesado por la primera instancia del servicio que se encuentre libre
    + Si una instancia está sobrecargada, no va a consumir eventos