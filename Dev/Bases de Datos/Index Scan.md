---
tags:
  - DB
  - DBI2doparcial
---
El motor utiliza un índice para localizar directamente los registros necesarios sin recorrer toda la tabla.

![[Pasted image 20260618120423.png]]


**Suele ser más eficiente cuando**:
- la consulta devuelve pocos registros,
- y el `WHERE` utiliza columnas indexadas.

> [!Example]
> 
> ```sql
> Index Scan using idx_nombre on table_dummy
> ```
> 