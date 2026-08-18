**HTTP (HyperText Transfer Protocol)** es un protocolo de la **capa de aplicación** que permite realizar solicitudes y transferir recursos en la Web.

Es la base de la comunicación entre **clientes** y **servidores** para intercambiar información como:

- Documentos HTML.
- Imágenes.
- Videos.
- Datos enviados mediante formularios.

---

## Funcionamiento

La comunicación HTTP se realiza mediante el intercambio de mensajes:

- **[[Peticiones HTTP (Requests)]]:** mensajes enviados por el cliente, normalmente un navegador web, solicitando un recurso.

- **Respuestas:** mensajes enviados por el servidor con el recurso solicitado o información sobre el resultado de la solicitud.

A diferencia de otros sistemas de comunicación que utilizan flujos continuos de datos (*streams*), HTTP trabaja mediante mensajes individuales de solicitud y respuesta.

---

## Relación con otros protocolos

HTTP funciona sobre el protocolo **TCP**, que permite la comunicación confiable entre dispositivos.

Cuando la comunicación utiliza **TLS** para cifrar los datos aparece **[[HTTPS]]**, una versión segura de HTTP.

---

## Métodos HTTP

Los mensajes HTTP pueden utilizar distintos métodos según la acción que se quiera realizar:

- **GET:** solicita o consulta información del servidor.
- **POST:** crea o da de alta un nuevo recurso enviando información al servidor.
- **PUT:** reemplaza o actualiza **completamente** un recurso existente.
- **PATCH:** modifica **parcialmente** un recurso existente.
- **DELETE:** elimina un recurso.

---

## Códigos de respuesta

HTTP utiliza códigos de estado para indicar el resultado de una solicitud.

Ejemplos:

- **200 OK:** la solicitud se realizó correctamente.
- **404 Not Found:** el recurso solicitado no fue encontrado.

---
