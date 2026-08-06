---
tags:
  - 
  
---
El comando **ALTER TABLE** permite modificar una tabla ya existente sin eliminarla.  
Se usa para cambiar su estructura:

- Renombrar la tabla o columnas
- Cambiar tipos de datos
- Agregar o eliminar columnas
- Agregar o eliminar restricciones
- 
### Sintaxis básica
```SQL
ALTER TABLE nombre_tabla accion;
```

---

## Operaciones comunes
#### Agregar una columna
```SQL
ALTER TABLE usuarios ADD COLUMN description VARCHAR(50);
```

#### Eliminar una columna
```SQL
ALTER TABLE usuarios DROP COLUMN description;
```

#### Renombrar una columna
```SQL
ALTER TABLE usuarios RENAME COLUMN description TO comments;
```

####  Cambiar tipo de dato
_(Solo si no hay conflictos con datos o relaciones)_
```SQL
ALTER TABLE usuarios ALTER COLUMN age TYPE INTEGER;
```

---

## Restricciones con ALTER TABLE

####  Agregar NOT NULL
```SQL
ALTER TABLE usuarios ALTER COLUMN comments SET NOT NULL;
```

#### Quitar NOT NULL
```SQL
ALTER TABLE usuarios ALTER COLUMN comments DROP NOT NULL;
```
#BasesdeDatos