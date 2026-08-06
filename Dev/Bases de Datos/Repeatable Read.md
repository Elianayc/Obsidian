---
tags:
  - 
  
---
La transacción trabaja con un **snapshot fijo tomado al comenzar la transacción**.  
A diferencia de Read Committed, todas las consultas dentro de la misma transacción ven exactamente la **misma versión de los datos**, aunque otras transacciones confirmen cambios mientras tanto.

Esto hace que las lecturas sean estables durante toda la transacción.

> Si otra transacción está modificando esa misma fila, tu transacción sigue viendo siempre la misma versión inicial de los datos durante toda su ejecución, y al intentar actualizar puede esperar el bloqueo o fallar si PostgreSQL detecta un conflicto con el estado del snapshot.

---

### Evita
- **Dirty reads**
- **Non-repeatable reads**

Si volvés a consultar una misma fila dentro de la transacción, siempre verás el mismo valor, aunque otra transacción la haya modificado y confirmado después.

### Permite
- **Phantom reads** (según el estándar SQL)

En PostgreSQL es un caso particular: gracias a MVCC, este nivel evita la mayoría de phantom reads clásicos, pero aún pueden existir ciertas anomalías de serialización en escenarios complejos de concurrencia.

---

### Cómo funciona internamente

En Repeatable Read:
- El snapshot es **por transacción**, no por consulta.
- La base queda “congelada” para esa transacción.
- Las lecturas no bloquean escrituras y las escrituras no bloquean lecturas gracias a MVCC.

Esto aumenta la consistencia respecto a Read Committed, pero también puede generar más conflictos entre transacciones que modifican datos.

---

### Por qué usarlo
Proporciona un equilibrio más fuerte hacia la consistencia:

- Garantiza lecturas estables dentro de la transacción.
- Reduce anomalías de concurrencia.
- Mantiene buen rendimiento, aunque con más riesgo de conflictos que Read Committed.
#BasesdeDatos