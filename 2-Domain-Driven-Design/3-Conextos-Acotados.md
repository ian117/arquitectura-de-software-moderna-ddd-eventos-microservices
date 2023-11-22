# Contextos Acotados

Forma de organizar el modelo y la lógica de negocio **guiado por el dominio**

+ Un contexto acotado es aquel que tiene un sentido especial en el dominio
+ Cada uno tiene su **lenguaje ubicuo propio**
+ Las entidades fuera del contexto pueden tener características ligeramente diferentes

✅ Tener definida la misma entidad en diferentes contextos **no implica una duplicidad de código, si no una aclaración del mismo**

❌ Compartiendo modelo entre contextos, se tiende a acumular detalles e información de todos ellos, **poniendo en riesgo la integridad del modelo**


## Ejemplo

Imaginemos que tenemos un gimnasio que puede hacer 3 cosas

![](/images/2-Domain-Driven-Design/Captura%20de%20pantalla%202023-11-21%20182940.png)

+ Manejar pagos del usuario
+ Hacer Reservas
+ Gestionar la información del mismo como la dirección, la sucursal, los mismo usuarios y las clases.

Si esto sigue creciendo, tenemos que dividir la carga de trabajo en módulos para seguir desarrollando

Además, tenemos que **dividir** las **responsabilidades** en **grupos de funcionalidades**

![](/images/2-Domain-Driven-Design/Captura%20de%20pantalla%202023-11-21%20182702.png)


Así que creamos 3 contextos (equipos):

+ Información
+ Pagos
+ Reservas


Así ya estos equipos pueden desarrollar o trabajar en su propio contexto

+ Se logró dividir las funcionalidades

+ ❌ Sin embargo, al tener las clases compartidas, se pone en riesgo la integridad del modelo ya que **hacer un cambio** en un **modelo compartido** puede afectar a otro **contexto**


![](/images/2-Domain-Driven-Design/Captura%20de%20pantalla%202023-11-21%20183501.png)

Una mejor forma de ordenar las clases y contextos es así

Cada **contexto** tiene sus **propias entidades**

Estos conextos **no** son del todo **independientes**

Se sigue necesitando que los 3 contextos **cooperen entre sí** para una funcionalidad completa, pero eso se ve en el _**Mapeo de Contextos**_

Todo esto es para **evitar** que un **cambio** sobre una **entidad compartida**, dentro de un contexto, afecte a otro contexto