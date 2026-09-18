El **Rate Limiting** y el **Throttling** son mecanismos utilizados para controlar las solicitudes que recibe una API y evitar que un cliente genere un exceso de tráfico.

Ayudan a proteger la **disponibilidad, estabilidad y rendimiento** del servidor.

---

## Rate Limiting

El **Rate Limiting** establece un **límite máximo de solicitudes** que un cliente puede realizar durante un período determinado.

El límite puede establecerse, por ejemplo, por **IP, usuario o API Key**.

### Ejemplo

Una API puede establecer la siguiente regla:

```text
Máximo: 100 requests
Período: 15 minutos
Cliente: una determinada IP
```

Si una IP realiza 100 solicitudes dentro de esos 15 minutos, las siguientes solicitudes pueden ser rechazadas hasta que se renueve el límite.

### Objetivos

- Prevenir o reducir el impacto de ataques **DoS (Denial of Service)**.
    
- Evitar abusos de la API.
    
- Proteger los recursos del servidor.
    
- Garantizar la disponibilidad del servicio.
    
- Distribuir los recursos entre los clientes.
    

### Ejemplo en Express

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

En este ejemplo:

- `windowMs` → establece una ventana de **15 minutos**.
    
- `max` → permite como máximo **100 solicitudes** dentro de esa ventana.
    
- `message` → mensaje que se devuelve cuando se supera el límite.
    
- `app.use(limiter)` → aplica el límite a las solicitudes de la aplicación.
    

---

## Throttling

El **Throttling** controla la **velocidad a la que se permiten o procesan las solicitudes**.

En lugar de limitar únicamente cuántas solicitudes puede realizar un cliente, busca evitar que lleguen o se procesen **demasiadas solicitudes de manera demasiado rápida**.

Por ejemplo, un servidor podría permitir como máximo:

```text
5 requests por segundo
```

Si llegan muchas solicitudes juntas, el sistema puede **ralentizarlas, ponerlas en espera o rechazarlas**, según la implementación.

### Objetivos

- Evitar picos excesivos de tráfico.
    
- Mantener la estabilidad del servidor.
    
- Controlar el consumo de recursos.
    
- Evitar que un cliente monopolice la capacidad de procesamiento.
    

---

## Diferencia entre Rate Limiting y Throttling

La forma más sencilla de diferenciarlos es:

> **Rate Limiting → cuántas solicitudes se permiten.**
> 
> **Throttling → qué tan rápido se permiten o procesan.**

Ambos conceptos están relacionados y, en algunas implementaciones, pueden utilizarse de manera conjunta.

---

## Estrategias de implementación

Existen diferentes algoritmos para controlar las solicitudes.

### Fixed Window

Divide el tiempo en **períodos fijos** y utiliza un contador para cada período.

Por ejemplo:

```text
10:00 ─────────────── 10:15
       máximo 100 requests

10:15 ─────────────── 10:30
       vuelve a permitir 100 requests
```

El contador se reinicia al comenzar cada período.

**Idea clave:** períodos fijos + contador.

---

### Sliding Window

En lugar de utilizar períodos fijos, considera una **ventana de tiempo que se desplaza continuamente**.

Por ejemplo, con un límite de 100 requests cada 15 minutos, el sistema analiza siempre los **últimos 15 minutos**.

```text
10:00 ───────────────── 10:15
        ventana

10:01 ───────────────── 10:16
         ventana desplazada
```

Esto permite un control más preciso de las solicitudes a lo largo del tiempo.

**Idea clave:** la ventana se desplaza con el tiempo.

---

### Token Bucket

Utiliza un sistema de **tokens que se van reponiendo gradualmente**.

Cada solicitud consume un token.

Por ejemplo, si tenemos 5 tokens:

```text
🪙 🪙 🪙 🪙 🪙
```

Cada request consume uno:

```text
Request → 🪙
Request → 🪙
Request → 🪙

Quedan:

🪙 🪙
```

Los tokens se vuelven a generar con el tiempo.

Si no quedan tokens disponibles, una solicitud puede **esperar o ser rechazada**, dependiendo de la implementación.

Esto permite soportar pequeños picos de solicitudes mientras existan tokens disponibles, pero limita el tráfico sostenido.

**Idea clave:** tokens que se consumen y se reponen.

---

## Resumen

|Concepto|¿Qué controla?|Ejemplo|
|---|---|---|
|**Rate Limiting**|Cantidad de solicitudes|100 requests cada 15 minutos|
|**Throttling**|Velocidad de las solicitudes|5 requests por segundo|
|**Fixed Window**|Solicitudes dentro de períodos fijos|100 cada 15 minutos|
|**Sliding Window**|Solicitudes dentro de una ventana móvil|Últimos 15 minutos|
|**Token Bucket**|Solicitudes según tokens disponibles|5 tokens que se reponen gradualmente|

### Idea clave

> **Rate Limiting limita la cantidad de solicitudes; Throttling controla la velocidad a la que se permiten o procesan.**