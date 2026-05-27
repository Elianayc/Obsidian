---
tags:
  - DB
  - DBI2doparcial
---
### Hash Aggregate

El motor crea una estructura hash en memoria para agrupar los registros.

Conceptualmente:

```text
clave_del_grupo → acumulador
```

Ejemplo:

```sql
SELECT categoria, COUNT(*)
FROM productos
GROUP BY categoria;
```

PostgreSQL puede crear un hash donde:
- la clave es `categoria`,
- y el valor almacena el conteo acumulado.

#### Ventajas
- Muy rápido.
- No requiere ordenar previamente los datos.

#### Desventajas
- Consume memoria.
- Puede degradarse si el hash no entra completamente en RAM.

Ejemplo en `EXPLAIN`:

```text
HashAggregate
```
