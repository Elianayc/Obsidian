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

```
/usuarios
/usuarios/123
/usuarios/123/pedidos
```

- `/usuarios` → colección de usuarios.
- `/usuarios/123` → usuario específico.
- `/usuarios/123/pedidos` → colección de pedidos del usuario 123.

La URL permite identificar directamente el recurso solicitado. No es necesario realizar previamente las otras solicitudes.

---

### Acciones mediante HTTP

La acción se determina mediante el **método HTTP**, no mediante el nombre de la URL.

```
GET /usuarios/123
```

→ Obtener el usuario.

```
DELETE /usuarios/123
```

→ Eliminar el usuario.

Por eso se prefieren rutas como:

```
/usuarios/123
```

en lugar de rutas orientadas a acciones como:

```
/obtenerUsuario/123
/getUser/123
```

Este último enfoque se aproxima al estilo **RPC**, donde las operaciones se expresan como acciones.

---

## Métodos HTTP

Los métodos HTTP permiten indicar qué operación se desea realizar sobre un recurso.

|  Método  |            Uso habitual            |
| :------: | :--------------------------------: |
|  `GET`   |         Obtener un recurso         |
|  `POST`  |          Crear un recurso          |
|  `PUT`   | Reemplazar o actualizar un recurso |
| `PATCH`  | Modificar parcialmente un recurso  |
| `DELETE` |        Eliminar un recurso         |

---

#### Conceptos Relacionados

- [[Idempotencia]]
- [[Versionado de APIs REST]]
