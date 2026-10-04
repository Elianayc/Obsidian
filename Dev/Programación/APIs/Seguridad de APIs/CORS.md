**CORS (Cross-Origin Resource Sharing)** es un mecanismo de seguridad que permite controlar qué solicitudes realizadas desde un **origen diferente** pueden ser aceptadas por el navegador.

---

### Origen

Un **origen** está determinado por:

- **Protocolo**: `http` o `https`.
- **Dominio**.
- **Puerto**.

Por ejemplo:

```text
https://api.example.com:443/users
https://api.example.com:443/products
```

pertenecen al mismo origen porque tienen el mismo **protocolo, dominio y puerto**.

En cambio:

```text
https://evil.com/steal-data
```

tiene un **dominio** diferente.

Y:

```text
http://api.example.com/users
```

tiene un **protocolo** diferente.

> Si el puerto no se indica, se utiliza el puerto por defecto del protocolo. Por ejemplo, `https` utiliza normalmente el puerto `443`.

---

### Same-Origin Policy

Por defecto, los navegadores aplican la **Same-Origin Policy (SOP)**, una política de seguridad que restringe determinadas solicitudes entre orígenes diferentes.

**CORS permite que el servidor indique qué solicitudes cross-origin están permitidas.**

Por ejemplo:

```text
Frontend
https://miapp.com
      ↓
      ↓ solicitud
      ↓
API
https://api.example.com
```

Como son orígenes diferentes, interviene CORS.

El servidor puede indicar que permite solicitudes desde `https://miapp.com` mediante headers como:

```http
Access-Control-Allow-Origin: https://miapp.com
```

---

### Preflight Request

Para determinadas solicitudes cross-origin, el navegador realiza primero una solicitud HTTP **`OPTIONS`**, denominada **Preflight Request**.
Su objetivo es consultar al servidor si la solicitud real está permitida.

#### Funcionamiento

1. El navegador envía una solicitud `OPTIONS`.
2. El servidor responde indicando qué **orígenes, métodos y headers** están permitidos.
3. Si la respuesta permite la operación, el navegador realiza la solicitud real.

Por ejemplo, el servidor puede responder:

```http
Access-Control-Allow-Origin: https://miapp.com
Access-Control-Allow-Methods: GET, POST, PUT, DELETE
Access-Control-Allow-Headers: Content-Type, Authorization
```

#### ¿Cuándo se realiza un Preflight?

Generalmente cuando:

- Se utilizan métodos como `PUT`, `DELETE` o `PATCH`.
- Se utilizan headers no considerados simples, como `Authorization`.
- Se utiliza `Content-Type: application/json`.
- Se utilizan otros headers personalizados.

> **Importante:** el Preflight no es un JSON. Es una **solicitud HTTP `OPTIONS` previa** que el navegador utiliza para consultar al servidor.

---

### Simple Requests

Son solicitudes **cross-origin** que cumplen determinadas condiciones y **no requieren un preflight**.

Generalmente:

- Métodos: `GET`, `HEAD` o `POST`.
- Headers considerados simples.
- `Content-Type`:
    - `text/plain`
    - `multipart/form-data`
    - `application/x-www-form-urlencoded`

Estas solicitudes pueden enviarse directamente.

---

### Implementación

En Express se puede configurar CORS indicando qué orígenes, métodos, headers y credenciales están permitidos.

Para desarrollo:

```js
const cors = require('cors');

app.use(cors());
```

Para producción:

```js
const corsOptions = {
  origin: [
    'https://miapp.com',
    'https://www.miapp.com',
    'https://admin.miapp.com'
  ],
  methods: ['GET', 'POST', 'PUT', 'DELETE'],
  allowedHeaders: [
    'Content-Type',
    'Authorization'
  ],
  credentials: true,
  maxAge: 86400
};

app.use(cors(corsOptions));
```

- `origin` → qué orígenes pueden acceder.
- `methods` → qué métodos HTTP se permiten.
- `allowedHeaders` → qué headers puede enviar el cliente.
- `credentials` → si se permiten credenciales, como cookies.
- `maxAge` → cuánto tiempo puede conservar el navegador la respuesta del Preflight.

---

### Buenas prácticas

- No utilizar configuraciones excesivamente permisivas en producción.
- Especificar **orígenes exactos**.
- Evitar `*` cuando no sea necesario.
- Limitar los métodos HTTP a los estrictamente necesarios.
- Limitar los headers permitidos.
- Utilizar **HTTPS** en producción.
- Configurar `maxAge` para optimizar la caché del Preflight.
- Monitorear las solicitudes CORS fallidas.

> **Importante:** CORS controla principalmente qué solicitudes **cross-origin pueden realizar los navegadores**. No debe considerarse por sí solo un mecanismo de protección contra **CSRF**.

----

