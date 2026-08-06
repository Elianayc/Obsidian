---
tags:
  - DB
  - DBI2doparcial
---
# Tercera Forma Normal
Elimina dependencias transitivas para que todos los atributos dependan directamente de la clave primaria.

**Precondición**
- Estar en 2FN

**Objetivos**
- Eliminar dependencias transitivas
- Evitar redundancia de datos
- Separar datos en tablas relacionadas correctamente

**Pasos**
1. Detectar dependencias transitivas
2. Eliminar atributos que dependan de otros atributos no clave
3. Crear nuevas tablas cuando sea necesario (N-M o datos comunes)
4. Eliminar campos calculados

---
### Separar dependencias parciales (2FN)


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

### Eliminar dependencias transitivas (3FN)


**Clientes**

|ID Cliente|Nombre|Tel|
|---|---|---|
|1|Ana|111|


**Pedidos**

|ID Cliente|Producto|
|---|---|
|1|Pan|
|1|Leche|

✔ Todo depende directamente de la clave  
✔ Sin redundancia obvia

---

#BasesdeDatos