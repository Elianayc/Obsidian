`finalize()` es un operador de RxJS, por eso va dentro de `pipe()`.

```ts
.pipe(
  finalize(() => {
    this.cargando = false;
  })
)
```

Se ejecuta cuando el Observable termina, tanto si salió bien como si ocurrió un error.

Por eso es útil para estados de carga.

```
cargando = true
↓
Observable
↓
├── éxito
└── error
↓
finalize
↓
cargando = false
```

---

## complete vs finalize

`complete`:

```
se ejecuta cuando el Observable termina correctamente
```

`finalize`:

```
se ejecuta cuando el Observable termina,
haya salido bien o mal
```

Caso exitoso:

```
next
↓
complete
↓
finalize
```

Caso con error:

```
error
↓
finalize
```

---