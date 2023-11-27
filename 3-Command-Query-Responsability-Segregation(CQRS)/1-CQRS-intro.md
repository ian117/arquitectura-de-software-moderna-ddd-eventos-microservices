# Introducción a Command Query Responsability Segregation ~ CQRS

Se refiere a la acción de dividir la aplicación / código en base a Comandos y Consultas

+ **Comandos**
    + Acciones que **realizan una modificación en el estado del sistema** y que no devuelven información
    + Ejemplo: Iniciar un partido de tenis

+ **Consultas**
    + Acciones que **no alteran el estado del sistema**, tan solo devuelven datos
    + Ejemplo: Obtener los ultimos diez partidos de tenis



## El Problema

Haciendo un énfasis en lo que vimos de los modelos anteriores en el DDD, podemos notar lo siguiente

+ Utilizando el modelo **anémico**, nos damos cuenta que es perfecto para hacer **consultas**

    ![](/images/3-Command-Query-Responsability-Segregation/Screenshot%20Capture%20-%202023-11-26%20-%2017-56-19.png)

    + Representa fielmente nuestro modelo en DB
    + No tiene lógica
    + Riesgo de estados incongruentes (Se puede acceder en escenarios que no están completos)

+ Utilizando el modelo **DDD**, notamos que es eficiente para los **comandos**

    ![](/images/3-Command-Query-Responsability-Segregation/Screenshot%20Capture%20-%202023-11-26%20-%2017-56-30.png)

    + Representa fielmente neustro modelo de dominio
    + Necesita modificaciones para la persistencia
    + Exponemos lógica de negocio a capas superiores que no la necesitan



#### ¿Por qué no usar ambas soluciones?

_El CQRS se puede aplicar a cualquier caso en el que queramos tratar de forma distinta las consultas de los comandos_

![](/images/3-Command-Query-Responsability-Segregation/Screenshot%20Capture%20-%202023-11-26%20-%2018-10-16.png)

El **CQRS** va más allá de tan solo tener **2 representaciones diferentes** para consultas y comandos

Se divide el código/stack del sistema en dos stacks disntintos

**Dividimos** las **peticiones** en base a que si son **consultas** y **comandos**

Además de **optimizar** las consultas y comandos tiene otros beneficios