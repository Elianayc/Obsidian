**HTTPS (HyperText Transfer Protocol Secure)** es la versión segura de HTTP. Permite establecer una comunicación protegida entre el cliente y el servidor mediante **SSL/TLS**.

Su objetivo es proteger la información que se transmite por la red.

---

## Características principales

- **Encriptación en tránsito:** protege los datos mientras viajan entre el cliente y el servidor.
- **Autenticidad:** permite verificar que el servidor es quien dice ser.
- **Integridad:** garantiza que los datos no sean alterados durante la transmisión.

---

## Implementación

```js
const https = require('https');
const fs = require('fs');

const options = {
  key: fs.readFileSync('private-key.pem'),
  cert: fs.readFileSync('certificate.pem')
};

https.createServer(options, app).listen(443, () => {
  console.log('Servidor HTTPS ejecutándose en puerto 443');
});
```

---

## Buenas prácticas

- Utilizar certificados SSL/TLS válidos.
- Utilizar certificados de autoridades confiables, como Let's Encrypt.
- Implementar **HSTS (HTTP Strict Transport Security)**.
- Redirigir automáticamente HTTP a HTTPS.
- Utilizar **TLS 1.2 o superior**.

---
