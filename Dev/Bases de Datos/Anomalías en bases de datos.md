---
tags:
---
Las anomalías aparecen cuando la base de datos no está bien normalizada, generando inconsistencias entre tablas padre e hijas.

- **Anomalía de inserción (Insert)**
  Ocurre cuando se intenta insertar un registro en una **tabla hija** sin que exista previamente el registro relacionado en la **tabla padre**.

- **Anomalía de eliminación (Delete)**
  Ocurre cuando se elimina un registro de una **tabla padre**, dejando registros huérfanos en una o varias **tablas hijas**.

- **Anomalía de actualización (Update)**
  Ocurre cuando se modifica un dato en una tabla y ese cambio no se propaga correctamente a todas las tablas relacionadas, generando **inconsistencias o datos desactualizados**.
#BasesdeDatos