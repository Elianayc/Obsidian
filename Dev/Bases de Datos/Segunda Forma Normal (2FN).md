---
tags:
  - DB
  - DBI2doparcial
---
Elimina valores estáticos o repetidos creando nuevas tablas con relaciones N-1.

**Precondición**
- Estar en 1FN

**Objetivos**
- Evitar duplicación de datos
- Eliminar dependencias parciales
- Lograr que las nuevas tablas tengan clave primaria simple

**Pasos**
1. Asegurar dependencia funcional completa de la clave primaria
2. Eliminar dependencias parciales
3. Crear nuevas tablas para los campos que dependen parcialmente