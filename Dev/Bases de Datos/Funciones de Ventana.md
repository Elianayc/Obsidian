Una **función de ventana** calcula un valor agregado o de ranking para cada fila, pero **sin colapsar el resultado**.

A diferencia de `GROUP BY`, la consulta conserva todas las filas originales.

---

### Sintaxis general

```sql
funcion() OVER (
	PARTITION BY columna_de_agrupamiento
	ORDER BY columna_de_orden
	[ROWS/RANGE BETWEEN ... AND ...]
)
```

- `PARTITION BY` → define subgrupos dentro de los cuales se reinicia el cálculo. Funciona de forma similar a un `GROUP BY`, pero **sin colapsar las filas**.
    
- `ORDER BY` → define el orden en que se procesan las filas dentro de cada partición. Es fundamental para rankings y totales acumulados.
    
- `ROWS` / `RANGE` → delimitan qué filas participan en el cálculo de cada fila.
    
---

### Principales funciones

|       Función        |                                                                Qué devuelve                                                                |                   Ejemplo                   |
| :------------------: | :----------------------------------------------------------------------------------------------------------------------------------------: | :-----------------------------------------: |
|    `ROW_NUMBER()`    |                       Número correlativo único por fila dentro de cada partición: `1, 2, 3, ...`. No admite empates.                       | `ROW_NUMBER() OVER (ORDER BY sueldo DESC)`  |
|       `RANK()`       |           Ranking que admite empates. Si dos filas empatan, ambas reciben la misma posición y se salta la siguiente: `1, 1, 3`.            |    `RANK() OVER (ORDER BY sueldo DESC)`     |
|    `DENSE_RANK()`    |                                    Igual que `RANK()`, pero sin saltos después de un empate: `1, 1, 2`.                                    | `DENSE_RANK() OVER (ORDER BY sueldo DESC)`  |
|  `SUM() OVER (...)`  |                             Calcula una suma por partición o un total acumulado, manteniendo todas las filas.                              | `SUM(monto) OVER (PARTITION BY id_cliente)` |
|  `AVG() OVER (...)`  |                                        Calcula un promedio por partición o según el orden definido.                                        | `AVG(monto) OVER (PARTITION BY id_cliente)` |
| `COUNT() OVER (...)` |                                   Cuenta filas dentro de una partición sin agruparlas en una sola fila.                                    |  `COUNT(*) OVER (PARTITION BY id_cliente)`  |
|  `LAG()` / `LEAD()`  | Devuelven el valor de una columna en la fila anterior / siguiente dentro de la partición. Son útiles para comparar valores entre períodos. |     `LAG(monto) OVER (ORDER BY fecha)`      |

---

### Diferencia con GROUP BY

|                  `GROUP BY`                   |         Función de ventana          |
| :-------------------------------------------: | :---------------------------------: |
|                 Agrupa filas                  |      Mantiene todas las filas       |
| Reduce la cantidad de registros del resultado |  Conserva la cantidad de registros  |
|        Calcula un resultado por grupo         | Calcula un resultado para cada fila |

---
