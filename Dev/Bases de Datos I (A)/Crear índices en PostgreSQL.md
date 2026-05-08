## Crear índices en PostgreSQL
Por defecto, PostgreSQL crea índices **B-Tree**, ya que sirven para la mayoría de los casos.

### Sintaxis básica
```sql
CREATE [UNIQUE] INDEX [CONCURRENTLY] nombre_indice
ON tabla [USING metodo]
(columna | (expresion))
[WHERE condicion];
```

### Opciones importantes
- **UNIQUE** → evita valores duplicados en el índice
- **CONCURRENTLY** → crea el índice sin bloquear la tabla
- **USING method** → tipo de índice (btree, hash, gin, gist, spgist, brin)
- **(expresion)** → permite crear índices basados en cálculos
- **WHERE** → permite crear **índices parciales**

---

## Mantenimiento de índices
Cuando se crean índices sobre tablas con datos (y periódicamente), se recomienda ejecutar:

```sql
VACUUM FULL ANALYZE nombre_tabla;
```

###### Este comando:
- Reorganiza la tabla
- Limpia espacio
- Actualiza estadísticas del optimizador
- Mejora el rendimiento de consultas e índices