---
tags:
  - 
  
---
El comando **UPDATE** permite **modificar uno o varios registros** de una tabla.

### Sintaxis básica
```SQL
UPDATE tablaSET campo1 = valor1,    
campo2 = valor2,    
...
[WHERE condicion];
```

⚠️ Si no se usa **WHERE**, se actualizan **todos los registros** de la tabla.

---

### Ejemplo
```SQL
UPDATE usuarios
SET description = 'hola mundo'
WHERE id < 10;
```

---

