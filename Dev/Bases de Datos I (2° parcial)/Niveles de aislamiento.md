El estándar SQL define **4 niveles de aislamiento** de transacciones:

- [[Read Uncommitted]]
- [[Read Committed]]
- [[Repeatable Read]]
- [[Serializable]]

Cuanto más alto el nivel → **menos problemas de concurrencia**, pero **más costo en rendimiento**.

El nivel más estricto es **Serializable**: garantiza que ejecutar transacciones en paralelo produce el mismo resultado que ejecutarlas una por una.

---

## Comando para definir aislamiento
Se usa dentro de TCL:

```sql
SET TRANSACTION ISOLATION LEVEL ...
```

---
