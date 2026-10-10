Los **genéricos** permiten escribir código que puede trabajar con distintos tipos sin tener que repetirlo.

La letra `T` suele utilizarse como un tipo todavía no definido.

```ts
get<T>()
```

Significa:

```text
T
↓
"el tipo me lo vas a decir cuando uses este método"
```

Por ejemplo:

```ts
this.get<Conversation[]>('conversations')
```

En ese caso:

```text
T = Conversation[]
```

---

## Ejemplo con Observable

```ts
Observable<boolean>
```

significa:

```text
Observable
↓
más adelante emite
↓
boolean
↓
true o false
```

No devuelve directamente un `boolean`.

Devuelve un `Observable` cuyo valor será un `boolean`.

---

## Ejemplo con ResponseObject

```ts
ResponseObject<T>
```

permite utilizar siempre la misma estructura:

```text
success
responseMessage
serverTime
data
```

pero cambiar el tipo de `data`.

Por ejemplo:

```ts
ResponseObject<Conversation[]>
ResponseObject<Message[]>
ResponseObject<AuthSession>
```

---

## Ejemplo completo

```ts
protected get<T>(
  path: string
): Observable<ResponseObject<T>>
```

Se puede leer así:

```text
get<T>
→ GET genérico

path: string
→ recibe una ruta

Observable<ResponseObject<T>>
→ devuelve un Observable
→ que emitirá un ResponseObject
→ cuyo data será del tipo T
```

Regla mental:

```text
<T>
= qué tipo espero manejar o recibir
```

---
