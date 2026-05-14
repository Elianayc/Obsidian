---
tags:
  - DB
  - DBI2doparcial
---
Modelo completamente normalizado donde no existen anomalías.

**Precondición**
- Estar en 5FN (conceptual)

**Objetivos**
- Eliminar todas las anomalías posibles
- Garantizar dependencia directa de la clave primaria
- Llevar la base a un estado completamente normalizado

**Pasos**
1. Asegurar dependencia total de la clave primaria
2. Eliminar cualquier posible redundancia
3. Validar que no existan anomalías de inserción, actualización o eliminación
4. Centralizar toda validación en el modelo de datos