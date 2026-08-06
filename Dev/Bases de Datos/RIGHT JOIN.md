---
tags:
  - DBI1erparcial
  - DB
---
Devuelve todo de la tabla derecha + coincidencias.

```SQL
SELECT e.nombre, d.nombre_departamento
FROM empleados e
RIGHT JOIN departamentos d
ON e.id_departamento = d.id_departamento;
```

#BasesdeDatos