---
tags:
  - 
  
---
Los tipos de datos determinan qué clase de información puede almacenarse en una columna de una tabla.

---

## Tipos de datos generales

### Numéricos
Se utilizan para almacenar valores numéricos enteros o con decimales.

|           Tipo            |                    Descripción                    |      Ejemplo       |
| :-----------------------: | :-----------------------------------------------: | :----------------: |
|        **Enteros**        |               Números sin decimales               |       `INT`        |
|   **Decimales exactos**   |         Números con precisión determinada         |   `DECIMAL(8,2)`   |
| **Decimales aproximados** | Números decimales almacenados de forma aproximada | `DOUBLE` / `FLOAT` |

---

### Texto
Se utilizan para almacenar cadenas de caracteres.

|      Tipo      |    Descripción    |       Ejemplo        |
| :------------: | :---------------: | :------------------: |
|  **CHAR(n)**   |   Longitud fija   |   `codigo CHAR(5)`   |
| **VARCHAR(n)** | Longitud variable | `nombre VARCHAR(50)` |
|    **TEXT**    |    Texto largo    |  `descripcion TEXT`  |

---

### Fecha y hora
Permiten almacenar fechas y horarios.

|       Tipo       |       Descripción        |               Ejemplo               |
| :--------------: | :----------------------: | :---------------------------------: |
|     **DATE**     |          Fecha           |            `fecha DATE`             |
| **Fecha y hora** | Fecha junto con una hora | `fecha_hora DATETIME` / `TIMESTAMP` |

---

### Booleanos
Permiten representar valores de verdadero o falso.

|Tipo|Descripción|Ejemplo|
|---|---|---|
|**BOOLEAN**|Verdadero / Falso|`activo BOOLEAN`|

---

## PostgreSQL
PostgreSQL agrega algunos tipos específicos y variantes:

|      Tipo       |          Descripción           |      Ejemplo       |
| :-------------: | :----------------------------: | :----------------: |
|  **SMALLINT**   |        Enteros pequeños        |  `edad SMALLINT`   |
|   **INTEGER**   |            Enteros             |  `stock INTEGER`   |
|   **BIGINT**    |        Enteros grandes         | `poblacion BIGINT` |
| **SMALLSERIAL** | Entero autoincremental pequeño |  `id SMALLSERIAL`  |
|   **SERIAL**    |     Entero autoincremental     |    `id SERIAL`     |
|  **BIGSERIAL**  | Entero autoincremental grande  |   `id BIGSERIAL`   |
|  **TIMESTAMP**  |          Fecha y hora          | `creado TIMESTAMP` |

### Autoincremento
PostgreSQL puede utilizar `SERIAL`, `SMALLSERIAL` o `BIGSERIAL` para generar automáticamente valores consecutivos.

```sql
id SERIAL
```


---

## MySQL
MySQL agrega algunos tipos y características específicas:

|     Tipo     |   Descripción    |      Ejemplo      |
| :----------: | :--------------: | :---------------: |
| **TINYINT**  | Enteros pequeños | `activo TINYINT`  |
| **DATETIME** |   Fecha y hora   | `creado DATETIME` |

### Autoincremento
En MySQL se utiliza **`AUTO_INCREMENT`** junto con un tipo entero.

```sql
id INT AUTO_INCREMENT
```

---

