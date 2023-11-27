## Aspectos Positivos

+ **Tratamiento Independiente de las lecturas y las escrituras**
    + Posibilidad de tener 2 modelos distintos
    + Uso de bases de datos adecuadas para cada situación
        + Escalado independiente en función de las necesidades de lectura / escritura
        + Normalización y desnormalización independientes de las BBDD

+ **Posibilidad de tener 2 equipos independientes**
    + Un equipo para el stack de comandos
    + Un equipo para el stack de consultas


## Aspectos Negativos

+ **Gran Complejidad**
    + Mantenimiento de 2 stacks dinstintos para escritura y lectura
    + Mantenimiento de múltiples Bases de datos

+ **Sincronización**
    + Mantener la consistencia de los datos es un problema añadido

+ **Duplicidad / Redundancia de Código**


## Cuando Usar

+ Sistemas dónde la **escalabilidad es muy importante o crítica**

+ Volumen de datos y transacciones elevados

+ Proyectos con **problemas de rendimiento**

+ **No es necesaria una consistencia inmediata** de la información

+ Distinto tratamiento para las escrituras y lecturas

+ Equipos grandes