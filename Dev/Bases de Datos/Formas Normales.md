---
tags:
  - DB
  - DBI2doparcial
---

|                Forma Normal                 | Precondición |                 Qué elimina                  |                                Idea clave                                 |
| :-----------------------------------------: | :----------: | :------------------------------------------: | :-----------------------------------------------------------------------: |
|     [[1FN\|1FN]]     |      —       |     Grupos repetidos / datos no atómicos     |       Cada campo debe tener un solo valor y existir clave primaria        |
|     [[2FN\|2FN]]     |     1FN      |            Dependencias parciales            |            Todo atributo no clave depende de la clave completa            |
|     [[3FN\|3FN]]     |     2FN      |           Dependencias transitivas           |             Los atributos dependen solo de la clave primaria              |
| [[3.5 - BCNF\|BCNF]] |     3FN      | Dependencias con múltiples claves candidatas |           Toda dependencia funcional debe tener una superclave            |
|     [[4FN\|4FN]]      |  3FN / BCNF  |          Dependencias multivaluadas          |             Se separan atributos multivaluados independientes             |
|     [[5FN\|5FN]]      |     4FN      |            Dependencias cíclicas             |          Descomposición en tablas que se recombinan sin pérdida           |
| [[6FN - DKNF\|6FN/DKNF]] |     5FN      |         Todas las anomalías posibles         | Modelo totalmente normalizado, cada dato depende directamente de la clave |

---

##### ¿Todo se basa en dividir tablas hasta lo mínimo?

En 1FN no estás “afinando relaciones”, solo estás eliminando cosas mal formadas (listas dentro de una celda). Es como ordenar la mesa antes de trabajar.

En 2FN ya no es cualquier división: estás atacando el problema de que una clave compuesta “arrastra” datos que no dependen de toda la clave. O sea, no es “separo todo”, es “separo lo que depende mal”.

En 3FN el foco es otro: dependencias indirectas. A → B → C. No es fragmentar por gusto, es cortar esa cadena.

BCNF es más quirúrgico todavía: arregla casos donde “la regla de negocio” no coincide con las claves que definiste. Es más lógico que estructural.

4FN y 5FN ya no son “hacer más tablas porque sí”, sino resolver tipos muy específicos de redundancia (listas independientes y combinaciones múltiples). Si no existe ese problema, no separás nada.

Y 6FN sí se acerca a dividir todo en tablas mínimas, pero justamente por eso casi no se usa en la vida real: es tan granular que puede volverse impráctico.

---

### Ejemplo de clase


**0FN**

![[0FN.png]]


**1FN**

![[1FN.png]]


**2FN**

![[2FN.png]]


**3FN**

![[3FN.png]]


**4FN**

![[4FN.png]]


**5FN**

![[5FN.png]]