`tap()` permite hacer algo con el valor que pasa por el Observable **sin transformarlo**.

```ts
tap((conversacionesRecibidas) => {
  this.conversaciones = conversacionesRecibidas;
})
```

Machete:

```ts
map() → transforma el dato

tap() → hace algo con el dato,
        pero el dato sigue igual
```

---