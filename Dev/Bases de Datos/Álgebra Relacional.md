Es el fundamento formal del modelo relacional y la base para la optimización de consultas en los SGBD relacionales.

## Operaciones unarias

### Selección (σ)
- Filtra las filas que cumplen una condición.
- Produce una **partición horizontal**.
- Es conmutativa.

### Proyección (π)
- Selecciona columnas específicas.
- Elimina filas duplicadas.
- Produce una **partición vertical**.

---

## Operaciones de teoría de conjuntos

> Requieren relaciones compatibles (mismo número de atributos y dominios equivalentes).

### Unión (∪)
- Combina todas las tuplas de ambas relaciones.

### Intersección (∩)
- Devuelve las tuplas presentes en ambas relaciones.

### Diferencia (-)
- Devuelve las tuplas presentes en la primera relación pero no en la segunda.

---

## Operaciones binarias y especiales

### Producto cartesiano (×)
- Combina cada tupla de una relación con todas las de la otra.
- Si una relación tiene **n** registros y la otra **m**, el resultado contiene **n × m** registros.

### JOIN (⋈)
Combina tuplas relacionadas según una condición.

Tipos principales:

- **Inner Join** → conserva solo las coincidencias.
- **Left Outer Join** → conserva todas las filas de la tabla izquierda.
- **Right Outer Join** → conserva todas las filas de la tabla derecha.
- **Full Outer Join** → conserva todas las filas de ambas tablas.

Cuando no existe coincidencia, los atributos faltantes se completan con **NULL**.

### División (÷)
Permite responder consultas del tipo:

> "Obtener las entidades que cumplen con **todos** los criterios especificados."

---
