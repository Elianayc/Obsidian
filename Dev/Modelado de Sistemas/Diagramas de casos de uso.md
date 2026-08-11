---
tags:
  - Modeladodesistemas
---
Describen las **funcionalidades del sistema desde la mirada del usuario**.  
Muestran _qué puede hacer el usuario_ con el sistema, no cómo está construido internamente.

Se usan mucho al inicio del desarrollo para definir requisitos.

![[diagramacasosdeuso.png|670]]


### Elementos principales


#### Actor
Representa quién interactúa con el sistema.

**Puede ser:**
- Usuario
- Otro sistema
- Dispositivo

Se dibuja como un **muñequito**.

**Ejemplos:**
- Cliente
- Administrador
- Sistema de pagos



#### Sistema
Se representa como un **rectángulo grande** que contiene los casos de uso.



#### Caso de uso
Es una funcionalidad del sistema.  
Se dibuja como un **óvalo**.

Se nombran con verbos:

- Iniciar sesión
- Comprar producto
- Registrar usuario



#### Relación Actor – Caso de uso
Una **línea simple** indica que el actor interactúa con esa funcionalidad.

---

### Relaciones entre casos de uso

**«include»**  
Un caso de uso **siempre incluye** a otro.  
Ejemplo: Comprar producto → incluye → Validar pago.  
Se usa cuando una funcionalidad siempre necesita otra.

**«extend»**  
Un caso de uso **a veces extiende** a otro.  
Ejemplo: Comprar producto → puede extender → Aplicar descuento.  
Es comportamiento opcional.

**Generalización (herencia de actores o casos)**  
Un actor o caso de uso puede heredar de otro.  
Ejemplo: Administrador hereda de Usuario.

---
#ArquitecturadeSistemas
