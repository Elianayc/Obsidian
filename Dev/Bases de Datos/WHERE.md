Se utiliza para **filtrar registros** antes de mostrar resultados.

```SQL
SELECT * FROM pedidos WHERE monto > 2000;
```

##### Resultado:  
Devuelve solo los pedidos con monto mayor a 2000.

##### Operadores de Filtrado
Los operadores de filtrado se utilizan dentro de consultas **SELECT** para restringir los resultados según condiciones específicas.
No son cláusulas completas, sino expresiones que se combinan con `WHERE` u otras condiciones.
 - [[LIKE]]
 - [[BETWEEN]]
 - [[IN]]
 - [[NOT IN]]
