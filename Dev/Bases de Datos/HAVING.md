---
tags:
  - DBI1erparcial
  - DB
---
Filtra resultados después de un GROUP BY.

```
SELECT id_cliente, SUM(monto)FROM pedidosGROUP BY id_clienteHAVING SUM(monto) > 3000;
```

##### Resultado:  
Muestra solo clientes cuyo total de compras supera 3000.
#BasesdeDatos