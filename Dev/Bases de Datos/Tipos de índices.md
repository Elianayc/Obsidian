---
tags:
---
- [[B-Tree]]
- [[GIST]]
- [[GIN]]
- [[Índices por expresión]]
- [[Índices parciales]]

## B-Tree

- El más común
- Ideal para valores únicos
- Permite datos ordenados
- Buen rendimiento general y concurrencia

![[Pasted image 20260527152926.png]]

---

## Generalized Search Tree

- Para datos complejos
- Ideal para datos geográficos o estructuras no tradicionales
- “Índice flexible” para casos especiales

![[Pasted image 20260526162245.png]]

---

## Generalized Inverted Index

- Ideal para datos con muchos duplicados
- Usado en JSON, arrays y documentos
- Cada clave apunta a varias filas

---

## Índices por Expresión

- Se crean a partir de una función o cálculo
- Ejemplo: `lower(nombre)`

---

## Índices Parciales

- Se aplican solo a un subconjunto de filas
- Reducen tamaño y costo del índice
- Ejemplo: solo clientes de un estado

---



