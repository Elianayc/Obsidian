---
tags:
  - DB
  - DBI2doparcial
---
Son los métodos que utiliza el motor de base de datos para acceder a los datos de las tablas durante la ejecución de una consulta.

Los principales tipos de acceso son:

- [[Sequential Scan]]
- [[Index Scan]]
- [[Bitmap Index Scan]]

El planner evalúa qué método resulta menos costoso según:

- el tamaño de la tabla,
- la distribución de los datos,
- la cantidad estimada de registros,
- y la existencia de índices.
-

> No siempre un acceso indexado es más eficiente que uno secuencial.

Por ejemplo, si la consulta devuelve un porcentaje muy alto de filas de la tabla, el costo de utilizar el índice puede ser mayor que recorrer la tabla completa secuencialmente.

---

### Forzar ciertos planes de ejecución

En PostgreSQL pueden deshabilitarse ciertos métodos para pruebas:

```sql
SET enable_seqscan = false;
SET enable_bitmapscan = false;
SET enable_nestloop = false;
```

Esto influye en las decisiones del planner, aunque no garantiza completamente el uso de índices.

---

### Posibles causas de no utilización de índices

Aunque exista un índice, PostgreSQL puede decidir no utilizarlo si:

- la consulta devuelve demasiados registros,
- el costo estimado del índice es mayor,
- las estadísticas están desactualizadas,
- o la condición del `WHERE` no utiliza columnas indexadas.

---
