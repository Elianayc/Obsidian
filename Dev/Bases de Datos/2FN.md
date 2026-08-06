---
tags:
  - DB
  - DBI2doparcial
---
# Segunda Forma Normal
Elimina valores estáticos o repetidos creando nuevas tablas con relaciones N-1.

**Precondición**
- Estar en 1FN

---

### Separar valores atómicos (1FN)

|Cliente|Producto|Tel|
|---|---|---|
|Ana|Pan|111|
|Ana|Leche|111|

✔ Sin listas en una celda  
❌ Pero sigue repitiendo datos


**Objetivos de 2FN**
- Evitar duplicación de datos
- Eliminar dependencias parciales
- Lograr que las nuevas tablas tengan clave primaria simple

---

### Separar dependencias parciales (2FN)

**Pasos**
1. Asegurar dependencia funcional completa de la clave primaria
2. Eliminar dependencias parciales
3. Crear nuevas tablas para los campos que dependen parcialmente


**Clientes**

| Cliente | Tel |
| ------- | --- |
| Ana     | 111 |


**Pedidos**

|Cliente|Producto|
|---|---|
|Ana|Pan|
|Ana|Leche|

✔ Tel no se repite  
❌ Aún puede haber dependencias transitivas

---

#BasesdeDatos