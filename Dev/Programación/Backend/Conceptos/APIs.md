---
tags:
  - ArquitecturadeSistemas
---
**API** significa **Application Programming Interface** (_Interfaz de Programación de Aplicaciones_).

Una API es un **conjunto de reglas, protocolos y mecanismos que permite que diferentes aplicaciones, sistemas o componentes de software se comuniquen entre sí**.

La API define **cómo un sistema puede solicitar información o utilizar determinadas funcionalidades de otro sistema**, sin necesidad de conocer cómo está implementado internamente.

Por ejemplo, un frontend puede comunicarse con un backend mediante una API para:

- Obtener información.
- Crear nuevos datos.
- Modificar datos existentes.
- Eliminar información.
- Ejecutar determinadas operaciones.
    
----

## ¿Cómo funciona?

Una aplicación que necesita utilizar una funcionalidad realiza una **solicitud (request)** a la API.

La API recibe la solicitud, la procesa y devuelve una **respuesta (response)**.

```text
Cliente
   ↓
Solicitud
   ↓
API
   ↓
Sistema / Backend
   ↓
Respuesta
   ↓
Cliente
```

Por ejemplo:

```http
GET /usuarios/123
```

El cliente solicita información sobre el usuario `123`.

La API procesa la solicitud y puede devolver:

```json
{
  "id": 123,
  "nombre": "Eli"
}
```

---

## API como intermediario

La API funciona como un **punto de comunicación entre diferentes sistemas**.

Por ejemplo:

```text
Frontend
    ↓
   API
    ↓
Backend
    ↓
Base de datos
```

El frontend no necesita acceder directamente a la base de datos. Se comunica con el backend mediante la API.

Esto permite **separar responsabilidades** y controlar qué información y funcionalidades pueden utilizar los distintos clientes.

---

## Características

- **Interoperabilidad:** permite que sistemas diferentes se comuniquen entre sí.
- **Abstracción:** el cliente no necesita conocer la implementación interna del sistema.
- **Reutilización:** una misma API puede ser utilizada por diferentes aplicaciones.
- **Control de acceso:** permite definir qué operaciones y datos están disponibles.
- **Separación de responsabilidades:** cada sistema puede encargarse de una parte específica del proceso.
- **Estandarización:** establece una forma definida de comunicación entre los componentes.
    
---

## Tipos de APIs

Las APIs pueden clasificarse de diferentes maneras según el criterio utilizado.

Algunas de las más utilizadas son:

- **[[API REST]]:** utilizan los principios de REST y normalmente se comunican mediante HTTP.
    
- **APIs SOAP:** utilizan el protocolo SOAP (_Simple Object Access Protocol_) y suelen utilizar XML para el intercambio de información.
    
- **APIs GraphQL:** permiten que el cliente especifique qué datos necesita obtener.
    
- **APIs internas:** se utilizan dentro de una misma organización o sistema.
    
- **APIs externas:** están disponibles para otros sistemas o desarrolladores.

---

## API y HTTP

Una API no necesariamente tiene que utilizar HTTP. Sin embargo, las APIs web suelen utilizarlo porque permite establecer una comunicación estandarizada entre clientes y servidores.

En una API basada en HTTP, la solicitud puede incluir:

- **Método HTTP:** indica la operación que se desea realizar.
- **URL:** identifica el recurso al que se quiere acceder.
- **Headers:** proporcionan información adicional sobre la solicitud.
- **Body:** contiene datos enviados al servidor cuando corresponde.

La respuesta puede incluir:

- **Código de estado HTTP:** indica el resultado de la operación.
- **Headers:** información adicional sobre la respuesta.
- **Body:** datos devueltos por el servidor.
    

---


