---
tags:
  - DBI1erparcial
  - DB
---
Controla las [[Transacciones|transacciones]] (bloques de operaciones).
Sirve para asegurar consistencia en operaciones múltiples.

- [[BEGIN TRANSACTION]]
- [[COMMIT]]
- [[ROLLBACK]]
- [[SAVEPOINT]]
- [[SET TRANSACTION]]
- [[END TRANSACTION]]

##### Ejemplo de uso:
```sql
BEGIN TRANSACTION;

-- Definimos el nivel de aislamiento
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;

-- Punto de control por si algo falla en el medio
SAVEPOINT inicio_operacion;

-- Operación 1: descontar saldo
UPDATE cuentas
SET saldo = saldo - 100
WHERE id = 1;

-- Operación 2: acreditar saldo
UPDATE cuentas
SET saldo = saldo + 100
WHERE id = 2;

-- Validación intermedia
SELECT saldo FROM cuentas WHERE id = 1;

-- Si algo sale mal, podemos volver al savepoint
-- ROLLBACK TO SAVEPOINT inicio_operacion;

-- Si todo está correcto, confirmamos los cambios
COMMIT;

END TRANSACTION;
```