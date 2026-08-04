Cuando un usuario ingresa una URL en el navegador ocurre una serie de pasos: 

--- 

## 1. Resolución de la URL 

El navegador debe obtener la dirección IP del servidor donde se encuentra el recurso solicitado. Para esto utiliza DNS, que traduce un nombre de dominio en una dirección IP. Ejemplo:

---

## 2. Creación de la petición HTTP

Una vez obtenida la dirección IP, el navegador crea una petición HTTP con la información necesaria para comunicarse con el servidor.

La petición puede incluir:

- Recurso solicitado.
- Información del navegador (*User-Agent*).
- Preferencias de idioma y codificación.
- Datos de autenticación si son necesarios.

---

## 3. Envío de la petición

La petición HTTP se envía al servidor utilizando **TCP**, que permite transportar los datos de manera confiable.

TCP divide la información en paquetes, controla su envío y asegura que lleguen correctamente al destino.

---

## 4. Procesamiento del servidor

El servidor recibe la petición y determina cómo responder.

Puede:

- Entregar un archivo estático como HTML, CSS o una imagen.
- Ejecutar código para generar contenido dinámico.
- Validar autenticación y permisos.

---

## 5. Generación y envío de la respuesta

El servidor genera una respuesta HTTP que incluye:

- Recurso solicitado.
- Código de estado HTTP.
- Información adicional mediante headers.

Luego envía la respuesta al cliente.

---

## 6. Procesamiento del navegador

El navegador interpreta la respuesta recibida.

Si recibe una página web:

- Procesa HTML para crear la estructura.
- Aplica estilos mediante CSS.
- Ejecuta JavaScript para agregar interacción.

---

## 7. Presentación del recurso

Finalmente, el navegador muestra el contenido solicitado al usuario.

Este proceso se repite cada vez que un usuario solicita un recurso web.

---

#ProgramaciónIII
#Redes