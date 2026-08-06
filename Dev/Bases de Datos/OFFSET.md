---
tags:
  - DBI1erparcial
  - DB
---
### OFFSET
Permite saltar registros antes de empezar a mostrar resultados.
```sql
SELECT *FROM empleados 
LIMIT 5 
OFFSET 10;
```

Salta los primeros 10 registros y muestra los siguientes 5.

#BasesdeDatos