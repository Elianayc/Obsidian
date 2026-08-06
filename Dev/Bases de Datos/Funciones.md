---
tags:
---
Las funciones encapsulan lógica reutilizable dentro de la base de datos. 

Se invocan para obtener un resultado y permiten centralizar comportamiento para que otras aplicaciones lo reutilicen de forma consistente.

#### Características principales
- Pueden recibir parámetros de **entrada**.

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

[[Tipos de funciones según lenguaje]]
[[Manejo de excepciones (PL - pgSQL)]]
[[Triggers]]
#BasesdeDatos