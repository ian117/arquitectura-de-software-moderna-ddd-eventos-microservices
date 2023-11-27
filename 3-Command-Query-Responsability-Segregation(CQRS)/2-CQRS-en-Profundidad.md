## Introducción a la Problemática

##### Neceistamos eficiencia en las lecturas pero no queremos sacrificar tiempo en las escrituras

![](/images/3-Command-Query-Responsability-Segregation/Screenshot%20Capture%20-%202023-11-27%20-%2009-56-10.png)

Necesitamos de tener en cuenta los requerimientos del negocio antes de aplicar CQRS


## Ejemplo Blog

Suponiendo que tenemos esta relación

![](/images/3-Command-Query-Responsability-Segregation/Screenshot%20Capture%20-%202023-11-27%20-%2009-58-08.png)

Podemos representarla de 2 maneras

#### Representación Relacional ~ Enfocada a Inserciones

![](/images/3-Command-Query-Responsability-Segregation/Screenshot%20Capture%20-%202023-11-27%20-%2009-59-25.png)

✅
+ **Rápido Insertando** nuevos comentarios

❌

+ **Lento leyendo** el número de comentarios de cada post
+ Lento leyendo el contenido de los comentarios de un post


#### Representación NOSQL ~ Enfocada a lecturas

![](/images/3-Command-Query-Responsability-Segregation/Captura%20de%20pantalla%202023-11-27%20101042.png)

✅
+ **Rápido leyendo** los post, el número de comentarios y su contenido. Información desnormalizada

❌
+ **Muy lento añadiendo comentarios** nuevos


### Problemática

## Métodos de Sincronización

![](/images/3-Command-Query-Responsability-Segregation/Screenshot%20Capture%20-%202023-11-27%20-%2009-56-10.png)


+ **Consistencia Inmediata** 
    + Método Síncrono
    <span style="color:red">+ _No recomendable_
    </span> **para _CQRS_**

+ **Consistencia Eventual**
    + Sincronización Asíncrona

+ **Consistencia Programada**
    + Sincronización a ciertas hotas del día

+ **Consistencia a baja demanda**
    + Se realiza la sincronización cuando se determine necesaria