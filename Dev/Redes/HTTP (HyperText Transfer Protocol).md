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

- **[[Peticiones HTTP (Requests)]]**: mensajes enviados por el cliente, normalmente solicitando un recurso o una operación.
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


> [!question] #### ¿Qué hace HTTPS?
> 
> HTTPS hace que la comunicación entre tu navegador y el servidor sea **cifrada y autenticada** mediante TLS.
> 
> Pensalo así:
> 
> ##### HTTP sin HTTPS
> 
> ```text
> Vos ──────── HTTP ────────→ Servidor
>        "Mi contraseña es 1234"
> ```
> 
> Los datos viajan sin cifrar. Si alguien logra interceptar la comunicación, podría leerlos.
> 
> ##### HTTPS
> 
> ```text
> Vos ──── HTTPS (HTTP + TLS) ────→ Servidor
>               🔒
>        "x7$kP9#..." 
> ```
> 
> TLS cifra los datos antes de enviarlos. Un tercero que los intercepte no debería poder entender su contenido.
> 
> Además, TLS proporciona:
> 
> - **Confidencialidad:** terceros no pueden leer fácilmente los datos transmitidos.
>     
> - **Integridad:** permite detectar si los datos fueron modificados durante el tránsito.
>     
> - **Autenticación del servidor:** mediante certificados digitales, el navegador puede verificar que está comunicándose con el servidor correspondiente al dominio.
>     
> 
> ##### Entonces, ¿qué cambia?
> 
> **HTTP** define **cómo se comunican** cliente y servidor.
> 
> **TLS** protege esa comunicación.
> 
> Por eso:
> 
> > **HTTPS = HTTP funcionando sobre una conexión protegida por TLS.**
> 
> Y algo importante para tu apunte: **HTTPS no es un protocolo completamente diferente de HTTP**. Es HTTP utilizando TLS para proteger la comunicación.

---

## Métodos HTTP

Los **métodos HTTP** indican la **operación que se quiere realizar sobre un recurso**.

Los principales métodos son:

- **GET:** solicita o consulta información del servidor.
- **POST:** crea o da de alta un nuevo recurso enviando información al servidor.
- **PUT:** reemplaza o actualiza **completamente** un recurso existente.
- **PATCH:** modifica **parcialmente** un recurso existente.
- **DELETE:** elimina un recurso.

Estos métodos se relacionan con las operaciones básicas de **CRUD**:

| Método | CRUD | Acción | Descripción |
| :--- | :--- | :--- | :--- |
| `GET` | Read | Leer | Obtener uno o varios recursos |
| `POST` | Create | Crear | Crear un recurso |
| `PUT` | Update | Modificar | Modificar completamente un recurso |
| `PATCH` | Update | Modificar | Modificar parcialmente un recurso |
| `DELETE` | Delete | Eliminar | Eliminar un recurso |

### Ejemplos

```http
GET /api/products
```

Obtiene una lista de productos.

```http
GET /api/products/123
```

Obtiene un producto específico.

```http
POST /api/products
```

Crea un nuevo producto.

```http
PUT /api/products/123
```

Modifica completamente el producto 123.

```http
PATCH /api/products/123
```

Modifica parcialmente el producto 123.

```http
DELETE /api/products/123
```

Elimina el producto 123.

Ver [[Idempotencia]].

---

## Códigos de respuesta

HTTP utiliza **códigos de estado** para indicar el resultado de una solicitud.

Los códigos se agrupan en cinco categorías:

- **1xx** → respuestas informativas.
- **2xx** → solicitudes exitosas.
- **3xx** → redirecciones.
- **4xx** → errores del cliente.
- **5xx** → errores del servidor.

### Principales códigos de estado

|            Código             |      Significado       |                        Uso                         |
| :---------------------------: | :--------------------: | :------------------------------------------------: |
|          **200 OK**           |         Éxito          |         Operación realizada correctamente          |
|        **201 Created**        |         Creado         |            Recurso creado correctamente            |
|      **204 No Content**       |     Sin contenido      |  Operación exitosa sin contenido en la respuesta   |
|      **400 Bad Request**      |  Solicitud incorrecta  |           Datos inválidos o mal formados           |
|     **401 Unauthorized**      |     No autenticado     |        Faltan credenciales o autenticación         |
|       **403 Forbidden**       |       Prohibido        | El cliente está autenticado pero no tiene permisos |
|       **404 Not Found**       |     No encontrado      |          El recurso solicitado no existe           |
| **500 Internal Server Error** |     Error interno      |         Error no controlado en el servidor         |
|  **503 Service Unavailable**  | Servicio no disponible |    El servicio no está disponible temporalmente    |

---

