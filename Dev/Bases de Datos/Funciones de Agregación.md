---
tags:
  - 
  
---
Las **funciones de agregado** realizan cálculos sobre **un conjunto de filas** y devuelven **un único valor**.

Se usan generalmente junto con **GROUP BY** dentro de una consulta **SELECT**.

Son **deterministas** → siempre devuelven el mismo resultado para el mismo conjunto de datos.

Permiten obtener **estadísticas** sobre los datos.

---

## Funciones más comunes


### COUNT()
- Cuenta la cantidad de filas o valores no nulos en una columna.

```sql
SELECT 
	COUNT(*) 
FROM 
	pedidos;
```

##### Resultado:  
Devuelve la cantidad total de pedidos.

---

### COUNT DISTINCT
Cuenta valores únicos.

```SQL
SELECT COUNT(DISTINCT id_departamento)
FROM empleados;
```


---

### SUM()
Suma todos los valores de una columna numérica.

```sql
SELECT 
	SUM(monto) 
FROM 
	pedidos;
```

##### Resultado:  
Devuelve el total de dinero vendido.

---

### AVG()
Calcula el promedio de una columna numérica.

```sql
SELECT 
	AVG(monto) 
FROM 
	pedidos;
```

##### Resultado:  
Devuelve el promedio de los montos de pedidos.

---

### MIN()
Devuelve el valor mínimo de una columna.

```sql
SELECT 
	MIN(monto) 
FROM 
	pedidos;
```

##### Resultado:  
Devuelve el pedido con menor monto.

---

### MAX()
Devuelve el valor máximo de una columna.

```SQL
SELECT 
	MAX(monto) 
FROM 
	pedidos;
```

##### Resultado:  
Devuelve el pedido con mayor monto.

---

## Otras funciones de agregación

Además de las funciones de agregación principales, **MySQL** ofrece otras funciones útiles para reportes y análisis estadístico.

|                      Función                       |                                                                                                 Qué hace                                                                                                 |                Ejemplo                |
| :------------------------------------------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :-----------------------------------: |
| `GROUP_CONCAT(col [ORDER BY ...] [SEPARATOR 'x'])` |                                          Concatena en una sola cadena todos los valores de un grupo. El separador es configurable y, por defecto, es una coma.                                           | `GROUP_CONCAT(nombre SEPARATOR ', ')` |
|          `STDDEV_POP()` / `STDDEV_SAMP()`          |                  Calculan la **desviación estándar poblacional / muestral**, que mide qué tan dispersos están los valores respecto del promedio. `STDDEV()` es alias de `STDDEV_POP()`.                  |         `STDDEV_POP(sueldo)`          |
|             `VAR_POP()` / `VAR_SAMP()`             |                              Calculan la **varianza poblacional / muestral**, que corresponde al cuadrado de la desviación estándar. `VARIANCE()` es alias de `VAR_POP()`.                               |           `VAR_POP(sueldo)`           |
|       `BIT_AND()` / `BIT_OR()` / `BIT_XOR()`       |         Aplican una operación bit a bit (**AND, OR, XOR**) entre todos los valores enteros de un grupo. Son poco frecuentes, pero pueden ser útiles para combinar columnas de flags o permisos.          |          `BIT_AND(permisos)`          |
|                `JSON_ARRAYAGG(col)`                |                                                Agrupa los valores de una columna en un único **array JSON**. Anticipa el trabajo con JSON de la Unidad 3.                                                |        `JSON_ARRAYAGG(nombre)`        |
|           `JSON_OBJECTAGG(clave, valor)`           |                                                Agrupa pares **clave-valor** en un único objeto JSON. También anticipa el trabajo con JSON de la Unidad 3.                                                |     `JSON_OBJECTAGG(id, nombre)`      |
|        `ANY_VALUE(columna)`<br><br><br><br>        | Indica al motor que devuelva un valor cualquiera de una columna no agregada ni agrupada, evitando el error de `ONLY_FULL_GROUP_BY` cuando se sabe que esa columna depende funcionalmente del `GROUP BY`. |          `ANY_VALUE(nombre)`          |

---
