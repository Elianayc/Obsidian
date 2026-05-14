---
tags:
  - DB
  - DBI2doparcial
---
# Primera Forma Normal
Elimina los grupos de campos repetidos, creando nuevas tablas y estableciendo una relación 1-N.

**Precondición**
- Ninguna

---

### Base sin normalizar (0FN)

|Cliente|Pedido|
|---|---|
|Ana|Producto: Pan, Leche; Tel: 111|
|Ana|Producto: Pan; Tel: 111|

 **Problema**: datos repetidos, listas dentro de una celda, redundancia.
 

**Objetivos de 1FN**
- Eliminar grupos de campos repetidos
- Asegurar que cada campo tenga valores atómicos
- Garantizar que todos los registros sean identificables por la clave primaria


----

### Separar valores atómicos (1FN)

**Pasos**
1. Eliminar grupos de campos repetidos
2. Definir claves primarias
3. Asegurar que todos los registros sean identificables por la clave primaria
4. Hacer que los campos no clave dependan de la clave primaria
5. Crear nuevas tablas para los grupos repetidos

|Cliente|Producto|Tel|
|---|---|---|
|Ana|Pan|111|
|Ana|Leche|111|

✔ Sin listas en una celda  
❌ Pero sigue repitiendo datos

----
