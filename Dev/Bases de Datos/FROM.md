---
tags:
  - DBI1erparcial
  - DB
---
La cláusula **FROM** se utiliza en SQL para indicar **de qué tabla o tablas se van a obtener los datos**.

Es una parte fundamental del comando **SELECT**, ya que sin FROM no se puede acceder a una fuente de datos.

### Función principal
- Define la(s) tabla(s) origen de la consulta
- Permite trabajar con una o varias tablas
- Es obligatoria en la mayoría de consultas SELECT


### Sintaxis básica
```SQL
SELECT nombre, email FROM clientes;
```

Indica que los datos se obtienen de la tabla clientes.

### FROM con alias
Los alias permiten renombrar temporalmente una tabla para simplificar consultas.

```SQL
SELECT e.nombre FROM empleados e;
```

“e” es un alias de la tabla empleados.


### FROM con múltiples tablas (JOIN implícito)

```SQL
SELECT e.nombre, d.nombre_departamento FROM empleados e, departamentos d;
```

Aunque hoy se usa más JOIN, esto muestra que FROM puede incluir varias tablas.


#BasesdeDatos