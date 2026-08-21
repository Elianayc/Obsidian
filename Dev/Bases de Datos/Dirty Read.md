---
tags:
  - 
  
---
### Lectura sucia
Una transacción lee datos **n confirmados** de otra transacción.  

Si la otra hace rollback → se usaron datos que nunca existieron.

PostgreSQL NO permite este fenómeno.
