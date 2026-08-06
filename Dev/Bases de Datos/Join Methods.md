---
tags:
---
Son los métodos que utiliza el motor de base de datos para unir (_join_) los registros de múltiples tablas durante la ejecución de una consulta.

La elección del método de join es una de las decisiones más importantes del planner para optimizar consultas.

![[Pasted image 20260618115920.png|648]]

Los principales métodos son:
- [[Nested Loop]]
- [[Hash Join]]
- [[Merge Join]]
#BasesdeDatos