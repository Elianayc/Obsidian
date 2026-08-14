La **arquitectura cliente-servidor** es un modelo donde dos componentes de software cooperan para realizar una tarea:

- **Cliente:** realiza peticiones.
- **[[Servidor Web]]:** recibe las peticiones y envía respuestas.

La capacidad de procesamiento se distribuye entre clientes y servidores, permitiendo una mejor organización del sistema y una separación clara de responsabilidades.

<div style="text-align: center;">

<iframe width="315" height="560" src="https://www.youtube.com/embed/Bv0W8IoS78I" frameborder="0" allowfullscreen></iframe>

</div>

---

## Ejemplos

Algunas aplicaciones que utilizan este modelo:

- Correo electrónico.
- Servidores de impresión.
- Servidores de archivos.
- [[World Wide Web (WWW)]].

---

## Configuraciones

Un servidor no necesariamente es un único programa, proceso o máquina. Puede tener diferentes configuraciones:

- **1 programa - 1 proceso.**
- **1 programa - N procesos:** permite escalabilidad.
- **N programas - M procesos:** múltiples programas y procesos.

![[Pasted image 20260804121953.png]]

---

## Capas

El esquema más simple del modelo cliente-servidor se conoce como **arquitectura de 2 capas**.

A partir de este modelo pueden desarrollarse arquitecturas con más capas, incorporando componentes como:

- Capa de datos.
- Capa de negocio.
- Capa de seguridad.

Para una explicación más detallada de la separación de responsabilidades por capas ver Arquitectura de Capas.

---

## Ventajas

- **Control centralizado:** el servidor puede gestionar solicitudes de varios clientes al mismo tiempo, centralizando recursos y datos.

- **Escalabilidad:** permite agregar más clientes o servidores sin afectar todo el sistema.

- **Seguridad de los datos:** los servidores pueden incorporar controles de seguridad para proteger información sensible.

---

## Desventajas

- **Único punto de fallo:** si el servidor deja de funcionar, los clientes pueden perder el acceso a los servicios y datos.

- **Dependencia de la red:** problemas de conectividad pueden afectar el rendimiento del sistema.

- **Consumo de recursos:** los servidores necesitan recursos suficientes para atender múltiples clientes, aumentando los costos de infraestructura.

---


