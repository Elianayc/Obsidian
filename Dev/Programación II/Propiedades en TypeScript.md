Son una forma propia del lenguaje de declarar getters y setters utilizando las palabras clave `get` y `set`.
Permiten acceder al atributo **como si fuera una propiedad normal**, manteniendo la encapsulación internamente.
Esto mejora la **legibilidad y naturalidad del código**.

##### Getter
```ts
public get name(): string {return this._name;}
```

##### Setter
```ts
public set name(value: string) {this._name = value;}
```

##### Uso
```ts
persona.name; //Get
persona.name = "Ana"; //Set
```
