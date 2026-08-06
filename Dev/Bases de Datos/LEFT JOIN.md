---
tags:
  - 
  
---
Devuelve todo de la tabla izquierda + coincidencias.

![[Pasted image 20260806144723.png]]



```SQL
SELECT e.nombre, d.nombre_departamento
FROM empleados e
LEFT JOIN departamentos d
ON e.id_departamento = d.id_departamento;
```

#BasesdeDatos