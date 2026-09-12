Un **proxy** es un **servidor intermediario** que se encuentra entre un cliente y el servidor al que este quiere acceder.

En lugar de comunicarse directamente con el servidor, el cliente envía la solicitud al proxy. El proxy recibe esa solicitud, puede **analizarla, filtrarla o modificarla** y luego la reenvía al servidor correspondiente. Cuando recibe la respuesta, también puede procesarla antes de devolvérsela al cliente.

```
Cliente → Proxy → Servidor
Cliente ← Proxy ← Servidor
```

Un proxy puede utilizarse para:

- **Filtrar solicitudes**, por ejemplo, bloquear determinados accesos.
- **Aplicar reglas de seguridad**.
- **Almacenar respuestas en caché** para evitar solicitudes repetidas.
- **Controlar el tráfico** entre clientes y servidores.
- **Ocultar o proteger** determinados detalles del servidor de destino.

El cliente puede utilizar el proxy sin necesidad de conocer cómo funciona internamente el servidor al que está accediendo.


---

