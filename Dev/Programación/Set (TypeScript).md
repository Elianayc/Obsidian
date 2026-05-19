---
tags:
  - Programación
  - ProgramaciónII
---
Un Set es una colección de valores **únicos**.
**No permite duplicados** y mantiene el **orden de inserción**.

> [!example]
> 
> ```ts
> const set = new Set<number();
> 
> set.add(10);
> set.add(20);
> set.add(20);
> set.add(30);
> 
> console.log(set);
> ```
> 
> `.has` Chequea si existe el elemento.
> `.delete` Elimina el elemento.
> 
> `agenda.forEach(unico)=>{console.log(unico);}` Recorrido.3

---

### Comparación de Sets
En TypeScript, un Set compara sus elementos de la siguiente manera:
- Los valores primitivos (number, string, boolean) se comparan por **valor**.
- Los objetos se comparan por **referencia**, es decir, dos objetos distintos en memoria nunca son iguales aunque tengan el mismo contenido.

#### Comparación por contenido (solución)
Para comparar objetos por contenido (por ejemplo, por id), se debe implementar una estrategia externa, como:

- Usar una clave única con Map.
- O controlar duplicados manualmente antes de insertar.

> [!example]
> **Ejemplo con control por clave:**
> ```ts
> // Creamos un Set de números.
> // Un Set solo permite valores únicos (no duplicados).
> const set = new Set<number>();
> 
> // Función que agrega un número solo si todavía no existe en el Set
> function addIfNotExists(id: number) {
> 
>     // Preguntamos si el valor YA está dentro del Set
>     // set.has(id) devuelve true si existe, false si no existe
>     if (!set.has(id)) {
> 
>         // Si NO existe, lo agregamos al Set
>         set.add(id);
>     }
> }
> 
> // Ejemplo de uso:
> 
> addIfNotExists(10); // Se agrega porque no existe
> addIfNotExists(20); // Se agrega porque no existe
> addIfNotExists(10); // No se agrega porque ya está
> 
> console.log(set); // Resultado: {10, 20}
> ```
> 
> 