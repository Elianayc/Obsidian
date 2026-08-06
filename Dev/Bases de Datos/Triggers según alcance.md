---
tags:
  - DB
  - DBI2doparcial
---

## FOR EACH ROW
La función se ejecuta una vez por cada fila afectada.

Si un `UPDATE` modifica 100 registros:
```sql
UPDATE empleados
SET salario = salario * 1.1;
```

la función trigger se ejecutará 100 veces.
```sql
FOR EACH ROW
```

---

## FOR EACH STATEMENT

La función se ejecuta una sola vez por sentencia SQL, independientemente de cuántas filas afecte.

Si el mismo `UPDATE` modifica 100 registros, el trigger se ejecutará una sola vez.

```sql
FOR EACH STATEMENT
```

#BasesdeDatos