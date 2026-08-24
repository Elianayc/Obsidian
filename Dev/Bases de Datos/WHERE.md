---
tags:
  - 
  
---
Se utiliza para **filtrar registros** antes de mostrar resultados.

```SQL
SELECT * FROM pedidos WHERE monto > 2000;
```

##### Resultado:  
Devuelve solo los pedidos con monto mayor a 2000.

---

## Operadores de Filtrado

Los operadores de filtrado se utilizan dentro de consultas **SELECT** para restringir los resultados según condiciones específicas.
No son cláusulas completas, sino expresiones que se combinan con `WHERE` u otras condiciones.

### LIKE

Se utiliza para buscar patrones dentro de textos.

Permite usar comodines como:
- `%` para cualquier cantidad de caracteres
- `_` para un solo carácter

```sql
SELECT * FROM empleados WHERE nombre LIKE 'M%';
```

```SQL
WHERE nombre LIKE 'M%';
```

---

### BETWEEN

Se utiliza para filtrar valores dentro de un rango.
Incluye los valores límite.

```sql
SELECT * FROM empleados WHERE salario BETWEEN 50000 AND 60000;
```

---

### IN

Se utiliza para comparar un valor contra una lista de posibles valores.

```sql
SELECT * FROM empleados WHERE id_departamento IN (1, 2, 3);
```


----

### NOT IN

Se utiliza para excluir valores de una lista.

```sql
SELECT * FROM empleados 
WHERE id_departamento 
NOT IN (1, 2);
```

---


