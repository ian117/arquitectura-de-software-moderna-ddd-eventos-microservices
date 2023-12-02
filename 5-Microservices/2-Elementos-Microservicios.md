# Elementos de los Microservicios


Veremos 3 puntos acerca de los microservcios

+ Almacenes de datos
+ Comunicación entre microservicios
+ Interfaz de usuario (API Layer)


## Almacenes de Datos

#### Nunca compartir la base de datos

En los microservicios, **compartir** la **base de datos** entre estos, es considerado un **antipatrón** y se debe de **evitar**

![](/Images/5-Microservices/Screenshot%20Capture%20-%202023-12-02%20-%2002-55-22.png)


+ Los microservicios dejan de ser **independientes**
    + No se pueden **desarrollar** de forma independiente
    + No se pueden **desplegar** de forma independiente
    + No se pueden **escalar** de forma independiente

+ **Encapsulación** de los **datos inexistente**
    + Un microservicio podría modificar información que no le corresponde

    + Con BBDD independientes forzamos a realizar la operación a través del microservicio dueño de esos datos


#### Sincronización de los Datos

A la hora de usar **múltiples BBDD**, esto conlleva también diferentes **problmáticas**


+ **Bajo demanda**
    + Un microservicio solicita a otro la información sobre sus entidades cuando le sea necesario. 
        + Ej: Pedido solicita la dirección al usuario al completar el pedido
    + De nuevo, se **pierde** la **independencia** entre los microservicios


+ Utilizando **sistemas** de **mensajes** (Eventos...)
    + Un microservicio publica un **evento** cuando sus datos  han sido modificados
    + El resto de microservicios a los que le interese el evento lo consume y actualiza la información
        + Ej: Usuario lanza un evento cuando la dirección se actualiza


## Comunicación Entre Microservicios

+ API REST
    + Simple, pero servicios acoplados
    + **Ambos** tienen que estar **disponibles** para que la comunicación funcione
    + Suele ser síncrono por defecto


+ Sistemas de Mensajes
    + Kafka, RabbitMQ, ActiveMQ etc
    + **Desacople** total entre los dos **servicios**
    + Procesamiento **asíncrono**
    + Si un sistema no está disponible, el mensaje permanecerá  en la cola hasta que vuelva a estar disponible, momento en el cual será consumido

![](/images/5-Microservices/Screenshot%20Capture%20-%202023-12-02%20-%2003-09-08.png)



## Interfaz de Usuario

La organización de la interfaz de usuario es un tema complejo con microservicios. 3 formas principales de hacerlo:

+ **Interfaz gráfica común**
    + Interactúa con una capa que integra todos los microservicios 
    + Como una API proxy

    ![](/images/5-Microservices/Screenshot%20Capture%20-%202023-12-02%20-%2003-12-53.png)


+ **Interfaz gráfica que enlaza a los micrositios**
    + Cada microservicio implementa su conjunto de páginas, en caso de tener
    
    ![](/images/5-Microservices/Screenshot%20Capture%20-%202023-12-02%20-%2003-13-46.png)


+ **Utilización de fragmentos incorporados en una interfaz general**
    + Fragmentos de múltiples microservicios pueden componer una única página
    
    ![](/images/5-Microservices/Screenshot%20Capture%20-%202023-12-02%20-%2003-14-23.png)
