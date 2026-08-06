---
tags:
---
## NEW
Representa la nueva versión de la fila.

Disponible en:
- `INSERT`
- `UPDATE`


> [!example]
> 
> ```sql
> NEW.nombre
> NEW.saldo
> ```
> 

---

## OLD
Representa la versión anterior de la fila.

Disponible en:
- `UPDATE`
- `DELETE`

> [!example]
> 
> ```sql
> OLD.nombre
> OLD.saldo
> ```
> 

----

En PostgreSQL, una función que será utilizada por un trigger:

- Debe devolver `trigger` (`RETURNS trigger`).
- **No recibe parámetros formales** en su declaración.
- El motor le proporciona automáticamente acceso a variables especiales como `NEW`, `OLD`, `TG_OP`, `TG_NAME`, etc.
    

> [!example]
> 
> ```sql
> CREATE OR REPLACE FUNCTION check_account_update()
> RETURNS trigger AS $$
> BEGIN
>     IF NEW.balance < 0 THEN
>         RAISE EXCEPTION 'No se permite saldo negativo.';
>     END IF;
> 
>     RETURN NEW;
> END;
> $$ LANGUAGE plpgsql;
> ```
> 
> No se define algo como:
> 
> ```sql
> FUNCTION check_account_update(new_balance NUMERIC)
> ```
> 
> porque los datos se acceden mediante `NEW` y `OLD`, que el motor pone a disposición automáticamente.


#BasesdeDatos