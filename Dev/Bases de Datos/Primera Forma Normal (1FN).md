---
tags:
  - DB
  - DBI2doparcial
---
Elimina los grupos de campos repetidos, creando nuevas tablas y estableciendo una relación 1-N.

**Precondición**
- Ninguna

**Objetivos**
- Eliminar grupos de campos repetidos
- Asegurar que cada campo tenga valores atómicos
- Garantizar que todos los registros sean identificables por la clave primaria

**Pasos**
1. Eliminar grupos de campos repetidos
2. Definir claves primarias
3. Asegurar que todos los registros sean identificables por la clave primaria
4. Hacer que los campos no clave dependan de la clave primaria
5. Crear nuevas tablas para los grupos repetidos