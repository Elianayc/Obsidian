---
tags:
  - DBI1erparcial
  - DB
---
Una **tabla intermedia** se usa para resolver relaciones de tipo **muchos a muchos (N-M)** entre dos tablas. 
Su función es evitar la redundancia y transformar la relación en dos relaciones **1-N**.
Contiene las claves foráneas de ambas tablas y, en general, puede tener una clave primaria compuesta.

#### Ejemplo: 
entre **Alumno** y **Materia** se crea la tabla **Inscripción**.

#### Consulta con JOIN:
```sql
SELECT a.nombre, m.nombre_materia
FROM alumnos a
JOIN inscripciones i 
ON a.id_alumno = i.id_alumnoJOIN materias m 
ON i.id_materia = m.id_materia;
```
La tabla intermedia permite conectar dos tablas que no se pueden relacionar directamente en el modelo relacional.
#BasesdeDatos