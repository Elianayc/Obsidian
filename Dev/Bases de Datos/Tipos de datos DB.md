---
tags:
  - 
  
---

Los tipos de datos determinan qué clase de información puede almacenarse en una columna de una tabla.

---

## Numéricos
Se utilizan para almacenar valores numéricos enteros o con decimales.

|       Tipo        |          Descripción           |             Ejemplo             |
| :---------------: | :----------------------------: | :-----------------------------: |
|   **SMALLINT**    |        Enteros pequeños        |      `edad SMALLINT = 25`       |
| **INT / INTEGER** |            Enteros             |        `stock INT = 50`         |
|    **BIGINT**     |        Enteros grandes         |       `poblacion BIGINT`        |
|  **SMALLSERIAL**  | Entero autoincremental pequeño |        `id SMALLSERIAL`         |
|    **SERIAL**     |     Entero autoincremental     |           `id SERIAL`           |
|   **BIGSERIAL**   | Entero autoincremental grande  |         `id BIGSERIAL`          |
| **DECIMAL(p, s)** |       Decimales exactos        | `precio DECIMAL(8,2) = 1999.99` |
|    **DOUBLE**     |     Decimales aproximados      |     `altura DOUBLE = 1.732`     |
|    **TINYINT**    |        Enteros pequeños        |        `activo TINYINT`         |

---

## Texto
Se utilizan para almacenar cadenas de caracteres.

|Tipo|Descripción|Ejemplo|
|---|---|---|
|**CHAR(n)**|Longitud fija|`codigo CHAR(5) = 'AB123'`|
|**VARCHAR(n)**|Longitud variable|`nombre VARCHAR(50)`|
|**TEXT**|Texto sin límite práctico|`descripcion TEXT`|

---

## Fecha y hora
Permiten almacenar fechas o fechas con hora.

|Tipo|Descripción|Ejemplo|
|---|---|---|
|**DATE**|Fecha|`fecha DATE = '2025-08-13'`|
|**TIMESTAMP**|Fecha y hora|`creado TIMESTAMP`|
|**DATETIME**|Fecha y hora|`creado DATETIME`|

---

## Booleanos

|Tipo|Descripción|Ejemplo|
|---|---|---|
|**BOOLEAN**|Verdadero / Falso|`activo BOOLEAN = TRUE`|

---

> **Nota:** Algunos tipos corresponden específicamente a PostgreSQL, como `SERIAL`, `SMALLSERIAL` y `BIGSERIAL`. 
> 
> En MySQL se utilizan otras alternativas para el autoincremento.