---
tags:
  - DBI2doparcial
  - DB
---
Cada consulta toma un **snapshot nuevo de los datos al comenzar.

### Evita
- Dirty reads

### Permite
- Non-repeatable reads
- Phantom reads

Proporciona un buen equilibrio entre rendimiento y consistencia.