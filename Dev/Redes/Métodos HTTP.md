Los **métodos HTTP** indican la **operación que se quiere realizar sobre un recurso**.

Los principales métodos son:

- **GET:** solicita o consulta información del servidor.
- **POST:** crea o da de alta un nuevo recurso enviando información al servidor.
- **PUT:** reemplaza o actualiza **completamente** un recurso existente.
- **PATCH:** modifica **parcialmente** un recurso existente.
- **DELETE:** elimina un recurso.

Estos métodos se relacionan con las operaciones básicas de **CRUD**:

|Método|CRUD|Acción|Descripción|
|---|---|---|---|
|`GET`|Read|Leer|Obtener uno o varios recursos|
|`POST`|Create|Crear|Crear un recurso|
|`PUT`|Update|Modificar|Modificar completamente un recurso|
|`PATCH`|Update|Modificar|Modificar parcialmente un recurso|
|`DELETE`|Delete|Eliminar|Eliminar un recurso|

---

### Ejemplos

```
GET /api/products
```

Obtiene una lista de productos.

```
GET /api/products/123
```

Obtiene un producto específico.

```
POST /api/products
```

Crea un nuevo producto.

```
PUT /api/products/123
```

Modifica completamente el producto 123.

```
PATCH /api/products/123
```

Modifica parcialmente el producto 123.

```
DELETE /api/products/123
```

Elimina el producto 123.

---
