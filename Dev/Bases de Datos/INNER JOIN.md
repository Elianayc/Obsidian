---
tags:
  - 
  
---
Devuelve solo coincidencias en ambas tablas.

![[Pasted image 20260806142649.png]]

```SQL
SELECT e.nombre, d.nombre_departamento
FROM empleados e
INNER JOIN departamentos d
ON e.id_departamento = d.id_departamento;
```


#BasesdeDatos