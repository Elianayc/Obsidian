Un Set es una colección de valores **únicos**.
**No permite duplicados** y mantiene el **orden de inserción**.

#### Ejemplo
```ts
const set = new Set<number();

set.add(10);
set.add(20);
set.add(20);
set.add(30);

console.log(set);
```

`.has` Chequea si existe el elemento.
`.delete` Elimina el elemento.

`agenda.forEach(unico)=>{console.log(unico);}` Recorrido.3

Comparación de Sets

Los sets de Typescript se comparas en cuanto a igualdad por referencia a memoria siempre que sean string, boolean o number.

Para poder comparar por contenido se puede definir un id **getKey** y se puede usar una clase genérica **GenericSet<>** que:

Reciba (x:T) => string para obtener la clave única.

Usar esa clave para add, has, get, delete, evitando de estaforma dos objetos con el mismo id se consideren iguales.

Nota: yo definiría un equals.