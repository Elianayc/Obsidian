---
tags:
  - 
  
---
Es el campo (o conjunto de campos) que **identifica de forma única cada registro** dentro de una tabla.

La clave primaria garantiza la **integridad de entidad**: cada fila debe tener un identificador único y no puede ser `NULL`.

---

### Características

- No se puede repetir.
- No puede ser `NULL`.
- Solo puede existir **una clave primaria por tabla**.
- Puede estar formada por una o varias columnas.
    
---

### Clave primaria simple

Está formada por **una sola columna**.

Es el caso más habitual. Muchas tablas utilizan un identificador generado específicamente para identificar cada registro, llamado **surrogate key** (clave subrogada).

**Por ejemplo:**

```sql
idClients INT PRIMARY KEY AUTO_INCREMENT
```

En este caso, `idClients` identifica de manera única a cada cliente.

---

### Clave primaria compuesta

Está formada por **dos o más columnas** que, combinadas, identifican de forma única a cada fila.

Es habitual en **tablas puente** que representan relaciones N:N, donde la combinación de las claves foráneas permite identificar cada registro.

**Por ejemplo, una tabla que relaciona alumnos con cursos:**

| idAlumno | idCurso |
| :------: | :-----: |
|    1     |   10    |
|    1     |   20    |
|    2     |   10    |

La combinación **`idAlumno + idCurso`** funciona como clave primaria:

```sql
PRIMARY KEY (idAlumno, idCurso)
```


---

### Autoincremento vs. UUID

Ambas son estrategias para generar identificadores únicos, pero tienen características y usos diferentes.

|      Criterio       |                    Autoincremento                    |                                                      UUID                                                      |
| :-----------------: | :--------------------------------------------------: | :------------------------------------------------------------------------------------------------------------: |
|     **Tamaño**      |                 Ocupa menos espacio                  |                                               Ocupa más espacio                                                |
|  **Orden físico**   | Los valores son secuenciales, favoreciendo el orden  |                            Los valores son aleatorios y no siguen un orden natural                             |
|   **Generación**    |       Generalmente la realiza la base de datos       |                             Puede generarse en la aplicación o en la base de datos                             |
| **Predictibilidad** |           Es predecible: `1`, `2`, `3`...            |                                             Es difícil de predecir                                             |
| **Escenario ideal** | Aplicaciones donde se busca simplicidad y eficiencia | Sistemas distribuidos o donde se necesita generar identificadores únicos sin depender de una secuencia central |

**Autoincremento:**

```sql
id INT AUTO_INCREMENT PRIMARY KEY
```

**UUID:**

```sql
id CHAR(36) PRIMARY KEY
```


---

