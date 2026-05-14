---
tags:
  - DB
  - DBI2doparcial
---
Elimina dependencias cíclicas mediante descomposición en proyecciones.

**Precondición**
- Estar en 4FN

**Objetivos**
- Eliminar redundancia compleja entre múltiples tablas
- Evitar dependencias cíclicas
- Garantizar reconstrucción de datos sin pérdida

**Pasos**
1. Detectar dependencias cíclicas
2. Descomponer la tabla en varias proyecciones
3. Asegurar que la unión de tablas reconstruye los datos originales
4. Mantener integridad mediante joins