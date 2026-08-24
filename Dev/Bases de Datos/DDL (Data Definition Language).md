---
tags:
  - 
  
---
DDL es el sublenguaje de SQL que permite **administrar la estructura de la base de datos**.

Sirve para **crear, modificar y eliminar objetos** como:
- Tablas
- Campos
- Índices
- Vistas

---

## Índices en DDL
- Se crean con:
```sql
CREATE INDEX
```

En PostgreSQL:

- Por defecto los índices son **B-Tree**
- La información de índices se guarda en la tabla del sistema:

```sql
pg_indexes
```

---

## Sentencias principales de DDL


### CREATE TABLE

Se utiliza para crear estructuras en la base de datos, como tablas o bases de datos.

```SQL
CREATE TABLE my_first_table (  first_column text,  second_column integer);
```

---

### ALTER TABLE

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

### Operaciones comunes

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

### Restricciones con ALTER TABLE

####  Agregar NOT NULL
```SQL
ALTER TABLE usuarios ALTER COLUMN comments SET NOT NULL;
```

#### Quitar NOT NULL
```SQL
ALTER TABLE usuarios ALTER COLUMN comments DROP NOT NULL;
```

---


### DROP
Se utiliza para eliminar completamente una tabla o base de datos.

```sql
DROP TABLE clientes;
```

---


### TRUNCATE
Se utiliza para eliminar todos los registros de una tabla sin eliminar su estructura.

```sql
TRUNCATE TABLE clientes;
```

---


### RENAME

Se utiliza para cambiar el nombre de una tabla.

```sql
ALTER TABLE clientes RENAME TO clientes_nuevos;
```


---

### COMMENT

Se utiliza para agregar comentarios descriptivos a tablas o columnas.

```sql
COMMENT ON TABLE clientes IS 'Tabla que almacena datos de clientes';
```

---

