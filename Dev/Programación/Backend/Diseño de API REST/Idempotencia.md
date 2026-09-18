Una operación es **idempotente** si ejecutarla varias veces produce el mismo efecto que ejecutarla una sola vez.

---

### Métodos idempotentes

|Método|Comportamiento|
|---|---|
|`GET`|Siempre retorna los mismos datos|
|`PUT`|Reemplaza completamente el recurso|
|`DELETE`|Eliminar algo que ya fue eliminado no cambia el estado|

---

### Métodos no idempotentes

|Método|Comportamiento|
|---|---|
|`POST`|Cada llamada puede crear un nuevo recurso|
|`PATCH`|Puede tener efectos diferentes dependiendo del estado actual|

##### Ejemplo

Si ejecutamos:

```http
POST /api/products
```

dos veces, cada llamada puede crear un nuevo producto.

En cambio:

```http
DELETE /api/products/123
```

puede ejecutarse nuevamente sin producir un efecto adicional una vez eliminado el recurso.

---