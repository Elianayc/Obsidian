---
tags:
  - DB
  - DBI2doparcial
---
El motor primero ordena los datos y luego agrupa los registros consecutivos.

**Conceptualmente**:
```text
ordenar → agrupar
```

**Generalmente se utiliza cuando**:
- los datos ya están ordenados,
- existe un índice útil,
- o el planner considera costoso utilizar hash.

---

#### Ventajas
- Menor consumo de memoria.
- Funciona bien con grandes volúmenes de datos.

#### Desventajas
- El ordenamiento puede ser costoso.

---

> [!Example]
> **En `EXPLAIN`**:
> 
> ```text
> Sort
> GroupAggregate
> ```
> 
#BasesdeDatos