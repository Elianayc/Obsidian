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


### ❌ NO 5FN

|Proveedor|Pieza|Proyecto|
|---|---|---|
|A|Tornillo|Casa|
|A|Tornillo|Puente|
|A|Tuerca|Casa|
|B|Tornillo|Casa|

**Problema**:
- Los datos dependen de combinaciones entre **3 entidades**
- Se pueden reconstruir desde relaciones más simples
- Hay redundancia por combinaciones innecesarias

---

### ✔ Se descompone en 3 tablas

**Proveedor-Pieza**

|Proveedor|Pieza|
|---|---|
|A|Tornillo|
|A|Tuerca|
|B|Tornillo|

**Proveedor-Proyecto**

|Proveedor|Proyecto|
|---|---|
|A|Casa|
|A|Puente|
|B|Casa|

**Pieza-Proyecto**

|Pieza|Proyecto|
|---|---|
|Tornillo|Casa|
|Tornillo|Puente|
|Tuerca|Casa|

Idea clave 5FN:
> separar relaciones complejas en partes más simples sin perder información al recombinar