Los **headers HTTP de seguridad** son encabezados que el servidor envía en la respuesta HTTP para indicarle al navegador cómo debe comportarse y agregar una capa de protección.

Los headers de seguridad son configurados por el servidor y enviados en las respuestas HTTP para indicarle al navegador determinadas reglas de seguridad.

|             **Header**              |                                              **Qué hace para proteger**                                              |                                                              **Contra qué protege**                                                               |
| :---------------------------------: | :------------------------------------------------------------------------------------------------------------------: | :-----------------------------------------------------------------------------------------------------------------------------------------------: |
|    <br>`X-Content-Type-Options`     |      <br>Evita que el navegador intente **adivinar o cambiar el tipo de contenido** declarado por el servidor.       |     **MIME sniffing**<br>El navegador intenta interpretar un contenido como otro tipo para procesarlo de una manera diferente a la esperada.      |
|        <br>`X-Frame-Options`        |                        I<br>mpide o limita que una página sea cargada dentro de un `iframe`.                         |             **Clickjacking** <br>Una página maliciosa hace que el usuario haga clic en algo distinto de lo que cree estar clickeando.             |
|             <br>`HSTS`              |                            <br>Indica al navegador que debe utilizar **HTTPS** y no HTTP.                            |                         **Downgrade** <br>Se intenta hacer que una conexión utilice un protocolo menos seguro, como HTTP.                         |
|       <br>`X-XSS-Protection`        |                  <br>Podía detectar y bloquear algunos ataques XSS. Actualmente está **deprecado**.                  |                                       **XSS** <br>Un atacante introduce código malicioso en una página web.                                       |
| <br>`Content-Security-Policy (CSP)` | <br>Indica qué recursos y código puede cargar o <br>ejecutar el navegador y bloquea los que <br>no están permitidos. |                                                                    <br>**XSS**                                                                    |
|        <br>`Referrer-Policy`        |            <br>Controla qué información de la página o URL anterior se comparte al acceder a otro sitio.             |              **Exposición de información** <br>Se envía información innecesaria sobre la página o URL desde la que viene el usuario.              |
|      <br>`Permissions-Policy`       |                           <br>Permite bloquear o restringir funcionalidades del navegador.                           | **Uso indebido de funcionalidades** <br>Evita que una página utilice funciones como cámara, micrófono o geolocalización cuando no son necesarias. |
|         <br>`X-Powered-By`          |             <br>Se puede **eliminar de la respuesta** para no revelar qué framework utiliza el servidor.             |                        **Exposición de información** <br>Evita revelar a un atacante qué tecnologías utiliza el servidor.                         |
|            <br>`Server`             |              <br>Se puede **ocultar de la respuesta** para no revelar qué software utiliza el servidor.              |                   **Exposición de información** <br>Evita revelar información sobre el software utilizado, como Nginx o Apache.                   |

---

## Ejemplo de uso

Cuando el navegador solicita una página:

```text
Navegador
    ↓
GET /inicio
    ↓
Servidor
    ↓
Respuesta HTTP
```

El servidor puede responder incluyendo headers de seguridad:

```http
HTTP/1.1 200 OK
Content-Type: text/html
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
Strict-Transport-Security: max-age=31536000
Content-Security-Policy: default-src 'self'
```

El navegador recibe esos headers y **aplica las reglas indicadas**.

Por ejemplo:

- `X-Content-Type-Options: nosniff` → no intenta adivinar el tipo de contenido.
- `X-Frame-Options: DENY` → no permite mostrar la página dentro de un `iframe`.
- `Strict-Transport-Security` → recuerda que debe utilizar HTTPS.
- `Content-Security-Policy` → limita qué recursos puede cargar o ejecutar.
    
---

### Ejemplo en Express

En un servidor Express se pueden agregar mediante `res.setHeader()`:

```js
res.setHeader('X-Content-Type-Options', 'nosniff');
res.setHeader('X-Frame-Options', 'DENY');
res.setHeader(
  'Strict-Transport-Security',
  'max-age=31536000'
);
```

Es decir:

> **El servidor configura el header → lo envía en la respuesta → el navegador recibe la regla → el navegador la aplica.**

No son funciones que el programador ejecuta manualmente cada vez que llega un usuario; normalmente se configuran **como parte de la configuración de seguridad del servidor o de la API**.

**Servidor → header → respuesta HTTP → navegador → aplica la regla.**

---

