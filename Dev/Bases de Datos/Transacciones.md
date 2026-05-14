---
tags:
  - DBI2doparcial
  - DB
---
Una **transacción** es un conjunto de operaciones que forman una única unidad lógica de trabajo sobre la base de datos.

###### Debe cumplirse que:
- Se ejecuten **todas las operaciones** o **ninguna**.
- Si ocurre un fallo, deben **deshacerse los efectos parciales**.
- Si finaliza **correctamente**, sus cambios deben **permanecer**.

Las transacciones son iniciadas por programas de usuario (SQL, Java, C, etc.) y están delimitadas por instrucciones de inicio y fin de transacción.

Las transacciones deben cumplir las [[Propiedades ACID]]

---

### Estados inconsistentes temporales
Durante la ejecución de una transacción puede existir un estado intermedio inconsistente, pero:

- No debe ser visible para otras transacciones.
- Solo el resultado final debe ser visible.

Esto justifica la necesidad del **aislamiento**.

---

### Uso básico de transacciones: [[TCL]]

---

### Control de Concurrencia
Cuando varias transacciones se ejecutan al mismo tiempo:

- Pueden interferirse
- Pueden leer datos intermedios incorrectos
- Pueden dejar la base inconsistente

Por eso el DBMS usa **mecanismos de [[Control de concurrencia]].

Objetivo: que ejecutar transacciones en paralelo sea equivalente a ejecutarlas **una detrás de otra**.
