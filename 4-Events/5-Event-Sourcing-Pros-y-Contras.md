# Event Sourcing Pros y Contras

## Pros ✅

+ **Trazabilidad** del **estado del sistema** en el **tiempo**
    + Recuperación del estado en días pasados
    + Estadísticas y análisis

+ Nos proporciona un **log** de las **acciones** de los **usuarios**
    + No hay necesidad de usar librerías externas ni implementar logging propio


+ Es más **eficiente** **espacialmente** que guarfar un log con la entidad commpleta

+ Con **CQRS** podemos aprovechar los beneficios de ambos, **mitigando** los **puntos débiles**

+ Al no tener UPDATES ni DELETES físicos, es más **eficiente** en las **escrituras**


## Contras ❌

+ **Eficiencia** en las **consultas**
    + Se puede mitigar el problema con snapshots o eliminarlo usando CQRS

+ **Eficiencia espacial**
    + Necesita mucho más espacio que para representar simplemente el estado

+ **Dificultad para debuggear**
    + No hay forma sencilla de hacer consultas directas para conocer el estado actual

+ **Tecnica** mucho **menos usada**
    + Será menos intuitiva para los programadores
    + Necesita un tiempo de adaptación

+ **Tratamiento** de **dominios amplios**
    + Pocos eventos son fáciles de tratar, pero se puede complicar con dominios grandes


## Cuando Usar ❇️🎲❇️

+ Situaciones dónde consideremos usar **CQRS**

+ Cuando necesitemos conocer el **estado** del **sistema** en un **instante** del **pasado**

+  Necesidad de un **log** con todas las **acciones** realizadas por los **usuarios**

+ Cuando la **eficiencia** de las **consultas** no sea algo **crítico**