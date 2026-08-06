---
tags:
  - DB
  - DBI2doparcial
---
Consiste en reordenar los datos de una tabla de acuerdo a un índice creado previamente y reescribirla en disco.

> [!Sintaxis]
> ```sql
> CLUSTER[VERBOSE] table_name [USING index_name]
> ```


> [!example]
> 
> ```sql
> CREATE INDEX geom_idx 
> ON TABLE my_table_geo 
> USING GIST (the_geom);
> 
> CLUSTER my_table_geo USING geom_idx;
> ```



#BasesdeDatos