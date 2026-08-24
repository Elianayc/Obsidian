---
tags:
---
# Sexta Forma Normal
Modelo completamente normalizado donde no existen anomalías.

**Precondición**
- Estar en 5FN (conceptual)

---

### ❌ Idea inicial (antes de 6FN)

|Empleado|Proyecto|Horario|
|---|---|---|
|Ana|Sistema|Mañana|
|Ana|App|Tarde|

**Problema**:
- Un mismo empleado puede tener distintos proyectos y horarios
- Todo está mezclado en una sola estructura
- Todavía hay dependencias implícitas


**Objetivos DKFN**
- Eliminar todas las anomalías posibles
- Garantizar dependencia directa de la clave primaria
- Llevar la base a un estado completamente normalizado

---

## ✔ En 6FN (DKNF)

Se lleva todo al extremo: **cada hecho mínimo en su propia tabla**

**Pasos**
1. Asegurar dependencia total de la clave primaria
2. Eliminar cualquier posible redundancia
3. Validar que no existan anomalías de inserción, actualización o eliminación
4. Centralizar toda validación en el modelo de datos


**Empleado-Proyecto**

|Empleado|Proyecto|
|---|---|
|Ana|Sistema|
|Ana|App|

**Empleado-Horario**

|Empleado|Horario|
|---|---|
|Ana|Mañana|
|Ana|Tarde|


Idea clave DKNF:
> cada dato depende directamente de la clave, sin ninguna dependencia oculta ni combinaciones complejas

---

### ⚠️ Importante 
- 6FN es más **teórica que práctica**
- Se usa casi solo en **modelos muy formales o temporales**
- En sistemas reales suele ser demasiado fragmentada

---

