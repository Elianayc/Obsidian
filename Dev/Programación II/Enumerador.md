---
tags:
  - Programación
  - ProgramaciónII
---
Un **enum (enumerador)** es un tipo de dato que define un conjunto cerrado de valores con nombre.

Se utiliza para representar opciones fijas dentro de un rango limitado de posibilidades.

```ts
enum Estado {
    Activo,
    Inactivo,
    Pendiente
}
```


```ts
let estadoUsuario: Estado;  
estadoUsuario = Estado.Activo;
```
