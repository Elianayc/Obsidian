## Domain Name System

El **DNS (Domain Name System)** es un sistema que permite traducir nombres de dominio fáciles de recordar por las personas en **direcciones IP** que utilizan los dispositivos para comunicarse en una red.

**Por ejemplo**:

```
www.google.com → 142.250.xxx.xxx
```

Los usuarios utilizan nombres de dominio, pero las computadoras necesitan direcciones IP para localizar los servidores.

---

## Funcionamiento del DNS

El DNS funciona mediante una **jerarquía de servidores** que almacenan información sobre dominios y sus direcciones IP.

Cuando un usuario ingresa una dirección web en el navegador:

1. El navegador consulta al **servidor DNS local** para obtener la dirección IP asociada al dominio.
2. Si el servidor DNS local no tiene la información almacenada, consulta a otros servidores DNS hasta encontrar la respuesta.
3. El servidor DNS devuelve la dirección IP correspondiente.
4. El navegador utiliza esa dirección IP para conectarse al servidor donde se encuentra el recurso solicitado.

---

## Caché y TTL

Para mejorar la velocidad de las consultas, los servidores DNS almacenan temporalmente las respuestas obtenidas.

Este almacenamiento se denomina **caché**.

El tiempo durante el cual una respuesta permanece almacenada se llama **TTL (Time To Live)**.

Gracias a la caché, si varios usuarios consultan el mismo dominio, la respuesta puede entregarse rápidamente sin volver a consultar todos los servidores DNS.

---

## Importancia del DNS

El DNS facilita el uso de Internet porque permite acceder a recursos mediante nombres legibles para humanos en lugar de recordar direcciones IP numéricas.

---

#ProgramaciónIII
#Redes