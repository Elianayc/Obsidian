---
tags:
  - DB
  - DBI2doparcial
---
Elimina dependencias multivaluadas entre atributos.

**Precondición**
- Estar en 3FN o BCNF

**Objetivos**
- Eliminar valores multivaluados independientes
- Reducir redundancia
- Mejorar la organización de datos repetidos independientes

**Pasos**
1. Identificar atributos multivaluados
2. Separar esos atributos en nuevas tablas
3. Relacionar cada nueva tabla con la tabla original
4. Mantener relaciones 1-N o N-M