Una operación es **idempotente** cuando ejecutarla varias veces con los mismos datos produce el **mismo estado final** que ejecutarla una sola vez.

> **Importante:** idempotencia no significa que siempre se devuelvan exactamente los mismos datos. Significa que repetir la operación no continúa modificando el estado del recurso.

---

## Métodos idempotentes

### GET

`GET` se utiliza para **obtener información** y no modifica el recurso.

```http
GET /api/products/123
```

Si hacemos el mismo `GET` varias veces y nadie modifica el producto entre las solicitudes, obtendremos el mismo estado del recurso.

```text
GET → producto 123
GET → producto 123
GET → producto 123
```

> Si otro proceso modifica el producto entre dos solicitudes, el segundo `GET` puede devolver datos diferentes. Esto no contradice la idempotencia: `GET` no fue quien modificó el recurso.

---

### PUT

`PUT` reemplaza o establece **completamente** el estado de un recurso.

```http
PUT /api/products/123
```

```json
{
  "nombre": "Mouse",
  "precio": 100
}
```

Primera ejecución:

```text
Producto 123 → Mouse, $100
```

Si ejecutamos exactamente la misma operación nuevamente:

```text
Producto 123 → Mouse, $100
```

Y aunque la ejecutemos diez veces, el estado final continúa siendo el mismo.

Por eso `PUT` es idempotente.

> Lo importante no es que `PUT` siempre coloque los mismos datos, sino que **repetir la misma operación con los mismos datos deja el recurso en el mismo estado final**.

---

### DELETE

`DELETE` elimina un recurso.

```http
DELETE /api/products/123
```

Primera ejecución:

```text
Producto 123 → eliminado
```

Si volvemos a ejecutar:

```http
DELETE /api/products/123
```

el producto ya estaba eliminado, por lo que no se produce un cambio adicional en el estado final.

```text
Producto 123 → inexistente
```

Por eso `DELETE` es idempotente.

---

## Métodos no idempotentes

### POST

`POST` normalmente se utiliza para **crear nuevos recursos**.

```http
POST /api/products
```

```json
{
  "nombre": "Mouse"
}
```

Primera ejecución:

```text
Producto 124 → Mouse
```

Si repetimos exactamente el mismo `POST`:

```text
Producto 125 → Mouse
```

Se creó otro recurso.

Por lo tanto, repetir el mismo `POST` puede producir un efecto adicional cada vez.

> **POST no es idempotente.**

---

### PATCH

`PATCH` permite **modificar parcialmente un recurso**.

A diferencia de `PUT`, la idempotencia de `PATCH depende de la operación concreta que se realice**.

#### PATCH idempotente

Por ejemplo:

```http
PATCH /api/products/123
```

```json
{
  "precio": 110
}
```

Primera ejecución:

```text
$100 → $110
```

Segunda ejecución:

```text
$110 → $110
```

Repetir la operación no continúa modificando el recurso.

En este caso, el `PATCH` es idempotente.

#### PATCH no idempotente

Ahora imaginemos un `PATCH` que indique:

```json
{
  "operacion": "incrementarPrecio",
  "cantidad": 10
}
```

Primera ejecución:

```text
$100 → $110
```

Segunda ejecución:

```text
$110 → $120
```

Tercera ejecución:

```text
$120 → $130
```

Cada ejecución vuelve a modificar el recurso.

En este caso, el `PATCH` no es idempotente.

> **PATCH puede ser idempotente o no, dependiendo de la operación que implemente.**

---

## Resumen

|Método|¿Idempotente?|Motivo|
|---|---|---|
|`GET`|Sí|Obtener un recurso no modifica su estado.|
|`PUT`|Sí|Repetir el mismo reemplazo deja el mismo estado final.|
|`DELETE`|Sí|Una vez eliminado, repetir la eliminación no cambia el estado final.|
|`POST`|No|Repetirlo puede crear nuevos recursos.|
|`PATCH`|Depende|Puede establecer un valor o realizar una operación acumulativa.|

### Idea clave

> **Idempotencia = repetir la misma operación no continúa cambiando el estado final del recurso.**

No significa que el request tenga que devolver exactamente la misma respuesta ni que el recurso nunca pueda cambiar por otras acciones externas.