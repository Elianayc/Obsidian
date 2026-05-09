---
tags:
  - DBI2doparcial
  - DB
---
Las transacciones garantizan las propiedades **ACID**:

==**Atomicidad**==
- Todas las operaciones se ejecutan o ninguna.
- Si ocurre un fallo → se restauran los valores anteriores.
- La gestiona el **componente de gestión de transacciones**.

==**Consistencia**==
- La base pasa de un estado válido a otro estado válido.
- Las reglas de integridad no deben violarse.
- Es responsabilidad del **programador + restricciones del sistema**.

==**Aislamiento**==
- Las transacciones concurrentes no deben interferirse.
- Cada transacción debe comportarse como si fuera la única ejecutándose.
- Lo maneja el **control de concurrencia**.

==**Durabilidad**==
- Una vez confirmada la transacción, los cambios permanecen incluso ante fallos.
- Se garantiza guardando los cambios en disco y permitiendo recuperarlos.
- Lo maneja el **gestor de recuperación**.

---

##### Ejemplo clásico (transferencia bancaria)
Transferir $50 de la cuenta A a la cuenta B:

**Problema sin transacciones:**
- Se descuenta dinero de A
- Ocurre un fallo antes de sumar a B  
    Se “pierde” dinero → estado inconsistente

**Gracias a ACID:**
- O se ejecuta toda la transferencia
- O se revierte completamente