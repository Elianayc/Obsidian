Un Backend puede centralizar la creación de respuestas para evitar repetir la misma estructura en todos los Controllers.
Una forma de hacerlo es mediante una [[Clase Abstracta]] que sirve como base para distintos Controllers.

```text
AbstractController
↓
contiene comportamiento común

Controller concreto
↓
extends AbstractController
↓
puede utilizar los métodos heredados
```

Por ejemplo:

```ts
export class ConversationController extends AbstractController {
}
```

La palabra `extends` indica [[Herencia]].

Gracias a esa herencia, el Controller puede utilizar métodos definidos en la clase padre:

```ts
this.createOkResponse(...)
```

sin tener que volver a implementarlos.

---

## AbstractController

Una clase como:

```ts
export abstract class AbstractController {
  protected createOkResponse<T>(data: T): ResponseObject<T> {
    // ...
  }
}
```

puede contener comportamiento común para los Controllers.

Después, cada Controller concreto puede heredarlo:

```ts
export class ConversationController extends AbstractController {
}
```

Conceptualmente:

```text
AbstractController
├── createOkResponse()
├── createOkResponseWithMessage()
└── createErrorResponse()

        ↓ herencia

ConversationController
MessageController
otros Controllers
```

---

## ResponseBuilder

Un `ResponseBuilder` puede encargarse de construir respuestas con una estructura consistente.

```text
Controller
↓
createOkResponse()
↓
ResponseBuilder
↓
ResponseObject
↓
respuesta HTTP
```

Esto evita repetir en cada endpoint la creación manual de campos como:

```text
success
responseMessage
serverTime
data
```

Por ejemplo, en lugar de construir siempre:

```ts
new ResponseObject(
  true,
  new ResponseMessage('0000', 'OK'),
  new Date().toISOString(),
  data
);
```

el Controller puede utilizar:

```ts
this.createOkResponse(data);
```

---

## `ResponseObject<T>`

`ResponseObject<T>` permite mantener una estructura común de respuesta y cambiar solamente el tipo de dato contenido.

Por ejemplo:

```ts
ResponseObject<ConversationModel>
```

o:

```ts
ResponseObject<MessageModel>
```

La `T` representa el tipo de dato que contiene la respuesta.

Conceptualmente:

```text
ResponseObject<T>
│
├── success
├── responseMessage
├── serverTime
└── data → T
```

Entonces:

```text
estructura común
+
dato específico
```

Esto permite mantener respuestas consistentes entre distintos Controllers.

---

## Ejemplo de flujo

```text
Frontend
↓
GET /conversations
↓
ConversationController
↓
createOkResponse(...)
↓
AbstractController
↓
ResponseBuilder
↓
ResponseObject<ConversationModel[]>
↓
Frontend
```

---
