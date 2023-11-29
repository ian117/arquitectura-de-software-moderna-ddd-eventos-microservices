# Event Sourcing & CQRS

Al combinar ambos sistemas se crean grandes ventajas

En la combincación de estas técnicas, el **Command Stack** es el que se encarga de usar **Event Sourcing**

Al usar un **comando**, se **almacena** un **evento** en la BBDD de escritura

Entonces el sistema de **Sincronización** podrá de forma totalmente **independiente** al de escritura:
+ **Leer** los **eventos** que se van almacenando y **aplicarlos** a la BD del **Query Stack**

![](/images/4-Events/Screenshot%20Capture%20-%202023-11-29%20-%2014-32-27.png)


## Event Sourcing & CQRS (Pros y Contras)

### CQRS

✅ **Independencia** de las **lecturas** y las **escrituras**, pudiendo **optimizar ambas**

❌ El problema es la necesidad de **sincronizar** ambos almacenes de datos


### Event Sourcing

✅ **Trazabilidad** del **estado** del **sistema**

❌ **Obtener** el **estado actual**



## Solución Óptima ~ Usar ambas

Usando ambas técnicas, tenemos lo bueno de ambas y mitigamos lo malo

+ **2** almacenes de datos con **optimización independiente**

+ **Trazabilidad** del estado del sistema en el tiempo

+ **Escrituras** más **rápidas**, ya que no hay UPDATES ni DELETES físicos

+ Sincronización más **sencilla** e **independiente** de las **escrituras**
    + Al Utilizar Event Sourcing en el Command Stack