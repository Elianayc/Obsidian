---
tags:
  - DBI2doparcial
  - DB
---
Es el nivel de aislamiento **más alto** del estándar SQL.  
Garantiza que el resultado de ejecutar transacciones concurrentes sea exactamente el mismo que si se hubieran ejecutado **una después de la otra en serie**.

La base de datos detecta situaciones peligrosas y puede **cancelar transacciones** para evitar inconsistencias.

> Si otra transacción está modificando esa misma fila, tu UPDATE puede esperar como en niveles anteriores, pero además el sistema puede abortar tu transacción con un error de serialización si detecta que ejecutar ambas operaciones en paralelo podría producir un resultado inconsistente.

---

### Evita
- **Dirty reads**
- **Non-repeatable reads**
- **Phantom reads**
- **Serialization anomalies**

Ofrece la máxima protección contra problemas de concurrencia.

### Permite
- No permite anomalías; en su lugar, puede producir errores de serialización que obligan a reintentar la transacción.

---

### Cómo funciona internamente
En PostgreSQL se implementa mediante **Serializable Snapshot Isolation (SSI)**:

- Analiza dependencias entre transacciones.
- Detecta posibles condiciones de carrera.
- Si detecta que el resultado podría no ser serializable, aborta una transacción con error de serialización.

Esto significa que la aplicación debe estar preparada para **reintentar la transacción**.

---

### Por qué usarlo
Proporciona la máxima consistencia:

- Ideal para sistemas financieros o críticos.
- Elimina anomalías de concurrencia.
- A cambio, tiene mayor costo y puede provocar abortos y reintentos de transacciones.

#BasesdeDatos