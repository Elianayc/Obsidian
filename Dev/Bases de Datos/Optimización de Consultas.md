---
tags:
  - DB
  - DBI2doparcial
---
SQL es un lenguaje declarativo, esto significa que podemos decirle **qué** hacer pero no **cómo**.

El motor de DB por cada consulta evalúa distintos planes de ejecución seleccionando el menos costoso en cuestión de tiempo.

El comando **EXPLAIN** permite ver, evaluar y mejorar el plan de ejecución.

```sql
EXPLAIN select * from table_dummy;
EXPLAIN VERBOSE select * from table_dummy;
```

![[Pasted image 20260527155220.png]]