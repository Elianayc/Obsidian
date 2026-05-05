Nivel más bajo del estándar SQL.

Permite, en teoría, leer datos que todavía **no fueron confirmados (COMMIT)** por otras transacciones.

En PostgreSQL no se implementa realmente: se comporta igual que **Read Committed**.

### Qué evita
- Ninguna anomalía garantizada por el estándar.

### Qué permite
- **Dirty reads** (teóricamente, pero no en PostgreSQL)

