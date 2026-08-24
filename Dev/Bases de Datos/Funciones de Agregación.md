---
tags:
  - 
  
---
Las **funciones de agregado** realizan cálculos sobre **un conjunto de filas** y devuelven **un único valor**.

Se usan generalmente junto con **GROUP BY** dentro de una consulta **SELECT**.

Son **deterministas** → siempre devuelven el mismo resultado para el mismo conjunto de datos.

Permiten obtener **estadísticas** sobre los datos.

---

## Funciones más comunes


### COUNT()
- Cuenta la cantidad de filas o valores no nulos en una columna.

```sql
SELECT COUNT(*) FROM pedidos;
```

##### Resultado:  
Devuelve la cantidad total de pedidos.

[[COUNT DISTINCT]]

---

### SUM()
Suma todos los valores de una columna numérica.

```sql
SELECT SUM(monto) FROM pedidos;
```

##### Resultado:  
Devuelve el total de dinero vendido.

---

### AVG()
Calcula el promedio de una columna numérica.

```sql
SELECT AVG(monto) FROM pedidos;
```

##### Resultado:  
Devuelve el promedio de los montos de pedidos.

---

### MIN()
Devuelve el valor mínimo de una columna.

```sql
SELECT MIN(monto) FROM pedidos;
```

##### Resultado:  
Devuelve el pedido con menor monto.

---

### MAX()
Devuelve el valor máximo de una columna.

```SQL
SELECT MAX(monto) FROM pedidos;
```

##### Resultado:  
Devuelve el pedido con mayor monto.

---

