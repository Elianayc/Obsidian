---
tags:
  - DBI2doparcial
  - DB
---
### Lectura no repetible
Una transacción lee un dato, otra transacción lo modifica y confirma, y al volver a leerlo el valor cambió.

Ejemplo típico: reportes largos que cambian durante la ejecución.