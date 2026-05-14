---
tags:
  - DB
  - DBI2doparcial
---
# Cuarta Forma Normal
Elimina dependencias multivaluadas entre atributos.

**Precondición**
- Estar en 3FN o BCNF

---

### ❌ NO 4FN

|Alumno|Idioma|Deporte|
|---|---|---|
|Ana|Inglés|Tenis|
|Ana|Inglés|Fútbol|
|Ana|Francés|Tenis|
|Ana|Francés|Fútbol|

**Problema**:
- Idiomas y deportes son **independientes**
- Se mezclan y generan combinaciones innecesarias (explosión de filas)


**Objetivos 4FN**
- Eliminar valores multivaluados independientes
- Reducir redundancia
- Mejorar la organización de datos repetidos independientes

---

### ✔ Se separa en dos tablas

**Pasos**
1. Identificar atributos multivaluados
2. Separar esos atributos en nuevas tablas
3. Relacionar cada nueva tabla con la tabla original
4. Mantener relaciones 1-N o N-M

**Idiomas**

|Alumno|Idioma|
|---|---|
|Ana|Inglés|
|Ana|Francés|

**Deportes**

|Alumno|Deporte|
|---|---|
|Ana|Tenis|
|Ana|Fútbol|

Idea clave 4FN:
> separar atributos multivaluados independientes para evitar combinaciones falsas

---