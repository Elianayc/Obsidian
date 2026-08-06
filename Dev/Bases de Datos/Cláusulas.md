---
tags:
  - DBI1erparcial
  - DB
---
![[Pasted image 20260527160648.png]]

> [!info]
> 
> ### Orden lógico de ejecución de una consulta SQL
> 
> Aunque el `SELECT` se escribe primero, el motor evalúa la consulta aproximadamente en este orden:
> 
> - [[FROM]] → origen de los datos
> - [[JOIN]] → combinación de tablas
> - [[WHERE]] → filtro de filas
> - [[GROUP BY]] → agrupación de registros
> - [[HAVING]] → filtro sobre grupos
> - [[SELECT]] → columnas y expresiones a devolver
> - [[ORDER BY]] → ordenamiento del resultado
> - [[LIMIT]] → límite de filas devueltas
> 
> > El orden de escritura de una consulta SQL no coincide necesariamente con el orden lógico de ejecución.

---

### SELECT con alias

```
SELECT nombre AS empleadoFROM empleados;
```

---

### SELECT con expresión

```
SELECT salario * 12 AS salario_anualFROM empleados;
```
#BasesdeDatos