# Modelo BBDD VS Modelo Dominio

Veremos un escenarios del modelo de persistencia y el modelo de dominio usando como ejemplo una abstracción de un partido de tenis


Es de hacer notar que 

+ El modelo de **persistencia** es muy recomendado para escenarios donde se necesita **información** y optimización a la **base de datos**
    + **CRUDS**, y acceso fácil y rápido a información en donde no existen muchos (o casi nulos) comportamientos y reglas

+ El modelo de **dominio** es importante para escenarios en donde el **comportamiento es clave**. 
    + Llevar en tiempo real el puntaje de un partido de tenis es un ejemplo



## Ejemplos

Estos ejemplos representan un juego de tenis

### Modelo BBDD Persistencia y su problema

El objetivo que el negocio tiene (en este ejemplo) es el de tener en tiempo real los datos de un juego de tenis

```java
public class TennisSet {
  int scorePlayer1;
  int scorePlayer2;

  // Getters and Setters
}
```

```java
import java.util.List;

public class TennisMatch {
  Long id;
  String player1;
  String player2;
  String winner;
  String status;
  List<TennisSet> sets;

  // Getters and Setters
}
```
En el **modelo de persistencia** solo se guardan **datos**

Se adaptan bien a la **persistencia** y a las **entidades** en la **BBDD**

+ Sencillo setear Setters & Getters para hacer **operaciones de escritura y lectura** en la BBDD

.

#### Problema ⚠️

+ ➡️ Al no tener **ninguna lógica** y **solo datos**, toda esa lógica que está relacionada con el dominio del tenis tiene que ser implementada en **servicios externos**

+ ➡️ Necesitamos **restricciones** sobre el **valor** que pueden tener los **datos internos** del sistema

+ ➡️ Es importante que las **reglas y comportamientos** funcionen a la hora de llevar a cabo la realización del dominio (en este caso el partido de tenis)

### Modelo Dominio

Se verá una gran diferencia con la siguiente forma

Una de ellas es la **implementación** y **nivel de acceso** de las **variables**

+ Se busca que se comparta lo mínimo necesario acceso de información.

    + Las constantes necesarias son **estáticas finales**
    + Existen **métodos** y **propiedades** **privadas** 
    + No se hacen getters y setters para todos

.

+ **Control** sobre lo que se **crea** y **existe** dentro del **dominio**
    + Solo **crear entidades** a traves de **constructores establecidos**
    + No se pueden hacer uso de setters para setear variables a nuestro antojo
    + Tenemos funciones que controlan el ciclo de vida (en este caso) del dominio del partido de tenis (start, finsh...)
.

En sí en todo el código se busca plasmar:

+ ✅ Una **representacion** del **dominio**. En este caso, del partido de tenis.

+ ✅ Una **manera** en la que las **acciones** que podemos realizar sobre las **entidades** estén **perfectamente controladas**

.

#### Entidades

##### TenisMatch

```java

import java.util.*;
import java.util.stream.Collectors;

public class TennisMatch {
  private static final int NUMBER_OF_SETS = 5;
  private static final int MAX_WARNINGS = 3;

  private Map<String, Player> players;
  private String player1;
  private String player2;
  private Status status;
  private List<TennisSet> sets;
  private TennisSet currentSet;
  private Player winner;

  public TennisMatch(String player1, String player2) {
    players = new HashMap<String, Player>();
    this.player1 = player1;
    this.player2 = player2;
    players.put(player1, new Player(player1, MAX_WARNINGS));
    players.put(player2, new Player(player2, MAX_WARNINGS));
    this.status = Status.NOT_STARTED;
    this.sets = new ArrayList<TennisSet>();
  }

  public void start() {
    if(this.status == Status.NOT_STARTED) {
      this.status = Status.IN_PROGRESS;
    }
  }

  public void finish(String winnerPlayer) {
    if(this.status == Status.IN_PROGRESS) {
      this.status = Status.FINISHED;
      this.winner = players.get(winnerPlayer);
    }
  }

  public void point(String player) {
    if(currentSet.addPoint(player)) {
      if(players.get(player).addSet() == NUMBER_OF_SETS) {
        finish(player);
      }

      advanceSet();
    }
  }

  private void advanceSet() {
    currentSet = new TennisSet(player1, player2);
    sets.add(currentSet);
  }

  public void warn(String player) {
    try {
      players.get(player).warn();
    } catch(MaxWarningReachedException e) {
      String winnerName = player.equals(player1) ? player1 : player2;
      finish(winnerName);
    }
  }

  public Player getWinner() {
    if(status == Status.FINISHED && winner != null) {
      return winner;
    }

    throw new NoWinnerException();
  }
}
```


##### TenisSet

```java
import java.util.HashMap;
import java.util.Map;

public class TennisSet {
  private static final int SET_POINTS = 6;
  private Map<String, Integer> points;

  public TennisSet(String player1, String player2) {
    points = new HashMap<String, Integer>();
    points.put(player1, 0);
    points.put(player2, 0);
  }

  public boolean addPoint(String player) {
    int playerPoints = points.get(player);
    playerPoints++;
    if(playerPoints == SET_POINTS) return true;
    points.put(player, playerPoints);
    return false;
  }
}
```

##### Player

```java
public class Player {
  private String name;
  private int setsWon;
  private int warnings;
  private int maxWarnings;

  public Player(String name, int maxWarnings) {
    this.name = name;
    this.warnings = 0;
    this.maxWarnings = maxWarnings;
    setsWon = 0;
  }

  public int addSet () {
    return ++setsWon;
  }

  public void warn() {
    warnings++;
    if(warnings == maxWarnings) {
      throw new MaxWarningReachedException();
    }
  }
}
```


##### Status

```java
public enum Status {
  NOT_STARTED,
  IN_PROGRESS,
  FINISHED,
}
```

##### NowinnerException

```java
public class NoWinnerException extends RuntimeException {
}
```

##### MaxWarningReachedException

```java
public class MaxWarningReachedException extends RuntimeException {
}
```

##### Notas

Las funciones como tal aplican todo lo visto anteriormente en cuestión de cuidar la estructura del dominio

+ Existe un control sobre lo que existe dentro de la aplicación
+ Satisfacen el objetivo del dominio (que es operar el partido de tenis)
+ Se aplica SOLID -> O -> Abierto a extensión y cerrado a modificación al usar clases, métodos y niveles de abstracción bien estructurados 

Sobre Enums que son objetos de valores

Sobre errores que son clean code

##### Aggregates