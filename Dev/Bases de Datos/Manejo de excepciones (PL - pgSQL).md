---
tags:
  - DB
  - DBI2doparcial
---

PostgreSQL permite manejar errores dentro de las funciones mediante la instrucción `RAISE`.


### Sintaxis

```sql
RAISE nivel 'mensaje';
```

> [!example]
> Ejemplos:
> ```sql
> RAISE INFO 'Proceso iniciado';
> RAISE WARNING 'Valor sospechoso';
> RAISE EXCEPTION 'Error detectado';
> ```
> 


---

### Niveles de mensajes

|   Nivel   |          Descripción          | ¿Detiene la ejecución? |
| :-------: | :---------------------------: | :--------------------: |
|   DEBUG   |  Información para depuración  |           No           |
|    LOG    | Mensaje para registro interno |           No           |
|   INFO    |      Información general      |           No           |
|  NOTICE   |       Aviso al usuario        |           No           |
|  WARNING  |          Advertencia          |           No           |
| EXCEPTION |        Genera un error        |           Sí           |

> `EXCEPTION` es el único nivel que, por defecto, interrumpe inmediatamente la ejecución de la función.


---

### Configuración de mensajes

El archivo `postgresql.conf` permite definir qué mensajes se muestran o almacenan:

- `log_min_messages` → mensajes que se guardan en el log del servidor.
- `client_min_messages` → mensajes que se envían al cliente.


### Ejemplo

```sql
CREATE OR REPLACE FUNCTION dividir(a INT, b INT)
RETURNS INT
AS $$
BEGIN
   IF b = 0 THEN
      RAISE EXCEPTION 'No se puede dividir por cero';
   END IF;

   RETURN a / b;
END;
$$ LANGUAGE plpgsql;
```

#### Explicación

- `IF` → evalúa una condición.
- `RAISE EXCEPTION` → genera un error.
- `RETURN` → devuelve el resultado de la función.

Si `b` vale `0`, PostgreSQL genera un error y la función se detiene inmediatamente.


---

### Ejemplo de ejecución

```sql
SELECT dividir(10,0);
```

Resultado:
```text
ERROR: No se puede dividir por cero
```

La sentencia `RETURN a / b;` nunca llega a ejecutarse.

---


#BasesdeDatos