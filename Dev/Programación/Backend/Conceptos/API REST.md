Una **API REST** es una API diseñada siguiendo los principios del estilo arquitectónico **REST (Representational State Transfer)**.
Permite que distintos sistemas se comuniquen mediante HTTP y accedan a recursos del backend.

### Conceptos relacionados

- [[Arquitectura REST]]
- [[Diseño de APIs REST]]
- [[Seguridad de APIs REST]]

---

# Diseño de APIs REST

El diseño de una **API REST** busca crear servicios **mantenibles, escalables y fáciles de utilizar**.

A diferencia de la arquitectura REST, que explica **los principios generales**, este apartado se centra en **cómo aplicar esos principios al diseñar una API**.

---

## Recursos y URLs

En REST, las URLs representan **recursos o entidades**, no acciones.

### Principios

- **Identificación:** cada recurso se identifica mediante una URL.
    
- **Sustantivos, no verbos:** las URLs representan entidades, no operaciones.
    
- **Jerarquía lógica:** las relaciones entre recursos pueden reflejarse en la URL.
    
- **Colecciones e instancias:** se diferencia entre una colección y un recurso individual.
    

### Ejemplo

```text
/usuarios
/usuarios/123
/usuarios/123/pedidos
```

- `/usuarios` → colección de usuarios.
    
- `/usuarios/123` → usuario específico.
    
- `/usuarios/123/pedidos` → colección de pedidos del usuario 123.
    

La URL permite identificar directamente el recurso solicitado. No es necesario realizar previamente las otras solicitudes.

### Acciones mediante HTTP

La acción se determina mediante el **método HTTP**, no mediante el nombre de la URL.

```http
GET /usuarios/123
```

→ Obtener el usuario.

```http
DELETE /usuarios/123
```

→ Eliminar el usuario.

Por eso se prefieren rutas como:

```text
/usuarios/123
```

en lugar de rutas orientadas a acciones como:

```text
/obtenerUsuario/123
/getUser/123
```

Este último enfoque se aproxima al estilo **RPC**, donde las operaciones se expresan como acciones.

---

## Métodos HTTP

Los métodos HTTP permiten indicar qué operación se desea realizar sobre un recurso.

|Método|Uso habitual|
|---|---|
|`GET`|Obtener un recurso|
|`POST`|Crear un recurso|
|`PUT`|Reemplazar o actualizar un recurso|
|`PATCH`|Modificar parcialmente un recurso|
|`DELETE`|Eliminar un recurso|

---

## Idempotencia

Una operación es **idempotente** cuando realizarla una o varias veces produce el mismo efecto final sobre el recurso.

Por ejemplo, realizar varias veces:

```http
PUT /usuarios/123
```

con los mismos datos debería dejar al usuario en el mismo estado final.

La idempotencia es importante para diseñar APIs predecibles y seguras frente a reintentos.

---

## Versionado

El versionado permite evolucionar una API sin romper los clientes existentes.

Una estrategia habitual es incluir la versión en la URL:

```text
/api/v1/usuarios
/api/v2/usuarios
```

Esto permite mantener diferentes versiones durante un período de transición y comunicar claramente los cambios entre versiones.

---

## Idea central

> **Arquitectura REST explica los principios que caracterizan a REST. Diseño de API REST explica cómo aplicar esos principios al construir las rutas, recursos y operaciones concretas de una API.**