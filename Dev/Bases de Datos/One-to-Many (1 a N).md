---
tags:
  - DBI1erparcial
  - DB
---
Un registro de una tabla puede relacionarse con varios registros de otra tabla.
Es la relación más común en bases de datos relacionales.

Ejemplo conceptual: un autor puede tener múltiples publicaciones.
- Una entidad → muchas entidades
- Ejemplo: país → provincias
- 
En la relación 1-N se utiliza la Clave foránea para vincular la tabla del lado 'Muchos' con la tabla del lado 'Uno', permitiendo que cada registro de la tabla 'hija' (N) identifique unívocamente al registro de la tabla 'padre' (1) al que pertenece.
