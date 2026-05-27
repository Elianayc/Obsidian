---
tags:
  - DB
  - DBI2doparcial
---
El motor ordena ambas tablas según la clave del join y luego las recorre simultáneamente comparando los valores.

Es eficiente para grandes volúmenes de datos.

Ventajas:
- no requiere múltiples recorridos,
- puede aprovechar índices ya ordenados,
- y evita construir hashes en memoria.

Si las tablas ya están ordenadas mediante índices, PostgreSQL puede evitar la etapa de ordenamiento previo.

![[Pasted image 20260526162557.png]]