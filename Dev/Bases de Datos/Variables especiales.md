---
tags:
  - DB
  - DBI2doparcial
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
