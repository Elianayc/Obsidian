Una clase de request define el **contrato de los datos que puede o debe recibir un endpoint**.

Ejemplo:

```ts
export class CreateDemoMessageRequest {
  content!: string;
  name!: string;
}
```

En este caso se esperan ambos datos.

```ts
export class UpdateDemoMessageRequest {
  content?: string;
  name?: string;
}
```

En este caso los datos son opcionales.

```
! → la propiedad se espera definida
? → la propiedad es opcional
```

El contrato del request **no define el método HTTP**.

El Controller decide dónde utilizarlo:

```ts
@Post()
createMessage(@Body() request: CreateDemoMessageRequest) {
}
```

```ts
@Patch(':messageId')
updateMessage(@Body() request: UpdateDemoMessageRequest) {
}
```

---
