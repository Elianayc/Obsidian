Las **funciones de cadena** permiten combinar, extraer, transformar y medir textos directamente en una consulta.

|                Función                |                                 Uso                                 |               Ejemplo                |
| :-----------------------------------: | :-----------------------------------------------------------------: | :----------------------------------: |
|          `CONCAT(a, b, ...)`          |                      Concatena varios valores.                      |   `CONCAT(nombre, ' ', apellido)`    |
|      `CONCAT_WS(sep, a, b, ...)`      |            Concatena valores intercalando un separador.             | `CONCAT_WS(' - ', nombre, apellido)` |
|  `SUBSTRING(cadena, inicio, largo)`   |             Extrae una porción de una cadena de texto.              |      `SUBSTRING(nombre, 1, 3)`       |
|         `UPPER()` / `LOWER()`         |            Convierte el texto a mayúsculas / minúsculas.            |           `UPPER(nombre)`            |
|   `TRIM()` / `LTRIM()` / `RTRIM()`    | Elimina espacios en blanco al inicio, al final o en ambos extremos. |            `TRIM(nombre)`            |
| `REPLACE(cadena, buscado, reemplazo)` |        Reemplaza todas las apariciones de un texto por otro.        |  `REPLACE(nombre, 'Juan', 'Pedro')`  |
|              `LENGTH()`               |           Cuenta la cantidad de **bytes** de una cadena.            |           `LENGTH(nombre)`           |
|            `CHAR_LENGTH()`            |         Cuenta la cantidad de **caracteres** de una cadena.         |        `CHAR_LENGTH(nombre)`         |

---

### LENGTH() vs. CHAR_LENGTH()

`LENGTH()` cuenta **bytes**, mientras que `CHAR_LENGTH()` cuenta **caracteres**.

Con `utf8mb4`, ambas pueden devolver valores diferentes porque algunos caracteres ocupan más de un byte.

---

