---
tags:
  - DB
  - DBI2doparcial
---
Un **trigger** (disparador) es un objeto de la base de datos que permite ejecutar automáticamente una función cuando ocurre un determinado evento sobre una tabla o vista.

Eventos típicos:
- `INSERT`
- `UPDATE`
- `DELETE`
- `TRUNCATE` (PostgreSQL)

Usos frecuentes:
- Auditoría de cambios.
- Validaciones automáticas.
- Mantenimiento de consistencia de datos.
- Generación de registros históricos (logs).
- Sincronización de datos relacionados.

---

## Cómo funciona un trigger
Todo trigger está compuesto por:
1. **Función trigger** → contiene la lógica a ejecutar
2. **Trigger** → indica cuándo y sobre qué objeto debe ejecutarse esa función.

> **La lógica está en la función; el trigger solamente define las condiciones de ejecución.**

>En PostgreSQL, cuando existen varios triggers para la misma tabla, el mismo evento y el mismo momento (`BEFORE` o `AFTER`), se ejecutan **en orden alfabético según el nombre del trigger**.

---

## Sintaxis general

> [!example]
> 
> ```sql
> CREATE [ CONSTRAINT ] TRIGGER nombre_trigger
> 
>     Momento:
>         BEFORE
>         AFTER
>         INSTEAD OF
> 
>     Evento:
>         INSERT
>         UPDATE
>         DELETE
>         TRUNCATE
>         [ OR otro_evento ]
> 
> ON tabla
> 
>     Opcional:
>         FROM referenced_table_name
> 
>     Opcional:
>         DEFERRABLE / NOT DEFERRABLE
> 
>     Opcional:
>         REFERENCING OLD/NEW
> 
>     Opcional:
>         FOR EACH ROW
>         FOR EACH STATEMENT
> 
>     Opcional:
>         WHEN ( condicion )
> 
> EXECUTE PROCEDURE nombre_funcion(argumentos);
> ```
> 
> ### Componentes principales
> 
> - **BEFORE** → ejecuta la función antes del evento.
>     
> - **AFTER** → ejecuta la función después del evento.
>     
> - **INSTEAD OF** → reemplaza la operación (principalmente en vistas).
>     
> - **FOR EACH ROW** → una ejecución por cada fila afectada.
>     
> - **FOR EACH STATEMENT** → una ejecución por sentencia SQL.
>     
> - **WHEN** → condición opcional de ejecución.
>     
> 
> _Ver [[Variables especiales]]_  
> _Ver [[Valores de retorno]]_

---

## Ejemplo

> [!example]
> 
> ```sql
> -- Función trigger
> CREATE OR REPLACE FUNCTION avisar_insert()
> RETURNS TRIGGER AS $$
> BEGIN
>    RAISE NOTICE 'Se insertó un registro';
>    RETURN NEW;
> END;
> $$ LANGUAGE plpgsql;
> 
> -- Trigger
> CREATE TRIGGER trigger_insert
> AFTER INSERT ON clientes
> FOR EACH ROW
> EXECUTE FUNCTION avisar_insert();
> ```
> 
> ### Elementos importantes
> 
> - `RETURNS TRIGGER` → indica que la función será utilizada por un trigger.
>     
> - `NEW` → contiene la nueva fila en operaciones `INSERT` y `UPDATE`.
>     
> - `OLD` → contiene la fila anterior en operaciones `UPDATE` y `DELETE`.
>     

---

## Resumen rápido

|Tipo|Cuándo se ejecuta|
|---|---|
|`BEFORE`|Antes de la operación|
|`AFTER`|Después de la operación|
|`FOR EACH ROW`|Una vez por fila afectada|
|`FOR EACH STATEMENT`|Una vez por sentencia SQL|

**Recordar:** la lógica se escribe dentro de la función trigger; el trigger únicamente determina cuándo debe ejecutarse.

---

[[Triggers según momento de ejecución]]  
[[Triggers según alcance]]

---

#BasesdeDatos