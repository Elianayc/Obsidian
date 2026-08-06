---
tags:
  - 
  
---
Permite combinar tablas relacionadas.

```SQL
SELECT e.nombre, d.nombre_departamento 
FROM empleados e 
JOIN departamentos d 
ON e.id_departamento = d.id_departamento;
```

[[INNER JOIN]] | [[FULL JOIN]] | [[LEFT JOIN]] | [[RIGHT JOIN]]

![[Pasted image 20260806144539.png]]


#BasesdeDatos