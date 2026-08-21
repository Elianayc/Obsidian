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

#### Sentencias principales de DDL

- [[CREATE TABLE]]
- [[ALTER TABLE]]
- [[DROP]]
- [[TRUNCATE]]
- [[RENAME]]
- [[COMMENT]]

---

