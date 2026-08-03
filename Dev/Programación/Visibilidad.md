---
tags:
  - Programación
  - ProgramaciónII
---
Nivel de exposición de los miembros de una clase (atributos y métodos).  

Define desde dónde se puede acceder a esos elementos dentro del sistema.

La visibilidad es clave para aplicar encapsulamiento y controlar el acceso a los datos.

---

### Privado (private)
Solo puede ser accedido desde el interior de la misma clase.

Es el nivel más restrictivo y el más utilizado en diseño orientado a objetos moderno para proteger el estado interno.

**Uso típico**:
- atributos internos
- datos que no deben ser modificados directamente desde afuera

---

### Protegido (protected)

Permite acceso desde:
- la misma clase
- clases hijas (herencia)

No es accesible desde instancias externas.

**Uso típico**:
- clases base donde las subclases necesitan reutilizar o extender comportamiento interno

---

### Público (public)
Puede ser accedido desde cualquier parte del sistema.

Es el nivel menos restrictivo.

**Uso típico**:
- métodos que forman parte de la interfaz de la clase
- constructores en muchos casos
- propiedades intencionalmente expuestas

---

### Sin modificador (default / package-private)
Nivel intermedio entre privado y protegido.

Permite acceso únicamente dentro del mismo paquete.

No es común en TypeScript, pero sí en lenguajes como Java.

No permite acceso desde subclases fuera del paquete.

---

## Relación con diseño moderno
En enfoques modernos de programación orientada a objetos:

- se prefiere `private` por defecto
- se expone lo mínimo necesario mediante métodos o propiedades controladas
- se evita exponer atributos directamente como `public`

---

[[Visibilidad en Typescript]]