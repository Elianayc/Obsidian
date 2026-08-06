---
tags:
  - DBI1erparcial
  - DB
---
Es un campo que **referencia la clave primaria de otra tabla**, creando una relación entre ellas.

### Características:
- Puede repetirse (representa relaciones 1-N o N-M)
- Puede ser NULL (si la relación no es obligatoria)
- Debe coincidir con un valor existente en la tabla padre
- Una tabla puede tener varias claves foráneas
- Un campo solo puede participar en **una clave foránea**

### Ejemplo:
- `pais_id` en tabla Provincias → referencia a Países
#BasesdeDatos