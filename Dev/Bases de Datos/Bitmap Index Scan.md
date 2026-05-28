---
tags:
  - DB
  - DBI2doparcial
---
Combina índices y acceso secuencial.

Primero construye un mapa de las páginas donde se encuentran los registros buscados y luego accede a ellas de forma agrupada.

Se utiliza generalmente cuando la consulta devuelve una cantidad intermedia de filas.