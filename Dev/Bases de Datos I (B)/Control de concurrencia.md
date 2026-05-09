---
tags:
  - DBI2doparcial
  - DB
---
Cuando varias transacciones se ejecutan al mismo tiempo:

- Pueden interferirse
- Pueden leer datos intermedios incorrectos
- Pueden dejar la base inconsistente

Por eso el DBMS usa **mecanismos de control de concurrencia**.

Objetivo: que ejecutar transacciones en paralelo sea equivalente a ejecutarlas **una detrás de otra**.

---
#### Mecanismos de control de concurrencia

==Los principales esquemas son==:
- Protocolos de **bloqueo**
- Ordenación por **marcas temporales**
- Técnicas de **validación**
- Esquemas **multiversión ([[MVCC]])

==Estos mecanismos==:
- Bloquean operaciones conflictivas  
    o
- Abortan transacciones problemáticas


 [[Fenómenos de concurrencia]]
 [[Niveles de aislamiento]]