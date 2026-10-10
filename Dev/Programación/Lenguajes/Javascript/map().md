`map()` transforma el valor que emite un Observable.

```ts
map((datoRecibido) => datoTransformado)
```

Flujo:

```
dato original
↓
map()
↓
dato transformado
```

Ejemplo:

```ts
map((response) => response.data)
```

Entra:

```
response
├── success
├── message
└── data
```

Sale:

```ts
data
```

Machete:

```ts
map() = transforma el dato
```
