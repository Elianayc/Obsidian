**REST (Representational State Transfer)** es un **estilo arquitectónico** para sistemas distribuidos basado en los principios fundamentales de la Web.

Fue definido por **Roy Fielding** en su tesis doctoral de 2000.

REST organiza la comunicación alrededor de **recursos**, que pueden ser identificados mediante URLs, y permite transferir representaciones de esos recursos mediante una **interfaz uniforme**, generalmente utilizando HTTP.

---

![[Pasted image 20260821122155.png]]

---

## Características

### Basada en recursos
Todo se organiza alrededor de **recursos**, que representan entidades o conceptos de negocio y pueden identificarse mediante una URL.

```
/books
/books/15
/authors/3/books
```

---

### Interfaz uniforme
Utiliza de manera consistente:

- Métodos HTTP.
- Códigos de estado HTTP.
- Convenciones de nombres para recursos y URLs.

Esto permite que el comportamiento de la API sea **predecible y estándar**.

---

### Sin estado (_Stateless_)
Cada solicitud debe contener toda la información necesaria para ser procesada.
El servidor **no debe depender del estado almacenado de solicitudes anteriores del cliente**.

Esto facilita:

- **Escalabilidad:** cualquier servidor puede procesar cualquier request.
- **Simplicidad:** reduce la necesidad de gestionar sesiones en el servidor.
- **Distribución de carga:** facilita utilizar _load balancers_ para distribuir requests entre servidores.
- **Confiabilidad:** reduce la dependencia del estado almacenado en un servidor específico.

---

### Sistema por capas
La comunicación puede incluir componentes intermedios, como [[Proxy (Servidores)]] o [[Gateway]], sin que el cliente tenga que conocer necesariamente su funcionamiento interno.

---

### Representaciones de recursos
Un recurso puede transmitirse mediante diferentes **representaciones**.

Las más comunes son:

- **JSON**
- **XML**
- **HTML**

Por ejemplo, el mismo usuario puede representarse como:

```json
{
  "id": 123,
  "nombre": "Juan"
}
```

o:

```xml
<usuario>
  <id>123</id>
  <nombre>Juan</nombre>
</usuario>
```

El recurso es el mismo; cambia la **representación utilizada para transmitirlo**.


![[Pasted image 20260912191716.png|831]]

---

### HATEOAS

**HATEOAS (Hypermedia as the Engine of Application State)** permite que las respuestas incluyan enlaces que indican al cliente qué recursos o acciones puede consultar a continuación.

![[Pasted image 20260912191616.png|556]]

---

## Ventajas

- **Escalabilidad:** el diseño sin estado facilita distribuir solicitudes entre servidores.
- **Simplicidad:** utiliza estándares y protocolos web ampliamente conocidos.
- **Portabilidad:** es independiente del lenguaje y la plataforma.
- **Interoperabilidad:** facilita la integración entre sistemas diferentes.
- **Evolución independiente:** cliente y servidor pueden evolucionar de manera independiente.

---

## Desventajas

- **Sobrecarga de red:** algunas operaciones pueden requerir múltiples solicitudes.
- **Granularidad de recursos:** puede ser difícil determinar cómo dividir correctamente los recursos.
- **Ausencia de estado:** puede complicar escenarios que necesitan mantener contexto entre solicitudes.
- **Implementaciones inconsistentes:** muchas APIs denominadas REST no aplican todos los principios de REST.
- **Operaciones por lotes:** no siempre es el enfoque más conveniente para transferencias masivas de datos.

---

# Modelo de Madurez de Richardson

Permite clasificar una API según el grado en que utiliza los principios de REST.

### Nivel 0 — HTTP como transporte
HTTP se utiliza principalmente como medio de transporte, de forma similar a **RPC sobre HTTP**.

### Nivel 1 — Recursos
La API comienza a organizarse alrededor de **recursos identificables mediante URLs**.

### Nivel 2 — Verbos HTTP y códigos de estado
Se utilizan correctamente los **métodos HTTP** y los **códigos de estado HTTP** según el resultado de cada operación.

### Nivel 3 — HATEOAS
Las respuestas incluyen **hipermedia**, proporcionando enlaces hacia posibles acciones o recursos relacionados.

> La mayoría de las APIs comerciales denominadas REST suelen encontrarse en niveles inferiores al nivel 3 y no implementan HATEOAS.

![[Pasted image 20260821122410.png|824]]

---

# Casos de uso

REST resulta especialmente adecuado para:

- APIs públicas.
- Servicios web orientados a recursos.
- Integraciones entre sistemas heterogéneos.
- Aplicaciones móviles que se comunican con servidores.
- Comunicación entre servicios en arquitecturas de microservicios.

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

