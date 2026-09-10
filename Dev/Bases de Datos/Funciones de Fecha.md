MySQL ofrece funciones para trabajar con valores `DATE`, `DATETIME` y `TIMESTAMP`.

|                 Función                 |                                                  Uso                                                   |                      Ejemplo                       |
| :-------------------------------------: | :----------------------------------------------------------------------------------------------------: | :------------------------------------------------: |
|                 `NOW()`                 |                              Obtiene la fecha y hora actual del servidor.                              |                      `NOW()`                       |
|               `CURDATE()`               |                                   Obtiene solamente la fecha actual.                                   |                    `CURDATE()`                     |
|  `DATE_ADD(fecha, INTERVAL n unidad)`   |                                Suma un intervalo de tiempo a una fecha.                                |         `DATE_ADD(fecha, INTERVAL 7 DAY)`          |
|  `DATE_SUB(fecha, INTERVAL n unidad)`   |                               Resta un intervalo de tiempo a una fecha.                                |        `DATE_SUB(fecha, INTERVAL 1 MONTH)`         |
|       `DATEDIFF(fecha1, fecha2)`        |                       Calcula la diferencia entre dos fechas expresada en días.                        |        `DATEDIFF(fecha_fin, fecha_inicio)`         |
| `TIMESTAMPDIFF(unidad, fecha1, fecha2)` | Calcula la diferencia entre dos fechas expresada en la unidad indicada (`DAY`, `MONTH`, `YEAR`, etc.). | `TIMESTAMPDIFF(YEAR, fecha_nacimiento, CURDATE())` |
|      `DATE_FORMAT(fecha, formato)`      |                                 Da formato personalizado a una fecha.                                  |           `DATE_FORMAT(fecha, '%Y-%m')`            |
|     `YEAR()` / `MONTH()` / `DAY()`      |                          Extraen directamente el año, mes o día de una fecha.                          |                   `YEAR(fecha)`                    |

---

