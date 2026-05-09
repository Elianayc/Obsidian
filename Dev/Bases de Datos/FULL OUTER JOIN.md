---
tags:
  - DBI1erparcial
  - DB
---
# FULL OUTER JOIN
Devuelve todo de ambas tablas.
```SQL
SELECT e.nombre, d.nombre_departamento
FROM empleados e
FULL OUTER JOIN departamentos d
ON e.id_departamento = d.id_departamento;
```