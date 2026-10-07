Códigos de respuesta HTTP

HTTP utiliza **códigos de estado** para indicar el resultado de una solicitud.

Los códigos se agrupan en cinco categorías:

- **1xx** → respuestas informativas.
- **2xx** → solicitudes exitosas.
- **3xx** → redirecciones.
- **4xx** → errores del cliente.
- **5xx** → errores del servidor.

### Principales códigos de estado

|Código|Significado|Uso|
|---|---|---|
|**200 OK**|Éxito|Operación realizada correctamente|
|**201 Created**|Creado|Recurso creado correctamente|
|**204 No Content**|Sin contenido|Operación exitosa sin contenido en la respuesta|
|**400 Bad Request**|Solicitud incorrecta|Datos inválidos o mal formados|
|**401 Unauthorized**|No autenticado|Faltan credenciales o autenticación|
|**403 Forbidden**|Prohibido|El cliente está autenticado pero no tiene permisos|
|**404 Not Found**|No encontrado|El recurso solicitado no existe|
|**500 Internal Server Error**|Error interno|Error no controlado en el servidor|
|**503 Service Unavailable**|Servicio no disponible|El servicio no está disponible temporalmente|

---

> [https://http.cat/](https://http.cat/)
