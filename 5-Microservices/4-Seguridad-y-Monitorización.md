# Seguridad y Monitorización de Microservicios

Como en los microservicios existen muchos más puntos de entrada que puedan afectar nuestro sistema

Hay que asegurarlo

## Auntenticación

Una manera es que cada microservicio implemente **auntenticación** y estos se **autentiquen** cada vez que realicen una **interacción entre ellos**

Si cada equipo implementa su mecanismo de autencación:

+ Esto es ineficiente Per Se
+ Desperdiciamos **recursos** y aumentando las **posibilidades** de algún **Back** que ponga en **riesgo** nuestro sistema

![](/images/5-Microservices/Screenshot%20Capture%20-%202023-12-02%20-%2014-17-30.png)

.

Aunque claro **existen soluciones**

Una de ellos son **mecanismos** de **autenticación centralizada**

Ej: KeyCloak, Okta, Forgerock, etc

Con ellos la **autenticación** se hace en **1 único punto** (Como la gateway | API Layer)

+ Lo único que se comparte entre microservicios es el **token de autenticación** que tendrá que ser **verificado** en cada microservicio con la implementación del MAC

+ La autenticación ocurre en 1 único punto de forma sencilla y segura
+ Son implementaciones robustas que tienen equipos dedicados a mejorarlas

![](/images/5-Microservices/Screenshot%20Capture%20-%202023-12-02%20-%2014-17-48.png)


## Monitorización

+ **Logging**
    + Loggear de forma clara la información deseada
    + Distintos niveles (Debug, info, warn, error)


+ ⚠️ Problema de **Segregación** de la **información**

Al ser divididos en mútiples sistemas o ficheros se hace incomodos consultarlos

Existen herramientas para facilitar esto
+ Splunk por dar un ejemplo

.

.


+ Monitorización del **estado en tiempo real**
    + Spring Actuator

+ Plataformas de **monitorización centralizada**
    + New Relic
