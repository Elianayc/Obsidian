Los **headers HTTP de seguridad** son encabezados que el servidor envía para indicarle al navegador **cómo debe comportarse** y agregar una capa de protección.

|        **Header**        |                  **Qué hace**                   |         **Protege contra**          |                            **Qué es**                            |                       **Cómo protege**                       |
| :----------------------: | :---------------------------------------------: | :---------------------------------: | :--------------------------------------------------------------: | :----------------------------------------------------------: |
| `X-Content-Type-Options` |     Respeta el tipo de contenido declarado.     |          **MIME sniffing**          |  El navegador intenta interpretar el contenido como otro tipo.   |  `nosniff` evita que el navegador intente adivinar el tipo.  |
|    `X-Frame-Options`     |          Controla el uso de `iframe`.           |          **Clickjacking**           |      El usuario hace clic en algo distinto de lo que cree.       |  Impide o limita que la página sea cargada en un `iframe`.   |
|    `X-XSS-Protection`    |          Mecanismo antiguo contra XSS.          |               **XSS**               |           Se introduce código malicioso en una página.           |  Podía detectar y bloquear algunos XSS. Está **deprecado**.  |
|          `HSTS`          |             Fuerza el uso de HTTPS.             |            **Downgrade**            |    Se intenta utilizar una conexión menos segura, como HTTP.     |          El navegador recuerda que debe usar HTTPS.          |
|          `CSP`           |  Define qué recursos puede cargar o ejecutar.   |    **XSS / inyección de código**    |       Se intenta introducir código o recursos maliciosos.        | El navegador bloquea recursos no permitidos por la política. |
|    `Referrer-Policy`     | Controla qué información se envía en `Referer`. |    **Exposición de información**    |     Se comparte información innecesaria de la URL anterior.      |   Limita la información que se envía al sitio de destino.    |
|   `Permissions-Policy`   |     Controla funcionalidades del navegador.     | **Uso indebido de funcionalidades** | Una página intenta usar cámara, micrófono, geolocalización, etc. |     Permite bloquear o restringir esas funcionalidades.      |
|      `X-Powered-By`      |      Puede revelar el framework utilizado.      |    **Exposición de información**    |         Se muestran tecnologías usadas por el servidor.          |       Se elimina para ocultar información innecesaria.       |
|         `Server`         |     Puede revelar el software del servidor.     |    **Exposición de información**    |         Se muestra información sobre Nginx, Apache, etc.         |     Se puede ocultar para reducir información expuesta.      |

---

