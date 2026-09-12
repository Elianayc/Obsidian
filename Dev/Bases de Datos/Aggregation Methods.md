
Son los métodos que puede utilizar el planner para ejecutar operaciones de agregación, como `GROUP BY`.

- **[[Hash Aggregate]]** → utiliza una estructura hash para agrupar los registros.
- **[[Sort Aggregate - Group Aggregate]]** → ordena los registros por las columnas de agrupación y luego procesa los grupos.

El método elegido depende del plan de ejecución que el planner considere menos costoso.

---
