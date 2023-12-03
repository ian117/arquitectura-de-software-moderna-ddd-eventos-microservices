# Pros y Contras de los Microservicios

## PROS ✅

+ División del sistema en **subsistemas** más **manejables**
    + El código más fácil de mantener

+ **Independencia** real entre **equipos**. Cada uno es dueño de su microservicio

+ Posibilidad de realizar **escalado** y **optimización independiente**
    + Menos coste, empezamos con menos recursos y escalamos cuando sea necesario

+ **Despliegue independiente**. Si falla un microservicio, el resto podría seguir funcionando

+ Elección de la **tecnología apropiada** para cada **microservicio**

## CONTRAS ❌

+ **Cooperación entre distintos equipos** para los puntos en común para los microservicios

+ Más complejo en general que una solución monolítica
    + Necesidad de **identificar** correctamente **subdominios**
    + **Test** en las **fronteras** entre microservicios
    + **Despliegue** del sistema completo
    + **Seguridad**

+ **Interfaz de usuario**
    + Si es única, se puede volver un monolito dificil de manteenr y el equipo que la desarrolla puede ser el cuello de botella
    + Si son varias puede haber problemas en la integración en una única UI


## Cuando Usar ❇️🎲❇️


+ Sistemas grandes y complejos con **subdominios claramente identificables**

+ **Disponibilidad de perosnal** para asignar al equipo de cada microservicio

+ **Sistemas de alta disponibilidad** en los que necesitamos escalar fácilmente cada pieza

+ Ahorro de costes