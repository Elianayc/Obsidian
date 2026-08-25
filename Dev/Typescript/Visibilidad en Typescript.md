---
tags:
  - ProgramaciónII
---
En TypeScript, la visibilidad se maneja de forma diferente a otros lenguajes como Java o C#.

---

### Clases
Las clases no utilizan modificadores de visibilidad como `public`, `private` o `protected`.

La visibilidad de una clase se define mediante `export`.

```typescript
export class Inmueble {}
```

Si una clase no tiene `export`, solo puede ser utilizada dentro del mismo archivo.

---

### Atributos y métodos
Los modificadores de visibilidad sí se aplican a los miembros de la clase.

- `private`: solo accesible dentro de la clase
- `protected`: accesible en la clase y sus subclases
- `public`: accesible desde cualquier parte (por defecto)

```typescript
class Inmueble {  
	private direccion: string;  
	public nombre: string;
}
```

---

[[Readonly en TypeScript]]

