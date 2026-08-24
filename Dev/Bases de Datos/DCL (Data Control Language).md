---
tags:
  - 
  
---
Controla permisos y seguridad de la base de datos.
Se usa para controlar quién puede acceder o modificar datos.


### GRANT
Se utiliza para otorgar permisos a usuarios sobre objetos de la base de datos.

```sql
GRANT SELECT, INSERT ON clientes TO usuario1;
```

---

### REVOKE

Se utiliza para quitar permisos previamente otorgados a un usuario.

```sql
REVOKE SELECT, INSERT ON clientes FROM usuario1;
```

---

### DENY

Se utiliza para negar explícitamente permisos a un usuario, incluso si fueron otorgados por otro rol o grupo.

```sql
DENY DELETE ON clientes TO usuario1;
```

---

