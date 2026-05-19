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


> [!example]
> ```sql
> CREATE FUNCTION sumar(a INT, b INT)
> RETURNS INT
> LANGUAGE plpgsql
> AS $$
> BEGIN
>    RETURN a + b;
> END;
> $$;
> ```
>
> - `a` y `b` → parámetros de entrada
> - `RETURNS INT` → devuelve un número
> - `plpgsql` → lenguaje usado
> - `RETURN a + b` → resultado de la función





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

---

