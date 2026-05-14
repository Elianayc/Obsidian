---
tags:
  - DBI2doparcial
  - DB
---
Cada consulta toma un **snapshot nuevo de los datos al comenzar**.  

Esto significa que dentro de una misma transacción, **cada SELECT puede ver una versión distinta de la base**, porque siempre observa únicamente los datos que ya estaban confirmados en el momento en que empieza esa consulta (no cuando empieza la transacción).

>Si otra transacción está modificando esa misma fila, tu UPDATE queda esperando hasta que la primera haga COMMIT o ROLLBACK, y recién después se ejecuta sobre la versión confirmada de los datos.

---

### Evita
- **Dirty reads**: nunca vas a leer cambios que otra transacción todavía no confirmó. PostgreSQL usa MVCC, así que las lecturas siempre ven datos consistentes ya confirmados.

### Permite
- **Non-repeatable reads**: si volvés a consultar una misma fila dentro de la misma transacción, puede haber cambiado porque otra transacción la modificó y confirmó entre ambas consultas.
- **Phantom reads**: si repetís una consulta con condición (por ejemplo `WHERE salario > 1000`), pueden aparecer o desaparecer filas porque otra transacción insertó o eliminó registros que cumplen esa condición.

---

### Cómo funciona internamente

En _Read Committed_:
- El snapshot es **por consulta**, no por transacción.
- Cada sentencia ve la base como si tomara una “foto nueva” justo antes de ejecutarse.
- Por eso es rápido y tiene buena concurrencia: no mantiene una visión congelada de toda la transacción.

---

### Por qué es el nivel por defecto
Proporciona un muy buen equilibrio entre rendimiento y consistencia porque:

- evita lecturas sucias (lo más peligroso),
- reduce bloqueos largos,
- permite alta concurrencia,
- pero acepta pequeñas inconsistencias temporales dentro de la misma transacción.

---
