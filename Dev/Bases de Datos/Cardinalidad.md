---
tags:
  - 
  
---
Define la obligatoriedad de una relación.

Cero indica que la relación puede no existir.
Uno indica que la relación es opcional o única según el caso.
Muchos indica que puede haber múltiples registros relacionados.

---

### One-to-One (1 a 1)
Cada registro de una tabla se relaciona con un único registro de otra tabla.
Se utiliza normalmente para separar datos opcionales o reducir valores nulos.

Una entidad ↔ una entidad
Ejemplo: persona ↔ historia clínica

---

### One-to-Many (1 a N)
Un registro de una tabla puede relacionarse con varios registros de otra tabla.
Es la relación más común en bases de datos relacionales.

Ejemplo conceptual: un autor puede tener múltiples publicaciones.

- Una entidad → muchas entidades

- Ejemplo: país → provincias

En la relación 1-N se utiliza la Clave foránea para vincular la tabla del lado 'Muchos' con la tabla del lado 'Uno', permitiendo que cada registro de la tabla 'hija' (N) identifique unívocamente al registro de la tabla 'padre' (1) al que pertenece.

---

### Many-to-Many (N-N)

Un registro de una tabla puede relacionarse con muchos de otra, y viceversa.
Este tipo de relación se resuelve mediante una tabla intermedia o tabla de unión.

Ejemplo: alumnos ↔ materias

Se resuelve con:
   - [[Tabla intermedia]]
   - Dos relaciones 1–N

----
   
> [!info]
> 
> ![[Tipos de relaciones ERD.png]]
> 

---

