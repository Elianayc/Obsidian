---
tags:
  - 
  
---
### ¿Qué asegura?

- Las Clave primaria|claves primarias no se repiten ni pueden ser NULL
- Las Clave foránea|claves foráneas deben existir en la tabla “padre”
- No se pueden crear registros “huérfanos” en tablas hijas

### ¿Qué evita?
- Registros sin correspondencia en la tabla relacionada
- Eliminaciones o modificaciones que rompan relaciones entre tablas
#BasesdeDatos