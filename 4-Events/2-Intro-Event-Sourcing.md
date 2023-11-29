# Intro Event Sourcing

Técnica que se baa en **almacenar** todos los **cambios** producidos en el sistema en un **almacén de datos**, el lugar el almacenar el estado actual


## Solución a: Constancia del Momento de una Acción

Problema común:
+ Login / Logout, Tiempo de sesión, acción específica realizada en el sistema, etc

Existen soluciones específicas:
+ Herramientas de logging
+ New Relic
+ Google Analytics

_(Según el autor del curso):_
_No es recomendable_. De esta forma aplicamos funcionalidad específica a mayores para mantener esa trazabilidad

Si tomamos el event sourcing como parte de la arquitectura de nuestra aplicación:
+ No tendriamos que depender de otras funcionalidades externas para eso

.

_(De mi propia exp, puede que esté_ mal):
Dejarle _**cierto trabajo**_ a herramientas especializadas puede ahorrar trabajo, tiempo, dinero y puede ser más eficiente al tener un sistema que permite flexibilidad y manejo de datos e integraciones está perfecto.

Incluir el event sourcing en la aplicación no está mal y es bueno para tener backup (y otras razones)

Pero no usar las herramientas creadas por otras compañias especializadas en ciertas problemáticas creo que sería poco prudente


## No es algo nuevo o innovador

Las bases de datos relacionales ya almacenan todas las acciones realizadas sobre cada entidad de la misma forma

A través de:

+ **Transacciones**