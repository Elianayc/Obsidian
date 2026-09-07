
Los métodos HTTP indican la **operación que se quiere realizar sobre un recurso**.

Se relacionan con las operaciones básicas de **CRUD**:

|  Método  |  CRUD  |  Acción   |            Descripción             |
| :------: | :----: | :-------: | :--------------------------------: |
|  `GET`   |  Read  |   Leer    |   Obtener uno o varios recursos    |
|  `POST`  | Create |   Crear   |          Crear un recurso          |
|  `PUT`   | Update | Modificar | Modificar completamente un recurso |
| `PATCH`  | Update | Modificar | Modificar parcialmente un recurso  |
| `DELETE` | Delete | Eliminar  |        Eliminar un recurso         |

##### Ejemplos

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