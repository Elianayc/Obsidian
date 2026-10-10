`pipe()` permite aplicar **operadores de RxJS** al Observable antes de consumirlo con `subscribe()`.

```ts
observable
  .pipe(
    operador1(),
    operador2()
  )
  .subscribe(...);
```

Conceptualmente:

```
Observable
↓
pipe()
aplica operadores
↓
subscribe()
consume el resultado
```

`pipe()` no siempre es necesario.

Algunos operadores son:

```ts
map()
tap()
filter()
switchMap()
finalize()
```

