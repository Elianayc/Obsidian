---
tags:
  - 
  
---
Devuelve todo de la tabla derecha + coincidencias.
![[Pasted image 20260806144800.png]]

```SQL
SELECT e.nombre, d.nombre_departamento
FROM empleados e
RIGHT JOIN departamentos d
ON e.id_departamento = d.id_departamento;
```

#BasesdeDatos