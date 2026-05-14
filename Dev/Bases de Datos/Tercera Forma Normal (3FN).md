---
tags:
  - DB
  - DBI2doparcial
---
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