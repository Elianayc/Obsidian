---
tags:
  - DBI1erparcial
  - DB
---
Un **índice** es una estructura que **mejora la velocidad de búsqueda de datos** en una tabla, copiando valores de uno o más campos.

Funciona como el índice de un libro: permite encontrar registros sin recorrer toda la tabla.

##### Importante:
- **No cambia los datos**, solo acelera la búsqueda.
- Se almacena **separado físicamente** de la tabla.
- Los datos de la tabla se guardan en **bloques/páginas de disco** y los índices en **estructuras separadas**.

---
## Cómo funcionan
Cuando se ejecuta una consulta:

- El [[Procesador de consultas]] decide si:
    - Hace un **escaneo secuencial** (recorre toda la tabla)
    - O usa un **índice** para acceder más rápido

No siempre el índice es mejor:
- En tablas pequeñas suele ser más rápido el **escaneo completo**.

---

## Impacto en rendimiento

**Ventajas**:
- Aceleran lecturas (**SELECT**)

**Desventajas**:
- Ralentizan escrituras (**INSERT, UPDATE, DELETE**)  
    → Los índices también deben actualizarse.

Más índices ≠ mejor rendimiento.  
Demasiados índices reducen el rendimiento de operaciones de alta/modificación/baja.

---

## Cómo funcionan
Cuando se ejecuta una consulta:
- El [[Procesador de consultas]] decide si:
    - Hace un **escaneo secuencial** (recorre toda la tabla)
    - O usa un **índice** para acceder más rápido

 No siempre el índice es mejor:
- En tablas pequeñas suele ser más rápido el **escaneo completo**.

---

## Impacto en rendimiento

**Ventajas**:
- Aceleran lecturas (**SELECT**)

**Desventajas**:
- Ralentizan escrituras (**INSERT, UPDATE, DELETE**)  
    → Los índices también deben actualizarse.

Más índices ≠ mejor rendimiento.  

Demasiados índices reducen el rendimiento de operaciones de alta/modificación/baja.

---

[[Tipos de índices]]
[[Crear índices en PostgreSQL]]
[[Clustering]]
[[Optimización de Consultas]]
[[Scan Methods]]
[[Join Methods]]
