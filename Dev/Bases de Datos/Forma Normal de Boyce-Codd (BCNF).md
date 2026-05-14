---
tags:
  - DB
  - DBI2doparcial
---
Elimina dependencias donde existan múltiples claves candidatas.

**Precondición**
- Estar en 3FN

**Objetivos**
- Resolver casos donde hay varias claves candidatas
- Asegurar que cada determinante sea una superclave
- Reducir anomalías en estructuras complejas

**Pasos**
1. Identificar claves candidatas
2. Separar en nuevas tablas si existen múltiples claves candidatas
3. Mantener relaciones entre tablas resultantes