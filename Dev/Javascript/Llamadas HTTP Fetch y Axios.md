Las aplicaciones frontend necesitan comunicarse frecuentemente con un **backend** mediante solicitudes HTTP.

JavaScript ofrece `fetch` como API nativa del navegador, mientras que también existen librerías externas como **Axios**.

---

## Fetch

`fetch` es la **API nativa del navegador** para realizar solicitudes HTTP.

No requiere instalar ninguna librería.

### GET

Se utiliza para obtener información del servidor:

```JavaScript
async function getConversaciones() {
    const response = await fetch('/api/conversaciones');

    if (!response.ok) {
        throw new Error(`Error: ${response.status}`);
    }

    return response.json();
}
```

`fetch()` devuelve una **Promise** que se resuelve con un objeto `Response`.

---

### POST

Se utiliza para enviar información al servidor:

```JavaScript
async function enviarMensaje(conversacionId, texto) {
    const response = await fetch(
        `/api/conversaciones/${conversacionId}/mensajes`,
        {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify({ texto })
        }
    );

    if (!response.ok) {
        throw new Error(`Error: ${response.status}`);
    }

    return response.json();
}
```

En este caso:

- `method` indica el método HTTP.
    
- `headers` proporciona información adicional.
    
- `body` contiene los datos enviados.
    
- `JSON.stringify()` convierte el objeto JavaScript en JSON.
    

---

### `response.ok`

Una característica importante de `fetch` es que **no rechaza automáticamente la Promise cuando el servidor responde con un error HTTP**.

Por ejemplo, una respuesta:

```text
404 Not Found
```

o:

```text
500 Internal Server Error
```

sigue produciendo una respuesta `Response`.

Por eso hay que comprobar:

```JavaScript
if (!response.ok) {
    throw new Error(`Error: ${response.status}`);
}
```

`response.ok` permite comprobar si la respuesta HTTP fue exitosa.

---

### Leer el cuerpo de la respuesta

Para obtener los datos JSON:

```JavaScript
const datos = await response.json();
```

`response.json()` también devuelve una Promise.

También existen:

```JavaScript
response.text()
response.blob()
```

para obtener otros tipos de contenido.

---

## Axios

**Axios** es una librería externa para realizar solicitudes HTTP.

Busca simplificar varias tareas que con `fetch` requieren código adicional.

```JavaScript
import axios from 'axios';
```

Se puede crear una instancia configurada para utilizarla en toda la aplicación:

```JavaScript
const api = axios.create({
    baseURL: 'http://localhost:3000/api',
    headers: {
        Authorization: `Bearer ${getToken()}`
    }
});
```

Esto permite centralizar configuraciones como:

- URL base.
    
- Headers.
    
- Timeouts.
    
- Autenticación.
    

### GET

```JavaScript
const { data } = await api.get('/conversaciones');
```

Axios procesa automáticamente las respuestas JSON, por lo que no es necesario llamar a `response.json()`.

### POST

```JavaScript
const { data: nuevo } = await api.post(
    `/conversaciones/${id}/mensajes`,
    { texto }
);
```

Axios también se encarga de serializar los datos enviados cuando corresponde.

---

## Ventajas de Axios

Entre sus características principales:

- Manejo automático de errores HTTP.
    
- Serialización y parseo automático de JSON.
    
- **Interceptors** para modificar requests y responses de manera centralizada.
    
- Cancelación de requests.
    
- Instancias configurables.
    
- Configuración centralizada de URL base, headers y timeouts.
    

Los **interceptors**, por ejemplo, permiten agregar automáticamente un JWT a las solicitudes sin repetir el código en cada request.

---

## Fetch vs Axios

|Característica|**Fetch**|**Axios**|
|---|---|---|
|Tipo|API nativa|Librería externa|
|Instalación|No requiere|Requiere instalación|
|JSON de respuesta|Hay que llamar `.json()`|Se procesa automáticamente|
|Errores HTTP 4xx/5xx|Hay que comprobar `response.ok`|Los rechaza automáticamente|
|Interceptors|No incorporados|Sí|
|Configuración centralizada|Más manual|Más sencilla|
|Sintaxis|Más verbosa|Más concisa|

---
