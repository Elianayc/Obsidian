---
tags:
---
Las **funciones** encapsulan lógica reutilizable dentro de la base de datos.

Se invocan para obtener un resultado y permiten centralizar comportamiento para que otras aplicaciones puedan reutilizarlo de forma consistente.

> Este apartado se refiere a **funciones definidas por el usuario**, creadas mediante `CREATE FUNCTION`. No confundir con las Funciones Incorporadas, que son funciones que el motor ya proporciona.

#### Características principales

- Pueden recibir parámetros de **entrada**.
    
- Devuelven un **resultado**.
    
- El resultado puede ser:
    
    - un tipo de dato simple (`INT`, `TEXT`, etc.)
        
    - un **registro**
        
    - una **tabla completa**
        
- PostgreSQL permite escribir funciones en varios lenguajes: **SQL, PL/pgSQL, C y Python**.
    
- **PL/pgSQL** es el lenguaje procedural nativo de PostgreSQL y permite agregar lógica de programación.
    

---

### Qué se define al crear una función

Cuando se crea una función se especifican principalmente **parámetros, retorno y lenguaje**.

**1) Parámetros**

Cada parámetro puede tener un modo:

- `IN` → recibe un valor de entrada. Es el modo predeterminado.
    
- `OUT` → define un valor de salida.
    
- `INOUT` → recibe un valor y lo devuelve modificado.
    

El tipo de dato puede ser:

- un tipo común (`INT`, `TEXT`, etc.)
    
- el tipo de una columna existente → `tabla.columna%TYPE`
    

**2) Tipo de retorno**

La función debe indicar qué tipo de resultado devuelve:

- Valor simple → `RETURNS INTEGER`
    
- Tabla → `RETURNS TABLE(columna tipo, ...)`
    

**3) Lenguaje**

Se indica mediante `LANGUAGE`.

Algunos lenguajes disponibles son:

- `SQL`
    
- `PLpgSQL`
    
- `PLPythonu`
    

> [!example]
> 
> ```sql
> CREATE OR REPLACE FUNCTION nombre(
> 	[<modo>] <arg1> <tipo>,
> 	...
> 	[<modo>] <argN> <tipo>
> ) 
> RETURNS <tipo_retorno> 
> AS $$
> DECLARE 
> 	<nombre_var> <tipo_var>;
> BEGIN
> 	-- lógica de la función
> END;
> $$ LANGUAGE <lenguaje>;
> ```

---

- [[Tipos de funciones según lenguaje]]
    
- [[Manejo de excepciones (PL - pgSQL)]]
    
- [[Triggers]]