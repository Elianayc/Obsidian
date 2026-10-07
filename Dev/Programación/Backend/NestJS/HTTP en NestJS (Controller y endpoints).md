En NestJS, un **Controller** recibe solicitudes HTTP y define los endpoints que expone el backend.

```
Frontend
↓ request HTTP
Controller NestJS
↓
endpoint
↓
response
↓
Frontend
```

---

## Controller

```ts
@Controller('encounters')
export class EncountersController {
}
```

`@Controller()` define la **ruta base** de los endpoints del Controller.

En este ejemplo:

```
/encounters
```

es la ruta base.

---

## Endpoints

Un **endpoint** es una operación de una API identificada por:

```ts
método HTTP + URL
```

Ejemplo:

```ts
GET /current/encounters
```

- `GET` → método HTTP.
- `/current/encounters` → URL del endpoint.

Por lo tanto:

```
GET /current/encounters
│          │
│          └── URL
└── método HTTP
```

---

- [[Decoradores HTTP]]
- [[Datos del Request]]
- [[Swagger]]

---
