---
tags:
  - 
  
---
Agrupa registros que tienen valores iguales en una o más columnas.

```
SELECT id_cliente, SUM(monto)FROM pedidosGROUP BY id_cliente;
```

##### Resultado:  
Agrupa los pedidos por cliente y suma sus montos.
#BasesdeDatos