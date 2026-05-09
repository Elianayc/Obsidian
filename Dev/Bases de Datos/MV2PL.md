---
tags:
  - DBI2doparcial
  - DB
---
## Bloqueo de dos fases multiversión

**Combina:**
- MVCC
- Protocolo de bloqueos de dos fases

Distingue dos tipos de transacciones:


### Transacciones de solo lectura
- Reciben timestamp al comenzar.
- Leen versiones sin esperar bloqueos.  
    Nunca se bloquean.


### Transacciones de actualización
- Usan bloqueos compartidos para leer.
- Usan bloqueos exclusivos para escribir.
- Mantienen bloqueos hasta el commit.
- Al confirmar, asignan timestamp definitivo a las versiones creadas.

**Resultado**:
- Lecturas nunca esperan.
- Se mantiene serialización según orden de commit.

Este protocolo se usa en **DB comerciales reales**.
