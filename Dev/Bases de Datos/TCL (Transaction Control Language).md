---
tags:
  - 
  
---
Controla las [[Transacciones|transacciones]] (bloques de operaciones).
Sirve para asegurar consistencia en operaciones múltiples.

### BEGIN TRANSACTION
Se utiliza para iniciar una transacción, agrupando varias operaciones como una unidad lógica.

```SQL
BEGIN TRANSACTION;
```


### COMMIT
Se utiliza para guardar permanentemente los cambios realizados dentro de una transacción.

```sql
COMMIT;
```


### ROLLBACK
Se utiliza para deshacer todos los cambios realizados dentro de una transacción no confirmada.

```sql
ROLLBACK;
```


### SAVEPOINT
Se utiliza para crear puntos intermedios dentro de una transacción, permitiendo volver a ese punto si es necesario.

```SQL
SAVEPOINT punto1;
```


### SET TRANSACTION
Se utiliza para definir propiedades de la transacción, como el nivel de aislamiento.

```sql
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
```


### END TRANSACTION
Se utiliza para finalizar una transacción (en algunos motores es implícito con COMMIT o ROLLBACK).

```sql
END TRANSACTION;
```


---

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

---

