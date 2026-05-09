---
tags:
  - DBI2doparcial
  - DB
---
Cada transacción tiene una **marca temporal (timestamp)** asignada antes de empezar.

Cada versión de un dato Q guarda:
- valor del dato
- timestamp de escritura
- timestamp de última lectura

---

### Reglas básicas
Cuando una transacción Ti:

**Lee Q**
- Lee la versión más reciente anterior a su timestamp.

**Escribe Q**
- Si otra transacción ya leyó esa versión → Ti se aborta.
- Si no → se crea una nueva versión del dato.

---

#### Ventajas
- Las lecturas **nunca esperan ni fallan**.
- Ideal porque en bases de datos se lee mucho más de lo que se escribe.

#### Desventajas
- Leer implica actualizar metadata (más accesos a disco).
- Los conflictos se resuelven con **abortos**, no con esperas (puede ser costoso).
