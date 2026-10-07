Las **funciones flecha** (_arrow functions_) son una forma abreviada de escribir funciones en JavaScript y TypeScript.

Se reconocen por el operador:

```javascript
=>
```

---

## Sintaxis

Una función tradicional:

```typescript
function sumar(numero1: number, numero2: number): number {
  return numero1 + numero2;
}
```

Puede escribirse como función flecha:

```typescript
const sumar = (numero1: number, numero2: number): number => {
  return numero1 + numero2;
};
```

Mentalmente:

```text
(parámetros) => {
    instrucciones
}
```

---

## Retorno abreviado

Cuando la función solamente tiene que retornar una expresión:

```typescript
const sumar = (numero1: number, numero2: number): number => {
  return numero1 + numero2;
};
```

se pueden eliminar las llaves y el `return`:

```typescript
const sumar = (numero1: number, numero2: number): number =>
  numero1 + numero2;
```

Es decir:

```text
(x) => {
    return expresión;
}

        ↓

(x) => expresión
```

La expresión puede ser también una condición:

```typescript
const esMayorDeEdad = (edad: number): boolean => edad >= 18;
```

Para el funcionamiento de las expresiones que retornan directamente `true` o `false`, ver [[Estructuras de control]].

---

## Uso como callback

Es común encontrar funciones flecha pasadas como argumento a otras funciones.

Por ejemplo:

```typescript
numeros.forEach((numero) => {
  console.log(numero);
});
```

También pueden aparecer en forma abreviada:

```typescript
const numerosMayores = numeros.filter((numero) => numero > 10);
```

Ver [[Event Loop y Callbacks]].

## `this`

Las funciones flecha tienen un comportamiento particular con `this`: no crean su propio `this`, sino que utilizan el del contexto donde fueron creadas.

Ver [[Palabra `this`]].

---