Nivel más bajo del estándar SQL.

En PostgreSQL no se implementa realmente: se comporta igual que **Read Committed**.

### Qué evita
- Ninguna anomalía garantizada por el estándar.

### Qué permite
- **Dirty reads** (teóricamente, pero no en PostgreSQL)