---
tags:
  - DB
  - DBI2doparcial
---
Son los métodos que utiliza el motor de base de datos para realizar operaciones de [[Funciones de Agregación|agregación]] y agrupamiento de datos durante la ejecución de una consulta.

Se utilizan principalmente en consultas con:
- `GROUP BY`
- `COUNT`
- `SUM`
- `AVG`
- `MIN`
- `MAX`
- `DISTINCT`

El planner evalúa cuál método resulta más eficiente según:
- la cantidad de registros,
- el uso de memoria,
- el orden de los datos,
- y el costo estimado de ejecución.

Los principales métodos son:
- [[Hash Aggregate]]
- [[Sort Aggregate - Group Aggregate]]


> Las funciones de agregación (`COUNT`, `SUM`, `AVG`, etc.) son escritas por el usuario en la consulta SQL.  


> Los _Aggregation Methods_ son las estrategias internas que utiliza PostgreSQL para ejecutar dichas operaciones.

