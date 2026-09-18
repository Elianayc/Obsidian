**CORS (Cross-Origin Resource Sharing)** es un mecanismo de seguridad implementado por los navegadores que controla si una página web puede realizar solicitudes hacia recursos pertenecientes a un **origen diferente**.

Un origen está determinado por:

- Protocolo.
- Dominio.
- Puerto.

---

## Same-Origin Policy

Por defecto, los navegadores aplican la **Same-Origin Policy**, que restringe determinadas solicitudes entre orígenes diferentes.

**Por ejemplo**:

```text
https://api.example.com:443/users
https://api.example.com:443/products
```

pertenecen al mismo origen.


**Mientras que**:

```
https://evil.com/steal-data
```

tiene un dominio diferente.


**Y**:

```
http://api.example.com/users
```

tiene un protocolo diferente.

---

## Preflight Request

Para determinadas solicitudes cross-origin, el navegador realiza primero una solicitud **OPTIONS**, denominada **preflight request**.

Su objetivo es consultar al servidor si la solicitud real está permitida.

### Funcionamiento

1. El navegador envía una solicitud `OPTIONS`.
2. El servidor responde indicando qué orígenes, métodos y headers están permitidos.
3. Si la solicitud está permitida, el navegador realiza la solicitud real.

Entre los headers utilizados se encuentran:

```
Access-Control-Allow-Origin
Access-Control-Allow-Methods
Access-Control-Allow-Headers
```

### ¿Cuándo se realiza un preflight?

Generalmente cuando:

- Se utilizan métodos distintos de `GET`, `POST` o `HEAD`.
- Se utilizan headers no considerados simples, como `Authorization`.
- Se utiliza `Content-Type: application/json`.

---

## Implementación

```js
const cors = require('cors');

// Solo recomendado para desarrollo
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

---

## Simple Requests

Son solicitudes que cumplen determinadas condiciones y **no requieren preflight**.

- Métodos: `GET`, `HEAD`, `POST`.
- Headers considerados simples.
- `Content-Type`:
    - `text/plain`
    - `multipart/form-data`
    - `application/x-www-form-urlencoded`

---

## Preflighted Requests

Son solicitudes que requieren una solicitud `OPTIONS` previa.

Por ejemplo:

- `PUT`
- `DELETE`
- `PATCH`
- Header `Authorization`.
- Headers personalizados.
- `Content-Type: application/json`.

---

## Buenas prácticas

1. No utilizar configuraciones excesivamente permisivas en producción.
2. Especificar **orígenes exactos**.
3. Evitar comodines (`*`) cuando no sean necesarios.
4. Limitar los métodos HTTP a los estrictamente necesarios.
5. Validar los headers permitidos.
6. Utilizar HTTPS en producción.
7. Configurar `maxAge` para optimizar la caché del preflight.
8. Monitorear las solicitudes CORS fallidas.

> **Importante:** CORS controla principalmente qué solicitudes cross-origin pueden realizar los navegadores. No debe considerarse por sí solo un mecanismo de protección contra CSRF.

----
