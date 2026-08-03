---
tags:
  - Modeladodesistemas
---
`readonly` se utiliza para indicar que una propiedad solo puede ser asignada una vez, generalmente en el constructor, y no puede modificarse después.

Se usa para modelar datos inmutables dentro de un objeto.

```ts
class Inmueble {
  public readonly direccion: Direccion;

  constructor(direccion: Direccion) {
    this.direccion = direccion;
  }
}
```

---

## `private readonly`

Se utiliza cuando la propiedad:

- no debe ser accesible desde fuera de la clase
    
- y además no debe modificarse después de su inicialización
    

```ts
class Inmueble {
  private readonly direccion: Direccion;

  constructor(direccion: Direccion) {
    this.direccion = direccion;
  }
}
```

---

## Diferencia con `private`

- `private`: controla el acceso (no se puede acceder desde afuera), pero puede modificarse dentro de la clase
    
- `readonly`: controla la mutabilidad (no se puede modificar después de inicializarse), pero puede ser público o privado
    

---

## Cuándo usar `readonly`

Se usa cuando:

- el valor no debe cambiar después de creado el objeto
    
- querés evitar modificaciones accidentales
    
- estás modelando datos estables del dominio
    

**Ejemplos típicos**:

- dirección
    
- código postal
    
- datos de creación del objeto
    

---

## Relación con encapsulamiento

`readonly` no reemplaza `private`, lo complementa:

- `private` → oculta el dato
    
- `readonly` → evita cambios después de la inicialización
    
- `private readonly` → oculta el dato y además lo vuelve inmutable
    

---

> `readonly` ayuda a diseñar objetos más simples, seguros y predecibles, reduciendo la necesidad de setters y lógica de modificación externa.
#Arquitecturadesistemas