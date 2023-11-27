### Problematica

Usando **Syncronia** para hacer que los datos estén iguales en la base de datos, hay problemas al usar lo que vimos anteriormente

Hacer que la base de datos entera se actualice con los commands, a la larga es lento y se tiene que optimizar mucho

Existe 

+ **Dependencia directa** con el mecanismo de **sincronización**
+ Complejidad para insertar el modelo de escritura en la BBDD de lectura

Aquí entra el **event sourcing**

## Event Sourcing

Se define como -> Sistemas que **almacenan** el **estado** como una **secuencia de eventos**

![](/images/3-Command-Query-Responsability-Segregation/Screenshot%20Capture%20-%202023-11-27%20-%2014-36-17.png)

Usando el ejemplo anterior del sistema de Posts y Comentarios

Hacemos notar que

+ En el **modelo tradicional** solo existe un paso que es el de guardar el Post y que significa el **estado actual** del sistema

+ En el **Event Sourcing** existen **acciones reproducibles** para conseguir el **estado actual** del sistema


## Beneficios Event Sourcing  + CQRS

+ **Independencia del sistema de sincronización**
    + No es necesario realizar una llamada directa para activarlo
    + **Command Stack** genera **eventos** y el sistema de **sincronización** los **consume**

+ **Las traducciones de eventos son más sencillas**
    + Traducir una entidad completa es más complejo que traducir un evento.
    + Podemos elegir desde dónde sincronizar
    