# Arquitectura Microkernel


**Kernel** significa núcleo y en el contexto de los sistemas operativos es el componente que tiene la funcionalidad básica para que las operaciones puedan procesarse

![](/images/6-Others-Patterns--and-Architectures/Screenshot%20Capture%20-%202023-12-03%20-%2022-41-01.png)


+ El **microkernel** que es el componente principal de **coordinar**

+ **Plug ins** que son los componentes que aportan funcionalidad y se registran en el microkernel

Por eso es conocida también como **arquitectura plug ins**


## Microkernel y Plug ins

Microkernel

+ Aporta la **funcionalidad mínima** para que el sistema se ejecute

+ Guarda un **registro de los plug ins** que están conectados al sistema

+ Canal de **comunicación** entre plug ins


Plug Ins

+ Aportan funcionalidad extra al sistema

+ No pueden vivir por sí mismos

![](/images/6-Others-Patterns--and-Architectures/Screenshot%20Capture%20-%202023-12-03%20-%2022-42-06.png)

## PROS ✅

+ **Fácil** de **testear**

+ **Fácil** de **mantener** a largo plazo que una arquitectura monolítica

+ **Flexibilidad** para añadir o eliminar plug ins, permitiendo así una **personalización** del sistema según las necesidades

## CONTRAS ❌

Necesita análisis previo

+ Qué **funcionalidades** introducimos al **microkernel**
+ Qué plugins tenemos? Cuán **grandes** deben ser los **plug ins**?
+ Existe la comunicación entre plug ins? **Mecanismo** de **comunicación**?

## Cuando Usar ❇️🎲❇️

+ Aplicaciones de escritorio que necesiten el concepto de plugins

+ Necesidad de un **sistema escalable**

+ Sistemas con un **tiempo** de **vida largo**