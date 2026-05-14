---
tags:
  - DB
  - DBI2doparcial
---

|                Forma Normal                 | Precondición |                 Qué elimina                  |                                Idea clave                                 |
| :-----------------------------------------: | :----------: | :------------------------------------------: | :-----------------------------------------------------------------------: |
|     [[Primera Forma Normal (1FN)\|1FN]]     |      —       |     Grupos repetidos / datos no atómicos     |       Cada campo debe tener un solo valor y existir clave primaria        |
|     [[Segunda Forma Normal (2FN)\|2FN]]     |     1FN      |            Dependencias parciales            |            Todo atributo no clave depende de la clave completa            |
|     [[Tercera Forma Normal (3FN)\|3FN]]     |     2FN      |           Dependencias transitivas           |             Los atributos dependen solo de la clave primaria              |
| [[Forma Normal de Boyce-Codd (BCNF)\|BCNF]] |     3FN      | Dependencias con múltiples claves candidatas |           Toda dependencia funcional debe tener una superclave            |
|     [[Cuarta Forma Normal (4FN)\|4FN]]      |  3FN / BCNF  |          Dependencias multivaluadas          |             Se separan atributos multivaluados independientes             |
|     [[Quinta Forma Normal (5FN)\|5FN]]      |     4FN      |            Dependencias cíclicas             |          Descomposición en tablas que se recombinan sin pérdida           |
| [[Sexta Forma Normal (6FN-DKNF)\|6FN/DKNF]] |     5FN      |         Todas las anomalías posibles         | Modelo totalmente normalizado, cada dato depende directamente de la clave |
