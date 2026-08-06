---
tags:
  - DBI2doparcial
  - DB
---
El estándar SQL define **4 niveles de aislamiento** de transacciones:

- [[Read Uncommitted]]
- [[Read Committed]]
- [[Repeatable Read]]
- [[Serializable]]

Cuanto más alto el nivel → **menos problemas de concurrencia**, pero **más costo en rendimiento**.

El nivel más estricto es **Serializable**: garantiza que ejecutar transacciones en paralelo produce el mismo resultado que ejecutarlas una por una.

---

#### Nivel de Aislamiento vs Fenómeno

|   Nivel/Fenómeno    |    Dirty Read     | Non Repeteable Read |   Phantom Read    | Serialization Anomaly |
| :-----------------: | :---------------: | :-----------------: | :---------------: | :-------------------: |
| **Read Uncommited** | Sí, no en Postgre |         Sí          |        Sí         |          Sí           |
|  **Read Commited**  |         X         |         Sí          |        Sí         |          Sí           |
| **Repeteable Read** |         X         |          X          | Sí, no en Postgre |          Sí           |
|  **Serializable**   |         X         |          X          |         X         |           X           |

---

## Comando para definir aislamiento
Se usa dentro de TCL:

```sql
SET TRANSACTION ISOLATION LEVEL ...
```

---

#BasesdeDatos