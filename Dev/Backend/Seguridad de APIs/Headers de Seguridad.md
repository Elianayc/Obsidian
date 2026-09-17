Los **headers HTTP de seguridad** proporcionan una capa adicional de protección indicando al navegador cómo debe comportarse al procesar determinado contenido.

---

## X-Content-Type-Options

Previene ataques de **MIME sniffing**, evitando que el navegador intente interpretar el contenido como un tipo diferente al declarado.

```js
res.setHeader('X-Content-Type-Options', 'nosniff');
```

---

## X-Frame-Options

Controla si el contenido puede ser cargado dentro de un `iframe`, ayudando a prevenir ataques de **clickjacking**.

```js
res.setHeader('X-Frame-Options', 'DENY');
```

También puede utilizarse `SAMEORIGIN`.

---

## X-XSS-Protection

Es un mecanismo antiguo relacionado con la protección contra XSS.

Actualmente está **deprecado** y se prioriza el uso de **Content-Security-Policy (CSP)**.

```js
res.setHeader('X-XSS-Protection', '1; mode=block');
```

---

## Strict-Transport-Security (HSTS)

Fuerza al navegador a utilizar **HTTPS** durante un período determinado.

Ayuda a prevenir ataques de downgrade.

```js
res.setHeader(
  'Strict-Transport-Security',
  'max-age=31536000; includeSubDomains; preload'
);
```

---

## Content-Security-Policy (CSP)

Define qué tipos de contenido y recursos puede cargar el navegador, ayudando a prevenir la **inyección de código malicioso**.

```js
res.setHeader(
  'Content-Security-Policy',
  "default-src 'none'; frame-ancestors 'none';"
);
```

---

## Referrer-Policy

Controla qué información del encabezado `Referer` puede enviarse a otros sitios.

```js
res.setHeader(
  'Referrer-Policy',
  'strict-origin-when-cross-origin'
);
```

---

## Permissions-Policy

Controla qué funcionalidades del navegador pueden utilizarse.

```js
res.setHeader(
  'Permissions-Policy',
  'geolocation=(), microphone=(), camera=()'
);
```

---

## Ocultar información del servidor

También es recomendable evitar exponer información innecesaria sobre las tecnologías utilizadas.

### X-Powered-By

Puede revelar el framework utilizado, por ejemplo Express.

```js
res.removeHeader('X-Powered-By');
```

### Server

Puede revelar información sobre el software utilizado para procesar las solicitudes, como Nginx o Apache.

```js
res.removeHeader('Server');
```

---

