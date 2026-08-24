---
tags:
  - 
  
---
La cláusula **LIMIT** se utiliza en SQL para **restringir la cantidad de filas que devuelve una consulta**.

Se usa principalmente para controlar el tamaño del resultado, especialmente en consultas grandes o en paginación de datos.

### Sintaxis básica
```sql
SELECT * FROM empleados LIMIT 5;
```

 Devuelve solo los primeros 5 registros.

---

### OFFSET

Permite saltar registros antes de empezar a mostrar resultados.
```sql
SELECT *FROM empleados 
LIMIT 5 
OFFSET 10;
```

Salta los primeros 10 registros y muestra los siguientes 5.

---

