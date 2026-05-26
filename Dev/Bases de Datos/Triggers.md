---
tags:
  - DB
  - DBI2doparcial
---
Un **trigger** (disparador) es un objeto de la base de datos que indica al motor que ejecute automáticamente una función cuando ocurre un determinado evento sobre una tabla o vista.

La función asociada al trigger se ejecuta automáticamente, sin necesidad de ser invocada mediante un `SELECT` o una llamada explícita.

Eventos típicos:
- `INSERT`
- `UPDATE`
- `DELETE`
- `TRUNCATE` (en PostgreSQL)

Se utilizan para:
- auditoría de cambios
- validaciones automáticas
- mantenimiento de consistencia de datos
- generación de registros históricos (logs)
- sincronización de datos relacionados

---

## Cómo funciona un trigger

Un trigger tiene dos componentes:
1. **Función trigger** → contiene la lógica a ejecutar.
2. **Trigger** → define cuándo debe ejecutarse esa función.

> [!example]
> 
> ```sql
> -- 1) Función trigger
> CREATE OR REPLACE FUNCTION avisar_insert()
> RETURNS TRIGGER AS $$
> BEGIN
>    RAISE NOTICE 'Se insertó un registro';
>    RETURN NEW;
> END;
> $$ LANGUAGE plpgsql;
> 
> -- 2) Trigger
> CREATE TRIGGER trigger_insert
> AFTER INSERT ON clientes
> FOR EACH ROW
> EXECUTE FUNCTION avisar_insert();
> ```
> 
> ##### Elementos importantes
>- `RETURNS TRIGGER` Indica que la función será utilizada por un trigger. 
> 	*ver [[Valores de retorno]]*
>  
>- `NEW` Contiene la nueva fila que se está insertando o actualizando.
>- `OLD` Contiene la fila anterior en operaciones de actualización o eliminación.
> 	 *ver [[Variables especiales]]*
>  
>- `FOR EACH ROW` Ejecuta la función una vez por cada fila afectada.
>- `EXECUTE FUNCTION` Indica qué función trigger debe ejecutarse.


---
## Resumen rápido

|         Tipo         |     Cuándo se ejecuta     |
| :------------------: | :-----------------------: |
|       `BEFORE`       |   Antes de la operación   |
|       `AFTER`        |  Después de la operación  |
|    `FOR EACH ROW`    | Una vez por fila afectada |
| `FOR EACH STATEMENT` | Una vez por sentencia SQL |

**El trigger no contiene la lógica; la lógica está en la función trigger. El trigger solamente define cuándo debe ejecutarse esa función.** 

[[Triggers según momento de ejecución]]
[[Triggers según alcance]]

---

