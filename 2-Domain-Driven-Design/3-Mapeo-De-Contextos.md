# Mapeo de Contextos

## Dependencias entre distintos contextos

A pesar de que es positivo separar nuestro modelo en contextos acotados, la lógica de un sistema complejo implica **interacción entre los distintos contextos**

+ Los contextos **no** son completamente **independientes**
+ Debemos tener clara la **interacción y dependencias** entre los mismos


Al final del día el el mapeo de contextos del Domain Driven Design es un diagrama en el que se dejan claro las relaciones y dependencias de nuestros contextos en el sistema

## Tipos de Relaciones

+ **Conformista (Conformist)**: No existe ninguna capacidad de negociación

+ **Cliente | Proveedor (Customer | Supplier)**: Dependencia con cierto grado de negociación. Necesidades en el cliente pueden implicar cambios en el proveedor

+ **Socio (Partership)**: Ambos contextos **colaboran** por una meta en común, por lo que ambos lados de la relación tienen poder para influenciar al otro.

+ **Núcleo compartido (Shared Kernel)**: Dos o más contextos **comparten un mismo modelo**. Todos necesitan estar de acuerdo para realizar cambios. Dificil de mantener.

+ **Capa anticorrupción (AntiCorruption Layer)**: **Interfaz** que utiliza Downstream para interactuar con Upstream, sin importar los cambios realizados en el ultimo

+ **Open Host Service | Published Languaje**: Relaciones de tipo **conformista** en las que se provee de documentación al Downstream context. Además se proporcionan **versiones** y compatibilidades entre ellas


### Ejemplo

Imaginemos que tenemos una tienda online con los siguientes contextos

Se pueden apreciar los contextos relacionados pero se necesita más información para tener una idea clara

![](/images/2-Domain-Driven-Design/Captura%20de%20pantalla%202023-11-21%20193155.png)


El contexto **Upstream (U)** _condiciona_ al **Downstream (D)**


![](/images/2-Domain-Driven-Design/Captura%20de%20pantalla%202023-11-21%20204147.png)

Por dar ejemplos

+ Core está condicionado por
    + Comparador de precios
    + Seguimiento de envíos

+ Core por su parte, condiciona a
    + Pagos y envíos
    + Listado y Carrito


+ La relación _Pagos y Envios_ con _Listado y Carrito_ es mutua y ninguno manda sobre el otro 