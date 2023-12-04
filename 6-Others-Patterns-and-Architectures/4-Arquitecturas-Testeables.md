# Arquitecturas Testeables

Arquitecturas que son fáciles de testear y como hacer esto correctamente

![](/images/6-Others-Patterns--and-Architectures/Screenshot%20Capture%20-%202023-12-03%20-%2023-01-30.png)

En estos tiempos se busca realizar proyectos con **despliegues** **rápidos**, **testeables** y **fiables**

+ Esto se logra haciendo **énfasis** en las **pruebas**


Estas arquitecturas hacen el **código** más **modular**, lo que resulta en un código más **fácil de probar**


### Pirámide de Pruebas

![](/images/6-Others-Patterns--and-Architectures/Screenshot%20Capture%20-%202023-12-03%20-%2023-04-04.png)


## Test Unitarios

**Objetivo** : Probar los métodos p´´ublicos de una clase de forma aislada

+ Mockear dependencias
+ Buscar una **cobertura alta** (> 90%)
+ Probar las distintas condiciones


## Test de Integración

**Objetivo** : Probar tu software con BBDD o librerias externas

+ **Desplegar Base de Datos real** para los test de integración
    + TestContainers, Docker

+ Probar el código que use librerías externas


## Test de Contrato

**Objetico**: Comprobar que las interfaces entre dos servicios se mantienen correctas

+ Muy común en **arquitecturas** de **microservicios**

+ Se prueban ambas partes de la comunicación
    + Productor
    + Consumidor


## Test de Interfaz Gráfica ~ Test de UI

**Objetivo**: Comprobar que la interfaz de usuario se mantiene como esperamos

+ **Distinto** de los **test** de **sistema** o **e2e** ~ EndToEnd

+ Se puede probar la interfaz mockeando el backend, por ejemplo:
    + Angular, react, vue
    + Jest, jasmine, mocha


    ## Test de Final a Final (E2E)

    **Objetivo**: Probar todo nuestro sistema

    + Pueden implicar **tests** de **UI**, pero no tienen por qué

    + Se **prueba** el **sistema** desde el **punto** de **entrada** al lugar donde se reflejen los **resultados**

    + Selenium, cypress


## Tests de Aceptación

**Objetivo**: Comprobar las funcionalidades de nuestra aplicación

+ Se centran en los **casos de uso** en **concreto**

+ Sintaxis **given-when-then**

+ Herramientas BDD como Cucumber


## Tests Exploratiorios

**Objetivos**: Probar **manualmente** nuestro sistema

+ Ni los mejores tests automáticos son perfectos
    + No podemos olvidar ciertos casos
    + Bugs en nuestros tests

+ Probar manualmente intentando romper la aplicación