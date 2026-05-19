PostgreSQL permite manejar errores dentro de las funciones.

**Niveles de mensajes**
- `DEBUG`
- `LOG`
- `INFO`
- `NOTICE`
- `WARNING`
- `EXCEPTION`  (corta la ejecución)


El archivo `postgresql.conf` permite definir qué mensajes se guardan:

- `log_min_messages` → mensajes que van al log
- `client_min_messages` → mensajes que ve el cliente

> [!example]
> 
> ```sql
> CREATE OR REPLACE FUNCTION dividir(a INT, b INT)
> RETURNS INT
> AS $$
> BEGIN
>    IF b = 0 THEN
>       RAISE EXCEPTION 'No se puede dividir por cero';
>    END IF;
> 
>    RETURN a / b;
> END;
> $$ LANGUAGE plpgsql;
> ```
> 
> - `IF` → valida condición
>     
> - `RAISE EXCEPTION` → genera error
>     
> - Si ocurre el error, la función se detiene
>     
