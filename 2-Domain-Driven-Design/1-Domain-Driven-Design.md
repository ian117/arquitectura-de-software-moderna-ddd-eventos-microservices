# Domain Driven Design

## Arquitectura Centrada en los Datos

Es usual que siempre empecemos nuestro desarrollo con este tipo de arquitectura

+ Se piensa primero en los **datos que se necesitan almacenar**
+ Se recompilan requisitos para tener claras las **reglas de negocio**
+ Diseño del modelo de datos
+ Diseñamos y construimos nuestro sistema para **trabajar con los datos**
+ Como consecuencia, tenemos una **arquitectura de software totalmente dependiente de los datos**

## Arquitectura Centrada en el Dominio

La arqu. centrada en los datos contrasta a la del dominio[^1]

Cuando se centra en el dominio[^1]:

+ Se piensa primero en el **dominio[^1] del problema**
+ El objetivo es ser expertos en el dominio[^1]
+ Se modelan todas las **entidades y reglas** específicas del dominio[^1]
+ A partir de ahí, se implementan los casos de uso que queremos resolver 


### Tiempo de desarrollo

DDD vs Centrada en Datos. Al final una arqu. centrada en el **domino**, es **lenta al principio**, pero conforme pasa el tiempo, la **complejidad nunca se tiene que adaptar** de manera **exponencial** por lo que no se tienen que escatimar muchos recursos conforme pasa el tiempo.


+ El **dominio[^1]** es **invariable**
+ Los **casos de uso son mucho más inestables**, tienden a cambiar con el tiempo


➡️ Separando los casos de uso y las reglas del dominio[^1] conseguimos **independizar** dos partes con **inestabilidades muy diferentes**

➡️ Esto hace que nuestro sistema sea mucho más flexible


En un proyecto que va para largo en **tiempo y tamaño**, el diseño guiado por el **dominio[^1] es mejor**


[^1]: Dominio: _**Contexto en el cual se desarrolla un sistema de software y en el que reside la lógica empresarial**_
    Conocimiento, actividad y problemáticas alrededor de un negocio