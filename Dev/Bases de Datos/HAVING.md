---
tags:
  - 
  
---
Filtra resultados después de un GROUP BY.

```sql
SELECT 
	id_cliente, SUM(monto)
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

![[Pasted image 20260910113346.png|711]]

---
