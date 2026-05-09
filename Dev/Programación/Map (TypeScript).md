---
tags:
  - Programación
  - ProgramaciónII
---
Un Map es una colección de pares **clave–valor**.

Cada clave es única y permite asociar un valor a una clave específica.

### Ejemplo
```ts
const map = new Map<string, number>();

map.set("Ana", 25);
map.set("Luis", 30);
map.set("Ana", 40);

console.log(map);
```

`.get` Obtiene un elemento.
`.has` Chequea si el elemento existe.
`.delete` Elimina el elemento.

`agenda.forEach((value, key)=>{console.log('nombre: ${key}, número: ${value}');` Recorrido.