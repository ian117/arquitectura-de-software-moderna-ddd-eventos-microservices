# Modelo del Dominio

### Elementos del Modelo de Dominio

❇️ **Entidades**
+ Clases con datos y comportamiento


❇️ **Value Objects**
+ Clases con simplemente datos
+ Sirven para representar de manera más claa los atributos de las entidades
+ Deben de ser **inmutables**

❇️ **Aggregates**
+ Grupos de entidades y value objects
+ Separan conceptos diferentes de nuestro dominio


✅ Como regla general, la comunicación entre distinros aggregates se debe hacer a **traves de la raíz** de los mismos. Una raíz no puede acceder a otro elemento no raíz de un aggregate diferente.