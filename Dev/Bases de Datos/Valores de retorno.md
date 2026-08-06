---
tags:
  - DB
  - DBI2doparcial
---
Las funciones trigger deben retornar un valor especial.

### En triggers `BEFORE`

Normalmente:
```sql
RETURN NEW;
```
Permite continuar la operación.

También puede retornarse:
```sql
RETURN NULL;
```
para cancelar la operación sobre esa fila.

---

### En triggers `AFTER`

El valor retornado es ignorado, pero por convención suele escribirse:
```sql
RETURN NEW;
```
o
```sql
RETURN NULL;
```

#BasesdeDatos