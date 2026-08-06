---
tags:
  - 
  
---
Cuando se diseña y desarrolla una aplicación, el objetivo principal es proveer una interfaz amigable para el usuario final. Los requerimientos de la aplicación definen restricciones que determinan el tipo de base de datos a utilizar.

A nivel funcional, los tipos de bases de datos se clasifican en:
- [[OLTP]]
- [[OLAP]]
- [[Híbridas]]


#### Comparación OLTP vs OLAP

|         Característica         |                     OLTP                      |                   OLAP                    |
| :----------------------------: | :-------------------------------------------: | :---------------------------------------: |
|      **Fuente de datos**       | Datos operacionales (aplicaciones de usuario) | Datos consolidados (varios sistemas OLTP) |
|   **Propósito de los datos**   |              Operación y control              |       Análisis y toma de decisiones       |
|  **Significado de los datos**  |           Estado actual del negocio           |       Visión histórica del negocio        |
|   **Actualización de datos**   |          Frecuente y en tiempo real           |           Periódica y por lotes           |
|         **Consultas**          |               Simples y rápidas               |           Complejas y agregadas           |
| **Velocidad de procesamiento** |                  Muy rápida                   |         Variable, puede ser lenta         |
|       **Almacenamiento**       |                Bajo a moderado                |        Alto (histórico + índices)         |
| **Diseño de la base de datos** |                  Normalizado                  |              Desnormalizado               |
|   **Backup y recuperación**    |              Crítico y frecuente              |              Menos estricto               |

No existe un único sistema ideal. La elección depende de las necesidades de procesamiento y requerimientos de análisis y toma de decisiones.

#BasesdeDatos