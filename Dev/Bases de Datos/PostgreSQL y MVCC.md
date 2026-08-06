---
tags:
  - DBI2doparcial
  - DB
---
PostgreSQL implementa el control de concurrencia usando **MVCC**.

Cada consulta SQL ve una **instantánea (snapshot)** de la base de datos:
- La transacción trabaja sobre una versión consistente de los datos.
- No ve cambios intermedios de otras transacciones.  
 Esto garantiza el **aislamiento**.
 
---

### Ventaja principal frente a bloqueo tradicional

**En sistemas basados solo en bloqueos:**
- Lecturas pueden bloquear escrituras
- Escrituras pueden bloquear lecturas

**En PostgreSQL (MVCC):**
- Las lecturas **NO bloquean** escrituras.
- Las escrituras **NO bloquean** lecturas.

**Resultado:**
- Mucha menor contención.
- Mejor rendimiento en entornos multiusuario.

---

### Aislamiento fuerte: SSI
PostgreSQL mantiene esta garantía incluso en el nivel más alto de aislamiento usando:

---

### Serializable Snapshot Isolation (SSI)  
Permite comportamiento equivalente a ejecución serial sin perder rendimiento.

---

### Bloqueos siguen existiendo
Aunque usa MVCC:
- PostgreSQL también ofrece **bloqueos de tabla y fila**.
- Se usan cuando la aplicación necesita controlar conflictos explícitamente.

#BasesdeDatos