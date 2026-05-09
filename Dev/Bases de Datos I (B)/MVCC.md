---
tags:
  - DBI2doparcial
  - DB
---
## Control de concurrencia multiversión

En **MVCC**, cada vez que una transacción escribe un dato, no lo reemplaza:  
crea una **nueva versión** del dato.

#### Cuando una transacción lee:

- El sistema elige la versión correcta del dato.
- Debe garantizar que el resultado sea equivalente a una ejecución secuencial (**serializabilidad**).
- La elección de la versión debe ser rápida para mantener buen rendimiento.

Varias versiones permiten que lecturas y escrituras convivan sin bloquearse.

---

#### MVCC + Marcas temporales
[[MVCC con marcas temporales]] 

#### MVCC + Bloqueo de dos fases
[[Bloqueo de dos fases multiversión (MV2PL)]]

---

[[PostgreSQL y MVCC]]

