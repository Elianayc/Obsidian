---
tags:
  - DB
  - DBI2doparcial
---
### Funciones en PostgreSQL
Las funciones encapsulan lógica reutilizable dentro de la base de datos. Se invocan para obtener un resultado y permiten centralizar comportamiento para que otras aplicaciones lo reutilicen de forma consistente.

#### Características principales

- Pueden recibir parámetros de entrada.
- Siempre devuelven **un único resultado**.
- El resultado puede ser:
    - un tipo de dato simple (`INT`, `TEXT`, etc.)
    - un **registro** → lo que permite devolver una **tabla completa**.
- PostgreSQL permite escribir funciones en varios lenguajes: **SQL, PL/pgSQL, C y Python**.
- **PL/pgSQL** es el lenguaje procedural nativo y permite agregar lógica de programación.

---

### Qué se define al crear una función
Cuando se crea una función hay que especificar tres cosas: **parámetros, retorno y lenguaje**.

**1) Parámetros**  
Cada parámetro tiene un modo:
- `IN` → entra un valor (por defecto).
- `OUT` → valor de salida.
- `INOUT` → entra y sale modificado.

El tipo de dato puede ser:
- un tipo común (`INT`, `TEXT`, etc.)
- el tipo de una columna existente → `tabla.columna%TYPE`.

**2) Tipo de retorno**
- Valor simple → `RETURNS INTEGER`
- Tabla → `RETURNS TABLE(columna tipo, ...)`

**3) Lenguaje**  
Se indica con `LANGUAGE`: `SQL`, `PLpgSQL` o `PLPythonu`.

> [!example]
> ```sql
> CREATE OR REPLACE FUNCTION nombre(
> 	[<modo>] <arg1> <tipo>,
> 	...
> 	[<modo>] <argN><tipo>
> ) 
> RETURNS <tipo_retorno> 
> AS $$
> DECLARE 
> 	<nombre_var> <tipo_var>
> BEGIN
>   -- lógica de la función
> END;
> $$ LANGUAGE <lenguaje>;
> ```


---

Te lo ordeno con el formato que venimos usando ✨ y seguimos desde donde quedó (excepciones + triggers).

---

### Tipos de funciones según lenguaje

El tipo de función depende del **lenguaje utilizado para implementarla**.
- **SQL**
    - Solo permite ejecutar sentencias SQL.
    - Útil para operaciones simples.

- **PL/pgSQL**
    - Permite lógica compleja.
    - Soporta:
        - condicionales (`IF`)
        - bucles (`LOOP`, `WHILE`)
        - variables
        - manejo de errores

- **PL/Python**
    - Permite escribir funciones usando Python.
    - Útil cuando se necesita mayor potencia de cálculo o librerías externas.
    

---

### Manejo de excepciones (PL/pgSQL)
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

---

## Triggers

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

