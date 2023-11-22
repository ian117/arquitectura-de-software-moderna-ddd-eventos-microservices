# Arquitectura de Capas ~ Capas del DDD

En las partes anteriores, se apreció como desenglosar el Dominio usando lenguaje Ubicuo, dividir las funcionalidades en contextos y cómo relacionarlos utilizando el mapeo de contextos.

Aquí se verá la arquitectura por capas en el DDD.


#### Arquitectura de 3 Capas

Al principio se vió un paso adelante cuando se separó el código spaghetti que era la presentación + la lógica de negocio 

Y se formaron las 3 con las que hoy en día empezamos a desarrollar cuando empezamos en la industria. Es mejor, es un código lasagna, más ordenado pero tiende a tener capas de spaghetti.

![](/images/2-Domain-Driven-Design/Captura%20de%20pantalla%202023-11-21%20205643.png)


#### Arquitectura de Capas DDD

Esta arquitectura es una evolución de la estructura de 3 capas normal

![](/images/2-Domain-Driven-Design/Captura%20de%20pantalla%202023-11-21%20205702.png)

Aquí, se **divide** la capa de **lógica de negocio** en **2**

En las capas de aplicación y presentación:

+ Aplicación: Donde residen nuestros de **casos de uso**. Independientes de la capa de dominio

+ Dominio: Toda la **lógica** del **dominio del problema**

.

También tenemos la capa de presentación que se mantiene igual

Además de la capa de infraestructura, que trata con todo lo relacionado a la **infraestructura de nuestro sistema**
+ Como datos, framework, login, etc.



## Capa de Presentación

❌ Esta capa NO es la Interfaz de Usuario

![](/images/2-Domain-Driven-Design/Captura%20de%20pantalla%202023-11-21%20210804.png)

Esta capa _**puede**_ tener detalles de la interfaz de usuario, pero _**no tiene porqué**_

+ En el pasado se construia la vista desde el servidor, por eso **se consideraba parte de la presentación**
+ Ahora es común tener la vista en otro proyecto (Frontend frameworks...)


✅ La **capa de presentación** sería nuestra _**API**_ que da la entrada a nuestro sistema que da soporte a la **interfaz de usuario**.

+ Es la fachada e interactúa con los servicios de la aplicacion para iniciar con los casos de uso

+ Serían los Controladores en la mayoría de los frameworks (Spring, Express, NestJs, etc)



## Capa de Aplicación

+ Encargada de **orquestar** todos los casos de uso necesarios para el funcionamiento de nuestro sistema

+ **Interactua con el dominio** para ejecutar su lógica específica

+ **Interactua con la infraestructura** para la persistencia, framework, logging etc.

+ **Responde a la presentacuón** con los datos formateados correctamente (Se devuelve el resultado)

+ De una manera general, son los **Services** en frameworks como Spring, NestJs, Express, etc.


## Capa de Dominio

+ **Datos y lógica central de nuestro sistema** diseñada bajo los principios de DDD

+ Debe de estar **lo más aislado posible del exterior** Se comunica con infraestructura si necesita algún aspecto como logging

+ Se compone de entidades de dominio y servicios de dominio

+ No se debe de ver afectada por cambios en el framework, base de datos o cualquier **implementación**


Serían las

+ **Entidades de dominio**
    + Datos
    + Lógica
    + No son entidades de persistencia (**@Entity** en Spring por ejemplo). Son clases o módulos planos.

+ **Servicios de dominio**
    + Lógica de dominio que no se pueda asignar a una entidad de dominio específica
    + Siguen los principios del DDD
    + **@Service** en Spring


## Capa de Infraestructura

+ **Persistencia**
    + Objetos de ORM(**@Entity** etc)
    + Repositorios[^1]

+ **Detalles del Framework**
    + Clases de Configuración
    + Arranque de la aplicación

+ **Oros Aspectos de la Infraestructura**
    + Logging


### Dependencias

➡️ Las flechas indican el **flujo de información**, no la dependencia

➡️ Es importante conseguir la **IoC**[^2] usando técnias como la **la inyección de dependencias**

![](/images/2-Domain-Driven-Design/Captura%20de%20pantalla%202023-11-22%20125711.png)



✅ Importante que el **dominio sea lo más estable** de nuestro sistema

+ ✅ Nunca debemos modificar nuestro dominio para adaptarlo al exterior, como por ejempolo BBDD

    + ✅ En ese caso, lo apropiado es adaptar la capa de infraestructura



[^1]: **Repositorio**: Un repositorio es una abstracción que facilita el acceso y la manipulación de datos, proporcionando una capa de separación entre la lógica de negocio y el almacenamiento de datos

[^2]: **IoC (Inversión de Control)**: **transferencia del control** del flujo de ejecución de un programa a un contenedor o framework