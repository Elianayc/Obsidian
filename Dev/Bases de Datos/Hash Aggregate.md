---
tags:
---
El motor crea una estructura hash en memoria para agrupar los registros.

**Conceptualmente**:
```text
clave_del_grupo → acumulador
```

> [!Example]
> 
> ```sql
> SELECT categoria, COUNT(*)
> FROM productos
> GROUP BY categoria;
> ```
> 

**PostgreSQL puede crear un hash donde**:
- la clave es `categoria`,
- y el valor almacena el conteo acumulado.

---

#### Ventajas
- Muy rápido.
- No requiere ordenar previamente los datos.

#### Desventajas
- Consume memoria.
- Puede degradarse si el hash no entra completamente en RAM.

---

> [!Example]
> 
> **En `EXPLAIN`**:
> 
> ```text
> HashAggregate
> ```
> 
#BasesdeDatos