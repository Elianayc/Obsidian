El **Rate Limiting** y el **Throttling** permiten controlar la cantidad y velocidad de solicitudes que recibe una API, ayudando a proteger su disponibilidad y estabilidad.

---

## Rate Limiting

El **rate limiting** limita la cantidad máxima de requests que un cliente puede realizar durante un período determinado.

El límite puede establecerse, por ejemplo, por **IP o usuario**.


#### Objetivos

- Prevenir ataques **DoS (Denial of Service)**.
- Evitar abusos de la API.
- Garantizar la disponibilidad del servicio.
- Distribuir los recursos de manera equitativa.

##### Ejemplo

```js
const rateLimit = require('express-rate-limit');

const limiter = rateLimit({
  windowMs: 15 * 60 * 1000,
  max: 100,
  message: 'Demasiadas solicitudes desde esta IP',
  standardHeaders: true,
  legacyHeaders: false
});

app.use(limiter);
```

En este ejemplo, una IP puede realizar como máximo **100 solicitudes cada 15 minutos**.

---

## Throttling

El **throttling** controla la **velocidad a la que se procesan las solicitudes**, evitando que el servidor reciba o procese requests demasiado rápidamente.

#### Objetivos

- Mantener la estabilidad del servidor.
- Optimizar el uso de recursos.
- Evitar picos excesivos de tráfico.
- Mantener una buena experiencia para los usuarios.

---

### Diferencia

- **Rate Limiting:** controla **cuántas solicitudes** puede realizar un cliente durante un período determinado.
- **Throttling:** controla **a qué velocidad** se procesan o permiten las solicitudes.

---

## Estrategias de implementación


### Fixed Window
Utiliza un contador que se reinicia al comenzar cada período.

Por ejemplo:
```
100 requests cada 15 minutos
```


### Sliding Window
Utiliza una **ventana de tiempo deslizante**, permitiendo un control más preciso de las solicitudes a lo largo del tiempo.


### Token Bucket
Utiliza un sistema de **tokens que se reponen gradualmente**.

Cada request consume un token. Si no quedan tokens disponibles, la solicitud debe esperar o ser rechazada.

---
