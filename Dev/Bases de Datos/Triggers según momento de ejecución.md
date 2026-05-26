---
tags:
  - DB
  - DBI2doparcial
---

## BEFORE
Se ejecuta antes de realizar la operación.

Permite:
- validar datos
- modificar valores antes de guardarlos
- cancelar la operación mediante una excepción

> [!example]
> 
> ```sql
> CREATE TRIGGER validar_saldo
> BEFORE UPDATE ON cuentas
> FOR EACH ROW
> EXECUTE FUNCTION check_account_update();
> ```
> 

---

## AFTER
Se ejecuta después de que la operación fue realizada exitosamente.

Se utiliza para:
- auditorías
- logs
- acciones secundarias

> [!example]
> 
> 
> ```sql
> CREATE TRIGGER log_update
> AFTER UPDATE ON cuentas
> FOR EACH ROW
> EXECUTE FUNCTION registrar_cambio();
> ```
> 
