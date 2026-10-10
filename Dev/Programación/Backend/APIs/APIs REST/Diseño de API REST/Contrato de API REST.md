Un **contrato de API** define cómo se van a comunicar el cliente y el servidor.

Establece qué operaciones existen, qué datos reciben y qué datos devuelven.

Un contrato incluye principalmente:

```text
endpoint
├── método HTTP
├── URL
├── request
├── response
└── código HTTP
```

Por ejemplo:

```text
GET /conversations
```

puede definir:

```text
Request
→ no recibe body

Response
→ lista de conversaciones

Código HTTP
→ 200
```

El contrato puede definirse **antes de implementar la lógica real del Backend**.

Esto permite que Frontend y Backend sepan de antemano cómo deben comunicarse.

---

## Swagger-first

En un enfoque **Swagger-first** primero se define y documenta el contrato de la API y después se implementa su lógica.

```text
definir contrato
↓
documentarlo en Swagger
↓
implementar Backend
↓
conectar Frontend
```

Swagger permite ver y probar ese contrato antes de tener toda la lógica terminada.

---

## Conceptos relacionados

- [[Recursos y URLs]]
- [[Swagger]]
- [[Contratos del Request]]
- [[HTTP en NestJS (Controller y endpoints)]]

---