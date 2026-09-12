
En una API REST, las URLs identifican **recursos y entidades**, no acciones.

---

### Nombres de recursos basados en sustantivos

Los recursos deben representar **entidades y no acciones**.
Se recomienda utilizar **sustantivos en plural**.

##### Ejemplos correctos

```text
GET /api/products
GET /api/products/123
POST /api/products
PUT /api/products/123
DELETE /api/products/123
```

##### Ejemplos incorrectos

```text
GET /api/getProducts
POST /api/createProduct
GET /api/product/delete/123
```

La acción debe determinarse mediante el **método HTTP**, no mediante el nombre de la URL.

---

### Recursos anidados

Cuando existen relaciones jerárquicas entre recursos, estas pueden representarse mediante URLs anidadas.

Por ejemplo, productos y comentarios:

```text
GET    /api/products/123/comments
POST   /api/products/123/comments
GET    /api/products/123/comments/456
PUT    /api/products/123/comments/456
DELETE /api/products/123/comments/456
```

Estas operaciones permiten:

- Obtener los comentarios del producto 123.
- Crear un comentario para el producto 123.
- Obtener el comentario 456 del producto 123.
- Actualizar el comentario 456.
- Eliminar el comentario 456.

La estructura representa la relación **padre-hijo** entre los recursos.

---