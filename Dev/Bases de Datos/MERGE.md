---
tags:
  - 
  
---
Se utiliza para combinar operaciones de inserción, actualización o eliminación según si el registro existe o no.

```sql
MERGE INTO clientes c  
USING nuevos_clientes n  
ON c.id = n.id  
WHEN MATCHED THEN  
UPDATE SET c.nombre = n.nombre  
WHEN NOT MATCHED THEN  
INSERT (id, nombre) VALUES (n.id, n.nombre);
```
#BasesdeDatos