---
tags:
  - DBI1erparcial
  - DB
---
También llamados columnas o atributos en una **Tabla**.  

Representan cada una de las características de las entidades y se repiten en todos los registros de la tabla.

### Sintaxis de un campo

```SQL
nombre_campo tipo_dato restricciones
```

[[Tipos de datos DB]]

---

## Restricciones más usadas
- **NOT NULL** → el campo es obligatorio
- **UNIQUE** → no se puede repetir el valor
- **PRIMARY KEY** → identificador único (NOT NULL + UNIQUE)
- **CHECK** → valida condiciones sobre el campo
- **REFERENCES** → define clave foránea

---

### Tabla usuarios
```SQL
CREATE TABLE usuarios (
id bigserial PRIMARY KEY,  
name character varying (30) NOT NULL,  
surname character varying (30) NOT NULL,  
email character varying (30) NOT NULL UNIQUE,  
age smallint CHECK (age > 0),  
type char DEFAULT ('C')
);
```
#BasesdeDatos