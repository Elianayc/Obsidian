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

### Uso básico de transacciones [[TCL]]

##### Temas Relacionados:
- [[Control de concurrencia]]

