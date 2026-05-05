Un índice es una estructura que **mejora la velocidad de búsqueda de datos** en una tabla, copiando valores de uno o más campos.

Funciona como el índice de un libro: permite encontrar registros sin recorrer toda la tabla.

#### Cuando se ejecuta una consulta:
- El [[Procesador de consultas]] decide si:
    - Hace un **escaneo secuencial** (recorre toda la tabla)
    - O usa un **índice** para acceder más rápido

No siempre el índice es más rápido (en tablas pequeñas, conviene escaneo completo)


## Impacto en rendimiento
- Los índices aceleran lecturas (SELECT)
- Pero **ralentizan escrituras** (INSERT, UPDATE, DELETE)
    - Porque también deben actualizarse los índices

Más índices ≠ mejor siempre


### [[Tipos de índices]]

