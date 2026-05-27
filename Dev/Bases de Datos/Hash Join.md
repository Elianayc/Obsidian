---
tags:
  - DB
  - DBI2doparcial
---
El motor:
1. Construye en memoria una tabla hash utilizando una de las tablas.
2. Recorre la otra tabla buscando coincidencias mediante hashes.

Es uno de los métodos más comunes y eficientes.

Generalmente se utiliza cuando:
- las tablas son medianas o grandes,
- y las condiciones del join utilizan igualdad (`=`).

> Es eficiente siempre que la estructura hash pueda almacenarse en memoria.

Ejemplo conceptual:
```
Tabla A → generar hashTabla B → buscar coincidencias en hash
```