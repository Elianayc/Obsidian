---
tags:
  - 
  
---
Ordena los resultados de una consulta.

```SQL
SELECT * FROM pedidos ORDER BY monto DESC;
```

##### Resultado:  
Ordena los pedidos de mayor a menor monto.

---

### DESC / ASC
```SQL
ORDER BY salario DESC;
```


### Múltiples criterios
```SQL
ORDER BY salario DESC, nombre ASC;
```


### Orden por expresión
```SQL
ORDER BY LENGTH(nombre);
```


### NULL ordering
```SQL
ORDER BY salario IS NULL, salario DESC;
```

---

