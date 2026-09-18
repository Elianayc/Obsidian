
**Basic Authentication** es uno de los métodos más simples y comunes de autenticación.

Consiste en enviar un **nombre de usuario y contraseña en cada solicitud**.

---

### Funcionamiento

El cliente combina:

```text
usuario:contraseña
```

y lo codifica mediante **Base64**.

Luego lo envía en el header `Authorization`:

```http
Authorization: Basic <credenciales>
```


##### Cliente

```js
const username = 'usuario';
const password = 'contraseña';

const credentials = btoa(`${username}:${password}`);

fetch('https://api.ejemplo.com/recursos', {
  headers: {
    'Authorization': `Basic ${credentials}`
  }
})
  .then(response => response.json())
  .then(data => console.log(data));
```

##### Servidor
El servidor obtiene el header, decodifica las credenciales y las verifica.

```js
app.use((req, res, next) => {
  const authHeader = req.headers.authorization;

  if (!authHeader || !authHeader.startsWith('Basic ')) {
    res.status(401).json({
      mensaje: 'Autorización requerida'
    });
    return;
  }

  const credenciales = Buffer
    .from(authHeader.split(' ')[1], 'base64')
    .toString()
    .split(':');

  const usuario = credenciales[0];
  const contraseña = credenciales[1];

  if (usuario === 'usuario' && contraseña === 'contraseña') {
    req.usuario = usuario;
    next();
  } else {
    res.status(401).json({
      mensaje: 'Credenciales incorrectas'
    });
  }
});
```

---

#### Ventajas

- Fácil de implementar.
- Compatible con casi todos los clientes HTTP.
    

#### Desventajas

- Las credenciales se envían en cada solicitud.
- **Base64 no es cifrado**, solamente codificación.
- No existe manejo de sesión integrado.
- No es ideal para aplicaciones SPA.

Por eso debe utilizarse junto con **HTTPS** para proteger las credenciales durante el transporte.

---