---
tags:
  - DB
  - DBI2doparcial
---
El motor recorre una tabla y, para cada fila encontrada, busca coincidencias en la otra tabla.

Conceptualmente funciona así:

```
para cada fila de tabla1:    buscar coincidencias en tabla2
```

Es eficiente cuando:
- una de las tablas tiene pocos registros,
- o existen índices que permiten encontrar rápidamente las coincidencias.

### Nested Loop + Sequential Scan

Si no existen índices útiles, PostgreSQL puede recorrer completamente la segunda tabla para cada fila de la primera.

Esto puede ser costoso en tablas grandes.

### Nested Loop + Index Scan

Si existe un índice sobre las columnas del join, el motor puede utilizarlo para buscar únicamente las filas necesarias.

Esto mejora significativamente el rendimiento.