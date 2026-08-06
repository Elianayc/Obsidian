---
tags:
  - DBI1erparcial
  - DB
---
Es un campo (o conjunto de campos) que también debe ser **único entre registros**, pero con diferencias respecto a la clave primaria.

### Características:
- No permite valores repetidos
- Puede haber varias por tabla
- Puede ser NULL (a menos que se combine con NOT NULL)
- No se usa normalmente como referencia principal en relaciones

### Ejemplo:
- Email en una tabla de usuarios
#BasesdeDatos