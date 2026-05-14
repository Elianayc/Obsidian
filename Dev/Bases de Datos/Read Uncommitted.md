---
tags:
  - DBI2doparcial
  - DB
---
Cada consulta podría leer **datos sin confirmar de otras transacciones**.  
En este nivel, una transacción puede ver cambios que otra todavía no confirmó con COMMIT. Eso significa que podrías leer información que luego **desaparece** si la otra transacción hace ROLLBACK.

En la práctica, esto implica que lo que ves **puede no haber existido nunca realmente** en la base de datos.

> Si otra transacción está modificando esa misma fila, tu lectura podría ver los cambios aunque todavía no hayan sido confirmados, y en un escenario teórico incluso podrías basar tu operación en datos que luego sean revertidos por un ROLLBACK.

---

### Evita
- Ninguna anomalía garantizada por el estándar.  
    No ofrece protección formal contra inconsistencias.

### Permite
- **Dirty reads**: leer datos no confirmados que podrían revertirse.
- **Non-repeatable reads**: una misma fila puede cambiar entre consultas dentro de la transacción.
- **Phantom reads**: pueden aparecer o desaparecer filas entre ejecuciones de la misma consulta.
- Lecturas totalmente inconsistentes o “basura” temporal.

---

### Cómo funciona internamente
Es el nivel de aislamiento **más débil** del estándar SQL:

- Prioriza al máximo el rendimiento.
- Minimiza bloqueos y esperas.
- Sacrifica completamente la consistencia de las lecturas.

Por eso casi ningún motor moderno lo implementa realmente (o lo mapea a Read Committed).

---

### Por qué casi no se usa
Proporciona el mejor rendimiento posible, pero con riesgos muy altos:

- Podés tomar decisiones con datos que nunca fueron reales.
- Puede romper lógica de negocio fácilmente.
- Hoy se considera peligroso para la mayoría de las aplicaciones.

---

Importante en PostgreSQL: este nivel **no se implementa de verdad**. Si lo configurás, PostgreSQL lo trata como **Read Committed**, porque su modelo MVCC no permite dirty reads.

---
