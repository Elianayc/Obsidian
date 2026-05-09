---
tags:
  - DBI1erparcial
  - DB
---
#### En orden lógico de uso

- [[FROM]] → de qué tabla vienen los datos
- [[JOIN]] → combinación de tablas
- [[WHERE]] → filtro de filas
- [[GROUP BY]] → agrupar datos
- [[HAVING]] → filtrar grupos
- **SELECT** → qué columnas mostrar
- [[ORDER BY]] → ordenar resultado
- [[LIMIT]] → cantidad de resultados

##### SELECT con alias
```SQL
SELECT nombre AS empleado FROM empleados;
```

##### SELECT con expresión
```sql
SELECT salario * 12 AS salario_anual FROM empleados;
```