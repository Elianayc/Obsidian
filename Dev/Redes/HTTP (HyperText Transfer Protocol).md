**HTTP (HyperText Transfer Protocol)** es un protocolo de la **capa de aplicación** que permite realizar solicitudes y transferir recursos a través de la Web.

Es la base de la comunicación entre **clientes y servidores** para intercambiar información como:

- Documentos HTML.
- Imágenes.
- Videos.
- Datos enviados mediante formularios.
- Datos en formatos como JSON.

---

## Funcionamiento

La comunicación HTTP se realiza mediante un intercambio de **mensajes**:

- **Peticiones HTTP (Requests):** mensajes enviados por el cliente, normalmente solicitando un recurso o una operación.
- **Respuestas HTTP (Responses):** mensajes enviados por el servidor con el recurso solicitado o información sobre el resultado de la solicitud.

El funcionamiento básico es:

```
Cliente → Petición HTTP → Servidor
Cliente ← Respuesta HTTP ← Servidor
```

HTTP trabaja mediante mensajes individuales de **solicitud y respuesta**, en lugar de mantener un flujo continuo de datos (_stream_).

---

## Relación con otros protocolos

HTTP funciona sobre protocolos de transporte como **TCP**, que proporciona una comunicación confiable entre dispositivos.

Cuando HTTP utiliza **TLS** para cifrar la comunicación, se obtiene **HTTPS (HTTP Secure)**.

```
HTTP + TLS = HTTPS
```

#### ¿Qué hace HTTPS?

HTTPS hace que la comunicación entre tu navegador y el servidor sea **cifrada y autenticada** mediante TLS.

Pensalo así:

##### HTTP sin HTTPS

```
Vos ──────── HTTP ────────→ Servidor
       "Mi contraseña es 1234"
```

Los datos viajan sin cifrar. Si alguien logra interceptar la comunicación, podría leerlos.

##### HTTPS

```
Vos ──── HTTPS (HTTP + TLS) ────→ Servidor
              🔒
       "x7$kP9#..."
```

TLS cifra los datos antes de enviarlos. Un tercero que los intercepte no debería poder entender su contenido.

Además, TLS proporciona:

- **Confidencialidad:** terceros no pueden leer fácilmente los datos transmitidos.
- **Integridad:** permite detectar si los datos fueron modificados durante el tránsito.
- **Autenticación del servidor:** mediante certificados digitales, el navegador puede verificar que está comunicándose con el servidor correspondiente al dominio.

##### Entonces, ¿qué cambia?

**HTTP** define **cómo se comunican** cliente y servidor.

**TLS** protege esa comunicación.

Por eso:

> **HTTPS = HTTP funcionando sobre una conexión protegida por TLS.**

HTTPS no es un protocolo completamente diferente de HTTP. Es HTTP utilizando TLS para proteger la comunicación.

---

- [[Métodos HTTP]]
- [[Códigos de Respuesta HTTP]]
- [[HTTP en NestJS (Controller y endpoints)]]

---

