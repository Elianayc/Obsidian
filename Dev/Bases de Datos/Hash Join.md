---
tags:
---
Es uno de los métodos más comunes y eficientes.

**El motor**:
1. Construye en memoria una tabla hash utilizando una de las tablas.
2. Recorre la otra tabla buscando coincidencias mediante hashes.


![[Pasted image 20260618120035.png]]


**Generalmente se utiliza cuando**:
- las tablas son medianas o grandes,
- y las condiciones del join utilizan igualdad (`=`).


> Es eficiente siempre que la estructura hash pueda almacenarse en memoria.

> [!Example]
> ```
> Tabla A → generar hashTabla B → buscar coincidencias en hash
> ```
> 
#BasesdeDatos