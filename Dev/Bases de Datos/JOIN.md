---
tags:
  - 
  
---
Permite combinar tablas relacionadas.
![[Pasted image 20260806142354.png|570]]

```SQL
SELECT e.nombre, d.nombre_departamento 
FROM empleados e 
JOIN departamentos d 
ON e.id_departamento = d.id_departamento;
```

- [[INNER JOIN]]
- [[LEFT JOIN]]
- [[RIGHT JOIN]]
- [[FULL OUTER JOIN]]

#BasesdeDatos