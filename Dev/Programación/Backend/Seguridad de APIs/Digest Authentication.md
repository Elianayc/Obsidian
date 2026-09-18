**Digest Authentication** es una mejora respecto de Basic Authentication.

Utiliza un mecanismo de **desafío-respuesta** para evitar enviar la contraseña directamente.

---

### Funcionamiento

1. El cliente solicita un recurso protegido.
   
2. El servidor responde `401 Unauthorized` con un desafío que contiene:

    - **Nonce:** número utilizado una vez.
    - **Realm:** dominio de autenticación.
    - **Algoritmo de hash:** normalmente MD5.
        
3. El cliente calcula una respuesta utilizando:
    
    - Usuario.
    - Contraseña.
    - Nonce.
    - URI solicitada.
    - Método HTTP.
        
4. El cliente vuelve a enviar la solicitud con la respuesta calculada.
    
5. El servidor verifica la respuesta y concede o rechaza el acceso.
    
---

### Concepto de implementación

El cliente recibe un desafío similar a:

```http
WWW-Authenticate: Digest realm="api.ejemplo.com",
qop="auth",
nonce="abc123",
algorithm=MD5
```

Luego calcula hashes para generar la respuesta.

De forma simplificada:

```text
HA1 = MD5(username:realm:password)

HA2 = MD5(method:digestURI)

response = MD5(HA1:nonce:nc:cnonce:qop:HA2)
```

Finalmente envía la información en:

```http
Authorization: Digest ...
```

---

### Ejemplo simplificado

```js
const authDigest = `Digest username="${usuario}",
realm="${realm}",
nonce="${nonce}",
uri="${url}",
algorithm=MD5,
response="${respuesta}",
qop=${qop},
nc=${nc},
cnonce="${cnonce}"`;

fetch(url, {
  method: 'GET',
  headers: {
    'Authorization': authDigest
  }
});
```

##### Servidor

El servidor genera y almacena nonces:

```js
const nonces = new Map();

const nonce = crypto.randomBytes(16).toString('hex');

nonces.set(nonce, {
  timestamp: Date.now()
});
```

Y envía el desafío:

```js
res.setHeader(
  'WWW-Authenticate',
  `Digest realm="api.ejemplo.com",
   qop="auth",
   nonce="${nonce}",
   algorithm=MD5`
);

res.status(401).json({
  mensaje: 'Autorización requerida'
});
```

Luego verifica que el nonce recibido sea válido y procesa la respuesta Digest.

---

#### Ventajas

- Más segura que Basic Authentication.
- No envía la contraseña directamente.
- Proporciona protección contra ataques de repetición.
    

#### Desventajas

- Mayor complejidad de implementación.
- Utiliza **MD5**, considerado débil actualmente.
- Requiere gestionar nonces.
- Tiene menor compatibilidad con frameworks modernos.
   
---