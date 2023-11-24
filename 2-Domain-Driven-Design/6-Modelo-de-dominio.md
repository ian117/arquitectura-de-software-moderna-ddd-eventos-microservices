# Modelo del Dominio

### Elementos del Modelo de Dominio

❇️ **Entidades**
+ Clases con datos y comportamiento


❇️ **Value Objects**
+ Clases con simplemente datos
+ Sirven para representar de manera más claa los atributos de las entidades
+ Deben de ser **inmutables**

❇️ **Aggregates**
+ Grupos de entidades y value objects
+ Separan conceptos diferentes de nuestro dominio
+ Tendrán **algo así** como una **API** (que es la raíz del aggregate) que es por donde pasarán las **interacciones** con **otros aggregates**


✅ Como regla general, la comunicación entre distintos aggregates se debe hacer a **traves de la raíz** de los mismos. Una raíz no puede acceder a otro elemento no raíz de un aggregate diferente.


### Ejemplo

Siempre que comenzamos a elaborar un dominio, es normal que empecemos a analizar primero las **entidades**

En este ejemplo, es una agencia de software pequeña que se divide en 3
+ Equipo
+ Proyecto
+ Miembro

![](/images/2-Domain-Driven-Design/Captura%20de%20pantalla%202023-11-22%20154830.png)


Además de que existen **attributos** que estas entidades poseen

![](/images/2-Domain-Driven-Design/Captura%20de%20pantalla%202023-11-22%20155109.png)

Estos son los **objetos de valor**, que serían los siguientes

+ Departamento (-> Equipo)
+ Estado (-> Proyecto)
+ Categoria (-> Proyecto)
+ Dirección (-> Miembro)
+ Rol (-> Miembro)

Sirven para representar de forma precisa atributos de nuestras entidades

_Solo son datos sin ninguna lógica implementada_


El siguiente paso es establecer las relaciones de nuestro modelo

![](/images/2-Domain-Driven-Design/Captura%20de%20pantalla%202023-11-22%20155548.png)

Cada objeto de valor con su entidad

Al final podemos apreciar los **conceptos** claramente **diferenciados**

![](/images/2-Domain-Driven-Design/Captura%20de%20pantalla%202023-11-22%20155630.png)


Cada uno de estos **conceptos** es conocido como **aggregate / agregado**


_Cada aggregate tendrá una **entidad raíz**_

Que en este caso son:
+ Equipo
+ Proyecto
+ Miembro

También pueden existir entidades secundarias en los aggregates

+ Estas entidades tendrán datos y lógica pero no serán la raíz del aggerate

#### Contexto Acotado

Si pondemos los **contextos acotados** en la mesa

_Cada **contexto acotado** tendrá **multiples aggregates**, y **dentro** de estos habrán **multiples entidades** y **objetos de valor**_