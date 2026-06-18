---
tags:
  - DBI1erparcial
  - DB
---

> [!Sintaxis]
> 
> ```sql
>  CREATE [ UNIQUE ] INDEX [ CONCURRENTLY ] [ nombre ] 
> 	ON tabla 
> 	[ USING método ]
> 	( 
> 		{ columna | ( expresión ) } 
> 		[ ASC | DESC ] 
> 		[ NULLS { FIRST | LAST } ] 
> 		[, ...] 
> 	)
> 	[ WHERE predicado ]
> ```
> 

> [!example]
> 
> ```sql
> CREATE UNIQUE INDEX CONCURRENTLY idx_clientes_email
> 	ON clientes
> 	USING btree
> 	( 
> 		email 
> 		ASC 
> 		NULLS LAST 
> 	)
> 	WHERE activo = TRUE;
> ```
> 


####  Desglose de parámetros

- **`unique`:** impide que la tabla tenga filas con valores duplicados.

- **`concurrently`:** crea el índice sin bloquear las escrituras de la tabla.

- **`nombre`:** el nombre que le asignás al índice.

- **`tabla`:** la tabla sobre la cual vas a trabajar.

- **`using método`:** el tipo de estructura de datos para el índice.
    - _opciones:_ `btree`, `hash`, `gin`, `gist`, `spgist`, `brin`.
    - _nota:_ si no lo especificás, por defecto se usa `btree`.

- **`columna / expresión`:**
  - _columna:_ el nombre de la columna física.
  - _expresión:_ una función o cálculo (índice funcional).

- **`asc / desc`:** orden ascendente o descendente.

- **`nulls first / last`:** define si los valores nulos van al principio o al final.

- **`where predicado`:** condición para crear un índice parcial (solo indexa las filas que cumplen la condición).

Por defecto, PostgreSQL crea índices **B-Tree**, ya que sirven para la mayoría de los casos.

---

## Mantenimiento de índices
Cuando se crean índices sobre tablas con datos (y periódicamente), se recomienda ejecutar:

```sql
vacuum full analyze nombre_tabla;
```

###### Este comando:

- **reorganiza la tabla:** recrea físicamente la tabla en el disco, eliminando la fragmentación.
    
- **limpia espacio:** libera el espacio en disco ocupado por filas muertas (datos eliminados o modificados) y se lo devuelve al sistema operativo.
    
- **actualiza estadísticas del optimizador:** recolecta información fresca sobre la distribución de los datos para que el motor de la base de datos elija los mejores índices al ejecutar consultas.
    
- **mejora el rendimiento:** optimiza de forma directa la velocidad de las consultas y la eficiencia de los índices.

>[!warning] **Nota importante** 
>`vacuum full` bloquea la tabla por completo (no se pueden hacer lecturas ni escrituras mientras corre). 
>
>En entornos en vivo con mucho tráfico, se suele usar la alternativa `vacuum analyze` (sin el `full`), que es más lenta pero no bloquea la tabla, o herramientas externas como `pg_repack`.

---
