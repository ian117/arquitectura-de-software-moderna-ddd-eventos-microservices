# Event Driven Architecture

Patrón de arquitectura en el que el **flujo de información** entre los **distinos subsistemas** viene determinado por **eventos**

+ Componente o subsistea publica un evento

+ Otro lo consume


Es muy utilizado en **microservicios**


## Comunicación Directa

![](/images/4-Events/Screenshot%20Capture%20-%202023-11-30%20-%2016-31-12.png)

+ El servicio 1 **depende directamente** del servicio 2

+ Tiene que esperar por la respuesta de forma síncrona (o añadir lógica a mayores)

## Comunicación Indirecta


![](/images/4-Events/Screenshot%20Capture%20-%202023-11-30%20-%2016-31-22.png)

+ Un servicio se **subscribe** a los eventos que quiere escuchar

+ El otro servicio **publica** los eventos

+ El event manager redirige los eventos a los consumidores
    + **Desacople** total **entre** los dos **servicios**
    + Procesamiento **asíncrono**
