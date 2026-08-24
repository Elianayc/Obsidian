---
tags:
  - 
  
---
Permite combinar tablas relacionadas.

```SQL
SELECT e.nombre, d.nombre_departamento 
FROM empleados e 
JOIN departamentos d 
ON e.id_departamento = d.id_departamento;
```

![[Pasted image 20260806144539.png|598]]

---

### INNER JOIN

Devuelve solo coincidencias en ambas tablas.

![[Pasted image 20260806144602.png]]

```SQL
SELECT e.nombre, d.nombre_departamento
FROM empleados e
INNER JOIN departamentos d
ON e.id_departamento = d.id_departamento;
```

---

### FULL JOIN

Devuelve todo de ambas tablas.

![[Pasted image 20260806144622.png]]

```SQL
SELECT e.nombre, d.nombre_departamento
FROM empleados e
FULL OUTER JOIN departamentos d
ON e.id_departamento = d.id_departamento;
```


---

### LEFT JOIN

Devuelve todo de la tabla izquierda + coincidencias.

![[Pasted image 20260806144723.png]]



```SQL
SELECT e.nombre, d.nombre_departamento
FROM empleados e
LEFT JOIN departamentos d
ON e.id_departamento = d.id_departamento;
```

---

### RIGHT JOIN

Devuelve todo de la tabla derecha + coincidencias.

![[Pasted image 20260806144800.png]]

```SQL
SELECT e.nombre, d.nombre_departamento
FROM empleados e
RIGHT JOIN departamentos d
ON e.id_departamento = d.id_departamento;
```

---


