# Event Driven Programming Pros y Contras

## Aspectos Positivos ✅

+ **Desacople** entre las **partes** **pulicadoras** y **consumidoras** del evento

+ **Flexibilidad**, es muy sencillo añadir o elminar consumidores sin modificar el productor

+ Proceso **asíncrono sencillo**, sin la necesidad de gestionar hilos

+ Al estar las **partes** más **desacopladas**, puede ser más **sencillo** de **testear**

## Aspectos Negativos ❌

+ Es más **complicado** de seguir el **flujo**

+ Tarea **debug** más **complicada**

+ Añade la **complejidad** del Event Publisher
    + Mitigado usando **frameworks** como **.NET** o **Spring**


## Cuando Usar  ❇️🎲❇️


+ Cuando en el futuro probablemente **necesitemos** más **entidades** que **procesen** el **mismo evento**

+ Necesidad de **operaciones asíncronas**

+ Cuando la parte **productora** _**no**_ necesite el **resultado** de la parte que **escucha** y **procesa** el **evento**