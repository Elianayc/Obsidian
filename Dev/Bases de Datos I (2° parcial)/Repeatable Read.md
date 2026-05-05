Toda la transacción ve **el mismo snapshot desde el inicio de la transacción**.

Si otra transacción cambió un dato yo no lo veo. 

### Evita
- Dirty reads
- Non-repeatable reads
- Phantom reads (en PostgreSQL)

### Puede permitir
- Serialization anomalies