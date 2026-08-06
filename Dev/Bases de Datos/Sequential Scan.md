---
tags:
---
El motor recorre toda la tabla fila por fila buscando los registros solicitados.

![[Pasted image 20260618120342.png]]

**Generalmente se utiliza cuando**:
- la tabla es pequeña,
- o la consulta devuelve una gran cantidad de registros.

> [!Example]
> Ejemplo de salida en `EXPLAIN`:
> 
> ```sql
> Seq Scan on table_dummy
> ```
> 
#BasesdeDatos