---
tags:
  - DBI1erparcial
  - DB
---
Permite combinar tablas relacionadas.
```SQL
SELECT e.nombre, d.nombre_departamento 
FROM empleados e 
JOIN departamentos d 
ON e.id_departamento = d.id_departamento;
```

[[INNER JOIN]]
[[LEFT JOIN]]
[[RIGHT JOIN]]
[[FULL OUTER JOIN]]