---
tags:
  - DB
  - DBI2doparcial
---
El motor utiliza un índice para localizar directamente los registros necesarios sin recorrer toda la tabla.

Suele ser más eficiente cuando:

- la consulta devuelve pocos registros,
- y el `WHERE` utiliza columnas indexadas.

Ejemplo:

```sql
Index Scan using idx_nombre on table_dummy
```
