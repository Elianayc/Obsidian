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

- **Peticiones HTTP (Requests)**: mensajes enviados por el cliente, normalmente solicitando un recurso o una operación.
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

---

## Métodos HTTP

Los mensajes HTTP utilizan distintos métodos según la acción que se desea realizar:

- **GET:** solicita o consulta información del servidor.
- **POST:** crea o da de alta un nuevo recurso enviando información al servidor.
- **PUT:** reemplaza o actualiza **completamente** un recurso existente.
- **PATCH:** modifica **parcialmente** un recurso existente.
- **DELETE:** elimina un recurso.

---

## Códigos de respuesta

HTTP utiliza **códigos de estado** para indicar el resultado de una solicitud.

|Código|Significado|Uso|
|---|---|---|
|**200 OK**|Éxito|Operación realizada correctamente|
|**201 Created**|Creado|Recurso creado correctamente|
|**204 No Content**|Sin contenido|Éxito sin contenido en la respuesta|
|**400 Bad Request**|Solicitud incorrecta|Datos inválidos o mal formados|
|**401 Unauthorized**|No autenticado|Faltan credenciales o autenticación|
|**403 Forbidden**|Prohibido|El cliente está autenticado pero no tiene permisos|
|**404 Not Found**|No encontrado|El recurso solicitado no existe|
|**500 Internal Server Error**|Error interno|Error no controlado en el servidor|

Los códigos se agrupan en cinco categorías:

- **1xx** → respuestas informativas.
- **2xx** → solicitudes exitosas.
- **3xx** → redirecciones.
- **4xx** → errores del cliente.
- **5xx** → errores del servidor.

---

## HTTPS

**HTTPS (HyperText Transfer Protocol Secure)** es la versión segura de HTTP. Permite transmitir información entre el cliente y el servidor de forma **cifrada**.

HTTPS utiliza **TLS (Transport Layer Security)** para proteger la comunicación.

### ¿Qué garantiza HTTPS?
- **Cifrado:** la información viaja cifrada entre el cliente y el servidor.
- **Integridad:** evita que los datos sean modificados durante la comunicación.
- **Autenticación:** permite verificar la identidad del servidor mediante certificados digitales.

### HTTP vs HTTPS

|HTTP|HTTPS|
|---|---|
|Comunicación sin cifrado|Comunicación cifrada|
|Menor seguridad|Mayor seguridad|
|Utiliza HTTP|HTTP + TLS|

**HTTPS es especialmente importante cuando se transmiten datos sensibles**, como contraseñas, información personal o datos de pago.

---

