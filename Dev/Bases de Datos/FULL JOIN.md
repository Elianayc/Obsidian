---
tags:
  - 
  
---
Devuelve todo de ambas tablas.
![[Pasted image 20260806144622.png]]

```SQL
SELECT e.nombre, d.nombre_departamento
FROM empleados e
FULL OUTER JOIN departamentos d
ON e.id_departamento = d.id_departamento;
```

#BasesdeDatos