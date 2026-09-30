# API REST

**REST** significa **Representational State Transfer** (_Transferencia de Estado Representacional_).

REST es un **estilo arquitectónico** para diseñar sistemas distribuidos y servicios web.

Una **API REST** es una API diseñada siguiendo los principios del estilo arquitectónico **REST**. Generalmente utiliza **HTTP** para permitir que distintos sistemas se comuniquen y accedan a los **recursos** de un servidor.

A diferencia de una API genérica, una API REST sigue una serie de principios y convenciones para organizar la comunicación entre el cliente y el servidor.

```text
Cliente
   ↓ HTTP
API REST
   ↓
Backend
   ↓
Base de datos
```

## Recursos

En REST, la información y las entidades del sistema se representan como **recursos**.

Por ejemplo:

```text
/usuarios
/productos
/pedidos
/categorias
```

Cada URL identifica un tipo de recurso.

También se pueden identificar recursos individuales:

```text
/usuarios/123
/productos/45
/pedidos/890
```

La API permite realizar operaciones sobre estos recursos mediante los métodos HTTP.

## Comunicación mediante HTTP

Las APIs REST suelen utilizar HTTP para realizar operaciones sobre los recursos.

Por ejemplo:

```http
GET /usuarios/123
```

Solicita el usuario `123`.

```http
POST /usuarios
```

Solicita la creación de un nuevo usuario.

```http
PUT /usuarios/123
```

Solicita reemplazar o actualizar el usuario `123`.

```http
DELETE /usuarios/123
```

Solicita eliminar el usuario `123`.

La **URL identifica el recurso**, mientras que el **método HTTP indica la operación** que se quiere realizar.

## Representación de los recursos

REST trabaja con **representaciones** de los recursos.

Por ejemplo, un usuario puede estar almacenado internamente de una determinada manera en el servidor, pero la API puede representarlo mediante JSON:

```json
{
  "id": 123,
  "nombre": "Eli",
  "email": "eli@example.com"
}
```

El cliente trabaja con esta representación y no necesita conocer cómo se almacena internamente la información.

## Principios fundamentales de REST

### Cliente-servidor

El cliente y el servidor tienen responsabilidades separadas.

- El **cliente** se ocupa de la interfaz y de realizar solicitudes.
    
- El **servidor** se ocupa de los datos y de la lógica de negocio.
    

Esta separación permite que ambos puedan evolucionar de manera independiente.

### Stateless

Cada solicitud debe contener la información necesaria para que el servidor pueda procesarla.

El servidor no debería depender del estado almacenado de solicitudes anteriores para interpretar una nueva solicitud.

Esto permite que las solicitudes sean independientes entre sí y facilita la escalabilidad del sistema.

### Cacheable

Las respuestas pueden indicar si pueden almacenarse temporalmente en una **caché**.

Esto permite reutilizar determinadas respuestas y evitar solicitudes innecesarias al servidor.

### Interfaz uniforme

REST busca establecer una forma uniforme y predecible de interactuar con los recursos.

Por ejemplo:

```http
GET /usuarios/123
DELETE /usuarios/123
```

La URL identifica el recurso y el método HTTP define la operación.

### Sistema en capas

El cliente no necesita conocer todos los componentes que existen detrás de la API.

Puede existir una arquitectura como:

```text
Cliente
   ↓
API
   ↓
Servicio
   ↓
Base de datos
```

Cada capa puede encargarse de una responsabilidad diferente.

## REST y JSON

REST **no exige utilizar JSON**.

Sin embargo, JSON es uno de los formatos más utilizados para representar los datos intercambiados entre clientes y servidores.

También pueden utilizarse otros formatos, como XML.

## Códigos de estado HTTP

Las APIs REST utilizan los códigos de estado HTTP para indicar el resultado de una solicitud.

|Código|Significado|
|---|---|
|`200 OK`|Solicitud procesada correctamente|
|`201 Created`|Recurso creado correctamente|
|`204 No Content`|Operación correcta sin contenido para devolver|
|`400 Bad Request`|Solicitud incorrecta|
|`401 Unauthorized`|Falta autenticación válida|
|`403 Forbidden`|No se permite realizar la operación|
|`404 Not Found`|Recurso no encontrado|
|`500 Internal Server Error`|Error interno del servidor|

## Ejemplo completo

Un cliente quiere obtener el usuario `123`:

```http
GET /usuarios/123
```

El servidor puede responder:

```http
200 OK
Content-Type: application/json
```

```json
{
  "id": 123,
  "nombre": "Eli",
  "email": "eli@example.com"
}
```

En este caso:

- `GET` indica la operación.
    
- `/usuarios/123` identifica el recurso.
    
- `200 OK` indica que la solicitud fue procesada correctamente.
    
- `application/json` indica el formato de la representación.
    
- El JSON contiene la representación del usuario.
    

## API REST y arquitectura REST

**REST** es el estilo arquitectónico que define los principios generales.

**API REST** es una API que aplica esos principios para permitir la comunicación entre clientes y servidores.

Por lo tanto, una API puede utilizar HTTP sin necesariamente estar diseñada siguiendo todos los principios de REST.

---

### Conceptos relacionados

- [[Arquitectura REST]]
- [[Diseño de APIs REST]]
- [[Seguridad de APIs REST]]

---