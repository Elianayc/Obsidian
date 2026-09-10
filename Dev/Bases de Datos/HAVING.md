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


|                                      | WHERE                                                                       | HAVING                                          |
| ------------------------------------ | --------------------------------------------------------------------------- | ----------------------------------------------- |
| **Momento de evaluación**            | Antes de agrupar, fila por fila                                             | Después de agrupar, grupo por grupo             |
| **¿Admite funciones de agregación?** | No                                                                          | Sí                                              |
| **¿Qué filtra?**                     | Filas individuales de las tablas de origen                                  | Grupos formados por `GROUP BY`                  |
| **Efecto en el rendimiento**         | Reduce las filas antes del agrupamiento, por lo que puede ser más eficiente | Actúa sobre los grupos después del agrupamiento |

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

![[Pasted image 20260910113346.png|711]]

---
