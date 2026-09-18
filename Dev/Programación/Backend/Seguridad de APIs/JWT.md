**JWT (JSON Web Token)** es un estándar abierto definido en el **RFC 7519**.

Permite transmitir información de forma **compacta y autónoma** entre partes mediante un objeto JSON.

Es especialmente utilizado para implementar autenticación en APIs REST.

---

### Estructura de un JWT

Un JWT está compuesto por **tres partes separadas por puntos**:

```text
Header.Payload.Signature
```

#### 1. Header

Contiene información sobre:

- Tipo de token.
    
- Algoritmo utilizado para la firma.
    

#### 2. Payload

Contiene las **claims**, es decir, información sobre el usuario o el contexto del token.

Por ejemplo:

```json
{
  "id": 1,
  "usuario": "usuario",
  "rol": "usuario"
}
```

#### 3. Signature

Es la firma utilizada para verificar que el token **no haya sido manipulado**.

> El payload está codificado en Base64URL, pero **no está cifrado por defecto**. Su contenido puede ser leído por quien tenga el token.

---

### Funcionamiento

El flujo básico es:

1. El usuario envía sus credenciales al endpoint de login.
    
2. El servidor verifica las credenciales.
    
3. Si son correctas, genera un JWT.
    
4. El servidor devuelve el token al cliente.
    
5. El cliente almacena el token.
    
6. En las solicitudes posteriores, el cliente envía el token.
    
7. El servidor verifica el token.
    
8. Si es válido, permite acceder al recurso protegido.
    
---

### Generación del token

```js
const SECRET_KEY = 'clave_secreta_muy_segura';

app.post('/login', (req, res) => {
  const { usuario, contraseña } = req.body;

  if (usuario === 'usuario' && contraseña === 'contraseña') {

    const token = jwt.sign(
      {
        id: 1,
        usuario,
        rol: 'usuario'
      },
      SECRET_KEY,
      {
        expiresIn: '1h'
      }
    );

    res.json({ token });

  } else {
    res.status(401).json({
      mensaje: 'Credenciales incorrectas'
    });
  }
});
```

En producción, la clave secreta debe almacenarse mediante **variables de entorno**, no directamente en el código.

---

### Middleware de autenticación

Las rutas protegidas pueden utilizar un middleware que verifique el token:

```js
function verificarToken(req, res, next) {

  const authHeader = req.headers.authorization;

  if (!authHeader || !authHeader.startsWith('Bearer ')) {
    return res.status(401).json({
      mensaje: 'Token requerido'
    });
  }

  const token = authHeader.split(' ')[1];

  try {

    const decoded = jwt.verify(token, SECRET_KEY);

    req.usuario = decoded;

    next();

  } catch (error) {

    return res.status(401).json({
      mensaje: 'Token inválido'
    });
  }
}
```

Una ruta protegida puede utilizar este middleware:

```js
app.get('/recursos', verificarToken, (req, res) => {

  res.json({
    mensaje: 'Acceso autorizado',
    usuario: req.usuario
  });

});
```

##### Cliente

Para iniciar sesión:

```js
fetch('https://api.ejemplo.com/login', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    usuario: 'usuario',
    contraseña: 'contraseña'
  })
})
  .then(response => response.json())
  .then(data => {
    localStorage.setItem('token', data.token);
  });
```

Luego, para acceder a un recurso protegido:

```js
fetch('https://api.ejemplo.com/recursos', {
  headers: {
    'Authorization': `Bearer ${localStorage.getItem('token')}`
  }
})
  .then(response => response.json())
  .then(data => console.log(data));
```

---

#### Ventajas

- **Stateless:** el servidor no necesita mantener sesiones.
- **Escalable:** resulta adecuado para arquitecturas distribuidas.
- **Firmado:** permite verificar que el token no haya sido manipulado.
- **Flexible:** el payload puede contener distintas claims.
- Adecuado para aplicaciones **SPA y móviles**.
    

#### Desventajas

- Los tokens pueden ser más grandes que las cookies.
- El payload es visible porque está codificado, no cifrado.
- La revocación requiere mecanismos adicionales.
- Si se compromete el secreto de firma, los tokens que dependan de ese secreto quedan comprometidos.

---

