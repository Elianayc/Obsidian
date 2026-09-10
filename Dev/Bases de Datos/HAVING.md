---
tags:
  - 
  
---
Filtra resultados después de un `GROUP BY`.

```sql
SELECT 
	id_cliente, 
	SUM(monto)
FROM 
	pedidos
GROUP BY 
	id_cliente
HAVING 
	SUM(monto) > 3000;
```

##### Resultado:

Muestra solo clientes cuyo total de compras supera 3000.

---

### HAVING: filtrar después de agrupar

`HAVING` actúa sobre los **grupos ya formados por `GROUP BY`**, no sobre las filas originales.

Según el orden lógico de ejecución:

```text
FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT
```

`HAVING` se ejecuta inmediatamente después de `GROUP BY`.

Por eso puede utilizar **funciones de agregación** como `COUNT()`, `AVG()` y `SUM()` en su condición. `WHERE` no puede hacerlo porque se evalúa antes de que los grupos existan.


![[Pasted image 20260910113346.png|711]]


**Ejemplo:**

```sql
SELECT 
	id_cliente, 
	COUNT(*) AS cantidad_pedidos
FROM 
	pedidos
GROUP BY 
	id_cliente
HAVING 
	COUNT(*) > 5;
```

##### Resultado:
Muestra únicamente los clientes que realizaron **más de 5 pedidos**.

---
