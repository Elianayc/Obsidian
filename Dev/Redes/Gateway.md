Un **gateway** es un **servidor que actúa como puerta de entrada entre los clientes y uno o varios servicios**.

El cliente realiza una solicitud al gateway y este determina **a qué servicio debe enviarla**. Además de realizar el enrutamiento, puede centralizar funciones que afectan a las solicitudes y respuestas, como autenticación, autorización, seguridad, control del tráfico o transformación de datos.

```
			                       ┌→ Servicio de Usuarios
Cliente → Gateway ───────┼→ Servicio de Productos
			                       └→ Servicio de Pedidos
```

Por ejemplo, en una arquitectura de microservicios, el cliente no necesita conocer directamente la dirección de cada microservicio. Puede comunicarse únicamente con el gateway, y este se encarga de dirigir cada solicitud al servicio correspondiente.

Un gateway puede utilizarse para:

- **Enrutar solicitudes** hacia el servicio correspondiente.
- **Centralizar autenticación y autorización**.
- **Aplicar reglas de seguridad**.
- **Controlar y limitar el tráfico**.
- **Transformar solicitudes o respuestas** cuando sea necesario.
- **Ocultar la estructura interna** de los servicios frente al cliente.

**Diferencia básica:** el **proxy** actúa como intermediario entre un cliente y un servidor; el **gateway** funciona principalmente como una **puerta de entrada y punto de coordinación hacia uno o varios servicios**.

---
