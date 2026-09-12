---
tags:
  - 
  
---
Agrupa registros que tienen valores iguales en una o más columnas.

```sql
SELECT 
	id_cliente, 
	SUM(monto)
FROM 
	pedidos
GROUP BY 
	id_cliente;
```

##### Resultado:
Agrupa los pedidos por cliente y suma sus montos.

---

### Reglas de GROUP BY

`GROUP BY` reúne las filas que comparten el mismo valor en una o más columnas y les aplica una función de agregación.

La regla de **dependencia funcional** establece que toda columna que aparezca en el `SELECT` y no esté dentro de una función de agregación debe figurar también en el `GROUP BY`.

Por ejemplo:

```sql
SELECT id_cliente, nombre, SUM(monto)
FROM pedidos
GROUP BY id_cliente, nombre;
```

MySQL valida esta regla mediante el modo `ONLY_FULL_GROUP_BY`, activado por defecto desde MySQL 5.7. Si se intenta seleccionar una columna que no está agrupada ni agregada, la consulta genera un error en lugar de devolver un valor arbitrario.

--

### WITH ROLLUP

Cuando se necesita agrupar por más de un criterio, MySQL permite utilizar `WITH ROLLUP` para generar automáticamente **subtotales por cada nivel de agrupamiento**.

```sql
SELECT tipo, año, SUM(monto)
FROM ventas
GROUP BY tipo, año WITH ROLLUP;
```

---

### GROUP BY y HAVING

En el orden de ejecución, `GROUP BY` forma los grupos después de `WHERE`.

El filtro que se aplica sobre los grupos ya formados es `HAVING`.

> `WHERE` → filtra filas  
> `GROUP BY` → forma grupos  
> `HAVING` → filtra grupos

---
