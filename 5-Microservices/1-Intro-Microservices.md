#  Microservicios

Proporciona una serie de prácticas, organización de trabajo y equipos para construir software complejo de forma más eficiente y a gran escala

+ Es agnóstico a las tecnologías

### Solución Monolítica

En un inicio se desarrollaban los proyectos con una solución monolítica

+ Un **único componente** para todo el **sistema**
    + Repositiorio de código único
    + BD única
    + Despliegue único de todo el sistema
    + La tecnología se mantiene desde el inicio al fin

+ Según va creciendo el sistema, aumentan los tiempos en mantenimiento
    + Más **complicado** integrar **nuevas funcionalidades** al código ya existente
    + Aparición de **más bugs**
    + Mantenimiento más **costoso** y **complicado** en general


### Microservicios

Para solucionar en parte estos problemas de la solución monolítica, se ideó separar en contextos cerrados el sistema para poder avanzar más rápido y eficientemente los proyectos


+ Dividimos el sistema en **contextos cerrados**
    + Creamos un **microservicio** para cada **contexto**

+ Micro en microservicios se refiere al alcance de las funcionalidades
    + No hay estándar para lo grandes que deben ser. **Deben hacer una cosa bien**

+ Cada microservicio vivirá de forma independiente a los demás
    + Equipo propio
    + Repositorio de código propio 
    + BD propia
    + Cada uno **elige** las **tecnologías** más apropiadas para su caso
    + Deben ser **desplegables** de forma **independiente**


##### Ejemplos

Cuando seguimos este tipo de arquitectura, dividiremos las funcionalidades importrantes (contextos cerrados) para que se le pueda asignar un equipo y avanzar de manera eficiente

![](/images/5-Microservices/Screenshot%20Capture%20-%202023-11-30%20-%2023-34-01.png)

![](/images/5-Microservices/Screenshot%20Capture%20-%202023-11-30%20-%2023-34-10.png)



### Comunicación Entre Microservicios

+ Importante la **buena comunicación** entre **equipos** dependientes
    + Dejar claras las necesidades de tu equipo
    + Poner sobre el papel las restricciones en caso de existir

+ **Métodos de comunicación**
    + API Rest
    + Sistema de mensakes. Event Driven Architecture