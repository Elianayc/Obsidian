**REST (Representational State Transfer)** es un **estilo arquitectónico** para sistemas distribuidos basado en los principios fundamentales de la Web.

Fue definido por **Roy Fielding** en su tesis doctoral de 2000.

REST organiza la comunicación alrededor de **recursos**, que pueden ser identificados mediante una URL, y permite transferir representaciones de esos recursos utilizando una **interfaz uniforme**, generalmente mediante **HTTP**.

![[Pasted image 20260821122155.png]]

---

## Características

### Basada en recursos
Todo se representa como un **recurso** identificable mediante una URL.

Por ejemplo:

/books
/books/15
/authors/3

### Interfaz uniforme
Utiliza los métodos HTTP estándar con significados bien definidos:

- **GET** → consultar información.
- **POST** → crear un nuevo recurso.
- **PUT** → reemplazar o actualizar un recurso completo.
- **DELETE** → eliminar un recurso.

### Sin estado (_Stateless_)
Cada solicitud debe contener toda la información necesaria para que el servidor pueda procesarla.

El servidor **no debe depender del estado de solicitudes anteriores** del cliente.

### Sistema por capas
La comunicación puede incluir componentes intermedios, como **proxies** o **gateways**, que pueden gestionar o transformar las comunicaciones sin que el cliente tenga que conocerlos.

### Representaciones múltiples
Un mismo recurso puede representarse en diferentes formatos, por ejemplo:

- **JSON**
- **XML**
- **HTML**

### HATEOAS
**HATEOAS (Hypermedia as the Engine of Application State)** permite que las respuestas incluyan enlaces que indiquen al cliente qué acciones o recursos puede consultar a continuación.

---

## Ventajas

- **Escalabilidad:** el diseño sin estado facilita la distribución de solicitudes entre servidores.
- **Simplicidad:** utiliza estándares y protocolos web ampliamente conocidos.
- **Portabilidad:** es independiente del lenguaje de programación y de la plataforma.
- **Visibilidad:** las solicitudes pueden ser comprendidas y gestionadas por componentes intermedios.
- **Evolución independiente:** cliente y servidor pueden evolucionar de forma independiente.

---

## Desventajas

- **Sobrecarga de red:** algunas operaciones complejas pueden requerir múltiples solicitudes.
- **Granularidad de recursos:** puede ser difícil determinar el nivel adecuado de división de los recursos.
- **Ausencia de estado:** puede complicar escenarios que necesitan mantener contexto entre solicitudes.
- **Implementaciones inconsistentes:** muchas APIs denominadas REST no cumplen todos los principios de REST.
- **Operaciones por lotes:** no es el enfoque más adecuado para transferencias masivas de datos.

---

# Modelo de Madurez de Richardson

El **Modelo de Madurez de Richardson** permite clasificar las APIs según el grado en que aplican los principios de REST.

### Nivel 0 — HTTP como transporte
Se utiliza HTTP principalmente como medio de transporte para realizar operaciones, de forma similar a **RPC sobre HTTP**.

### Nivel 1 — Recursos
La API comienza a organizarse alrededor de **recursos identificables mediante URLs**.

### Nivel 2 — Verbos HTTP y códigos de estado
Se utilizan correctamente los **métodos HTTP** y los **códigos de estado HTTP** según el resultado de cada operación.

### Nivel 3 — HATEOAS
Las respuestas incluyen **hipermedia**, proporcionando enlaces que indican posibles acciones o recursos relacionados.

![[Pasted image 20260821122410.png]]

---

# Casos de uso

REST resulta especialmente adecuado para:

- **APIs públicas** para consumo externo.
- **Servicios web orientados a recursos.**
- **Integraciones entre sistemas heterogéneos.**
- Aplicaciones móviles que necesitan comunicarse con servidores.
- Comunicación entre servicios en arquitecturas de **microservicios**.

---

> [!example]
> 
> ![[Pasted image 20260821122513.png]]
> 
> Una API de una biblioteca podría organizar sus recursos de la siguiente manera:
> 
> /books
> /books/15
> /authors/3/books
> 
> 
> ### Colección de libros
> GET /books
> POST /books
> 
> - `GET` → obtiene el listado de libros.
> - `POST` → crea un nuevo libro.
> 
> 
> ### Libro específico
> GET /books/15
> PUT /books/15
> DELETE /books/15
> 
> - `GET` → obtiene los datos del libro.
> - `PUT` → actualiza o reemplaza el libro.
> - `DELETE` → elimina el libro.
> 
> 
> ### Libros de un autor
> GET /authors/3/books
> 
> Obtiene los libros asociados al autor `3`.
> 
> En una implementación que utiliza **HATEOAS**, las respuestas pueden incluir enlaces hacia recursos relacionados o acciones disponibles.

---

# API REST vs. API RESTful

Aunque suelen utilizarse como sinónimos, existe una diferencia:

- **API REST completa:** cumple con los principios de REST, incluyendo **HATEOAS (nivel 3)**.
- **API RESTful:** sigue algunos de los principios de REST, generalmente los niveles **1 y 2**, pero no necesariamente todos.

En la práctica, muchas APIs comerciales denominadas **REST** o **RESTful** no implementan HATEOAS.

---

