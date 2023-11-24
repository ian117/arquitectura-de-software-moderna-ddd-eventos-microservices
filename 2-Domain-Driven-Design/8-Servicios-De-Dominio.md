# Servicios De Dominio

+ Ejecutan **lógica** que **no tiene lugar** en ninguna de las **entidades**

+ Suele ser para **coordinar** dos o más **tipos** de **aggregates**, pero no tiene por qué

+ Son **parte** del **dominio**, no se crean de forma arbitrarria
    + Se identifican en las sesiones de brainstorming
    + Son parte del **lenguaje ubicuo**

+ Acciones como **_save, delete, upsert_**, **no** tienen cabida en los **servicios de dominio**


➡️ Estos servicios tienen lógica que representa parte del dominio. **No** tienen **conocimiento** de la **BBDD** ni de los **casos de uso**

### Servicios de Aplicación

En los SD podrían ir los **casos de uso** (usando el ejemplo de abajo, _consultar los paises con esperanza de vida mayor a X_ )


### Ejemplo

_Esperanza de vida en paises y estado fisico de personas_

Función / Método ➡️ Estimación de la esperanza de vida para una persona

+ Implementarlo en la entidad País
    + No tiene sentido de que el País calcule ese dato para una persona

+ Implementarlo en la entidad Persona
    + Podría tener sentido, pero **violaríamos el SRP** en esa entidad

➡️ ✅ La mejor opción es implementar esa lógica en un **servicio de dominio**, que coordine ambos aggregates

![](/images/2-Domain-Driven-Design/Captura%20de%20pantalla%202023-11-23%20183657.png)


```java
➡️ //Entidad
import com.danielblanco.examples.ddd.services.model.Country;
➡️ //Entidad
import com.danielblanco.examples.ddd.services.model.Person;

public class LifeExpectancyCalculator {

  public double calculateLifeExpectancy(Person person, Country country) {
    double healthFactor = person.healthFactor();
    double yearsOfAge = person.getYearsOfAge();
    double countryLifeExpectancyYears = country.getLifeExpectancyYears();
    double countryHaq = country.getHealthQualityIndexVal();

    double lifeExpectancy = countryLifeExpectancyYears * healthFactor * countryHaq;
    return Math.max(yearsOfAge, lifeExpectancy);
  }
}
```

En este ejemplo

El objetivo es usar **información** de **ambas entidades**

Se podría implementar en la Clase Person, pero esto rompería el **Single Responsability Principle**

Se hace una **Clase Intermedia** ~ **Servicio** que se encargue de interacturar con ambas entidades

### Resumiendo

Como este servicio trabaja con **entidades y objetos de valor** debería de ir entonces en el _**Servicio de Dominio**_

.

Si trabajara con
+ Una **transición** de **datos** entre la **interfaz de usuario** y la **capa de dominio**

+ Coordinando la ejecución de **casos de uso**

+ _Utilizando los servicios de dominio_ según sea necesario

Iría en la capa de _**servicios de la Aplicación**_
