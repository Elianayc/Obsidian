Los **headers HTTP de seguridad** son encabezados que el servidor envía para indicarle al navegador cómo debe comportarse y agregar una capa de protección.

|           **Header**            |                                      **Qué hace para proteger**                                       |                                                           **Contra qué protege**                                                            |
| :-----------------------------: | :---------------------------------------------------------------------------------------------------: | :-----------------------------------------------------------------------------------------------------------------------------------------: |
|    `X-Content-Type-Options`     | Evita que el navegador intente **adivinar o cambiar el tipo de contenido** declarado por el servidor. |                **MIME sniffing:** cuando el navegador intenta interpretar un contenido como un tipo diferente al declarado.                 |
|        `X-Frame-Options`        |                   Impide o limita que una página sea cargada dentro de un `iframe`.                   |        **Clickjacking:** cuando una página maliciosa hace que el usuario haga clic en algo distinto de lo que cree estar clickeando.        |
|       `X-XSS-Protection`        |            Podía detectar y bloquear algunos ataques XSS. Actualmente está **deprecado**.             |          **XSS:** cuando un atacante consigue introducir código malicioso, normalmente JavaScript, dentro de una página legítima.           |
|             `HSTS`              |                      Indica al navegador que debe utilizar **HTTPS** y no HTTP.                       |     **Downgrade:** cuando se intenta hacer que una conexión utilice una versión o protocolo menos seguro, como HTTP en lugar de HTTPS.      |
| `Content-Security-Policy (CSP)` | Indica qué recursos y código puede cargar o ejecutar el navegador y bloquea lo que no esté permitido. |               **XSS / inyección de código:** cuando un atacante intenta introducir o ejecutar código malicioso en una página.               |
|        `Referrer-Policy`        |           Controla qué información de la URL anterior se envía al navegar hacia otro sitio.           |           **Exposición de información:** cuando se envían datos innecesarios sobre la página o URL desde la que viene el usuario.           |
|      `Permissions-Policy`       |                     Permite bloquear o restringir funcionalidades del navegador.                      | **Uso indebido de funcionalidades:** cuando una página intenta utilizar funciones como cámara, micrófono o geolocalización que no necesita. |
|         `X-Powered-By`          |                 Se puede eliminar para no revelar qué framework utiliza el servidor.                  |          **Exposición de información:** revelar tecnologías del servidor puede proporcionar información innecesaria a un atacante.          |
|            `Server`             |                  Se puede ocultar para no revelar qué software utiliza el servidor.                   |    **Exposición de información:** revelar tecnologías como Nginx o Apache proporciona información innecesaria sobre la infraestructura.     |

---


