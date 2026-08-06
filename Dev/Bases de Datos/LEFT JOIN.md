---
tags:
  - DBI1erparcial
  - DB
---
# LEFT JOIN
Devuelve todo de la tabla izquierda + coincidencias.
```SQL
SELECT e.nombre, d.nombre_departamento
FROM empleados e
LEFT JOIN departamentos d
ON e.id_departamento = d.id_departamento;
```

#BasesdeDatos