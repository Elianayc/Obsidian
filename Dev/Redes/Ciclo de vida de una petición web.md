Cuando un usuario ingresa una URL en el navegador, ocurre una serie de pasos para obtener y mostrar el recurso solicitado.

---

## 1. Resolución DNS

El navegador obtiene la **dirección IP** del servidor donde se encuentra el recurso solicitado.
Para esto utiliza **DNS (Domain Name System)**, que traduce un nombre de dominio en una dirección IP.

**Ejemplo:*

`www.ejemplo.com` → `93.184.216.34`


> **Importante:** después de resolver mediante DNS la dirección IP, el siguiente paso es **establecer la conexión TCP con el servidor**.

---

## 2. Establecimiento de la conexión

Una vez obtenida la dirección IP, el navegador establece una conexión con el servidor utilizando **TCP**.
TCP permite transportar los datos de manera confiable y controla su envío para asegurar que lleguen correctamente.

---

## 3. Creación y envío de la petición HTTP

El navegador crea una **petición HTTP** con la información necesaria para comunicarse con el servidor.

La petición puede incluir:

- Recurso solicitado.
- Información del navegador (_User-Agent_).
- Preferencias de idioma y codificación.
- Datos de autenticación si son necesarios.

Luego, la petición HTTP se envía al servidor.

---

## 4. Procesamiento del servidor

El servidor recibe la petición y determina cómo responder.

Puede:
- Entregar un archivo estático como HTML, CSS o una imagen.
- Ejecutar código para generar contenido dinámico.
- Validar autenticación y permisos.

---

## 5. Generación y envío de la respuesta

El servidor genera una **respuesta HTTP** que incluye:

- Recurso solicitado.
- Código de estado HTTP.
- Información adicional mediante _headers_.

Luego envía la respuesta al cliente.

---

## 6. Procesamiento del navegador

El navegador interpreta la respuesta recibida.

Si recibe una página web:
- Procesa **HTML** para crear la estructura.
- Aplica estilos mediante **CSS**.
- Ejecuta **JavaScript** para agregar interacción.

---

## 7. Presentación del recurso

Finalmente, el navegador muestra el contenido solicitado al usuario.

Este proceso se repite cada vez que el navegador solicita un nuevo recurso web.

---

### Resumen

**DNS → TCP → Petición HTTP → Servidor → Respuesta HTTP → Procesamiento → Presentación**

---
