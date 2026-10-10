**NestJS** es un framework de Backend basado en TypeScript.

Permite organizar una aplicación del lado servidor mediante Controllers, Services y Modules.

---

## Estructura básica

Una funcionalidad de NestJS suele organizarse así:

```text
Module
├── Controller
├── Service
├── Request
└── Models
```

El Module agrupa las piezas.
El Controller recibe las solicitudes HTTP.
El Service contiene la lógica.
Los Request describen los datos que entran.
Los Models representan datos con los que trabaja la aplicación.

---

## Temas de NestJS

- [[Módulos en NestJS]]
- [[HTTP en NestJS (Controller y endpoints)]]
- [[Decoradores HTTP]]
- [[Datos del Request]]
- [[Contratos del Request]]
- [[Respuestas en NestJS]]
- [[Swagger]]

---

## Flujo general

```text
Frontend
↓
HTTP
↓
Controller
↓
Service
↓
API / Base de datos
↓
Service
↓
Controller
↓
Response
↓
Frontend
```

---
