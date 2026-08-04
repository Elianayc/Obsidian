---
tags:
  - Modeladodesistemas
---
Muestran cómo se comunican los objetos en el tiempo.  
Lo importante es el **orden de los mensajes**.  
Se usan para entender qué ocurre paso a paso cuando sucede una acción.

![[diagramadesecuencia.png]]


### Elementos principales

#### Línea de vida (Lifeline)
Representa un objeto participante.

###### **Se dibuja como:**
- Nombre del objeto arriba
- Línea vertical punteada hacia abajo

El tiempo avanza **de arriba hacia abajo**.


#### Activación
Rectángulo vertical sobre la línea de vida.  
Indica que el objeto está ejecutando una acción.


#### Mensajes
Flechas entre objetos.

##### Tipos de mensajes:
- **Mensaje síncrono**  
	El emisor espera respuesta (flecha con punta llena).  
	Ejemplo: llamar método.

- **Mensaje asíncrono**  
	El emisor no espera respuesta (flecha abierta).  
	Ejemplo: enviar notificación.

- **Mensaje de retorno**  
	Respuesta a una llamada (línea punteada).


#### Muestran una secuencia típica como:  
Usuario → Sistema → Base de datos → Sistema → Usuario.
Son ideales para entender flujos de interacción.

---
#ArquitecturadeSistemas