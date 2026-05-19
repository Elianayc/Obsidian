Un **trigger** es una indicación al motor de base de datos para que ejecute automáticamente una función cuando ocurre un evento.

Es decir: la función se ejecuta **sola** sin que nadie la llame.

Eventos típicos:
- `INSERT`
- `UPDATE`
- `DELETE`

Se usan para:
- auditoría
- validaciones automáticas
- mantener consistencia de datos

---

### Cómo funciona un trigger

Un trigger tiene dos partes:
1. **Función trigger** → contiene la lógica
2. **Trigger** → indica cuándo ejecutarla

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
> - `RETURNS TRIGGER` → función especial para triggers
>     
> - `NEW` → registro recién insertado
>     
> - `AFTER INSERT` → se ejecuta después de insertar
>     
> - `FOR EACH ROW` → se ejecuta por cada fila
>     

