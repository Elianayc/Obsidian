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



![[Pasted image 20260527155831.png|524]]


> [!info]
> https://www.querifylabs.com/blog/rule-based-query-optimization


### Salida del Comando EXPLAIN

```sql
QUERY PLAN
--------------------------------------------------------------------------------
Seq. Scan on table_dummy (cost=0.00..458.00 rows=10000 width=244)
```

Para cada consulta, el motor de base de datos arma un árbol de ejecución, donde cada nodo es un plan a ejecutar. 

- Por cada plan de ejecución que el motor realice se mostrará una fila (un nodo del árbol). 
- Para interpretar la salida del comando EXPLAIN, estos nodos deben leerse desde abajo hacia arriba. 

**Cada nodo presenta la siguiente información:** 
- Costo estimado para comenzar a devolver información 
- Costo estimado para finalizar la consulta 
- Cantidad estimadas de filas procesadas 
- Cantidad estimados de bytes 

**¿Qué tiene que evaluar el planner?** 
- [[Scan Methods]] (sequential, index, bitmap index)
- [[Join Methods]] (nested loops, hash join, merge join) 
- [[Aggregation Methods]] (hash, sort)