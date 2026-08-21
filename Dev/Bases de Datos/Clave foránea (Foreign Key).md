---
tags:
  - 
  
---
Es un campo que **referencia la clave primaria de otra tabla**, creando una relación entre ellas.

Garantiza la **integridad referencial**, es decir, que el valor de la clave foránea corresponda a un registro existente en la tabla referenciada.

---

### Características

- Puede repetirse.
- Puede ser `NULL` si la relación no es obligatoria.
- Debe coincidir con un valor existente en la tabla referenciada, salvo que sea `NULL`.
- Una tabla puede tener varias claves foráneas.
- Un campo puede formar parte de una clave foránea.
    
---

### Ejemplo

`pais_id` en la tabla `Provincias` referencia a `idPais` en la tabla `Paises`.

```sql
Provincias
-----------
idProvincia
nombre
pais_id  →  Paises.idPais
```

---

## Integridad referencial

La integridad referencial garantiza que las relaciones entre las tablas sean válidas.

Cuando se **elimina o actualiza** un registro de la tabla referenciada, se debe definir qué ocurre con los registros que dependen de él.

Esto se configura mediante:

- `ON DELETE`: define qué ocurre cuando se elimina el registro referenciado.
- `ON UPDATE`: define qué ocurre cuando se modifica el valor referenciado.
    

### Acciones

|Acción|Comportamiento|
|---|---|
|**RESTRICT**|Impide eliminar o actualizar el registro si existen registros relacionados.|
|**CASCADE**|Elimina o actualiza automáticamente los registros relacionados.|
|**SET NULL**|Establece la clave foránea en `NULL`.|
|**NO ACTION**|No realiza ninguna acción automática y rechaza la operación si se viola la integridad referencial.|

---

### Ejemplo

```sql
FOREIGN KEY (pais_id)
REFERENCES Paises(idPais)
ON DELETE RESTRICT
ON UPDATE CASCADE
```

En este caso:

- Si se intenta eliminar un país que tiene provincias relacionadas, `RESTRICT` lo impide.
    
- Si cambia el identificador del país, `CASCADE` actualiza automáticamente el `pais_id` de las provincias relacionadas.
    
---
