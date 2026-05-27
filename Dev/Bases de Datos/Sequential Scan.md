---
tags:
  - DB
  - DBI2doparcial
---
El motor recorre toda la tabla fila por fila buscando los registros solicitados.

Generalmente se utiliza cuando:

- la tabla es pequeña,
- o la consulta devuelve una gran cantidad de registros.

Ejemplo de salida en `EXPLAIN`:

```sql
Seq Scan on table_dummy
```
