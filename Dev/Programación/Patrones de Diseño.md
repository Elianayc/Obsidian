---
tags:
  - Programación
  - ProgramaciónII
---
### ¿Qué es un patrón de diseño?
Los patrones de diseño son **soluciones habituales a problemas que aparecen con frecuencia en el diseño de software**.  
Funcionan como **plantillas o planos reutilizables** que pueden adaptarse a distintas situaciones.

No son código listo para copiar y pegar.  
Un patrón es un **concepto general** que describe cómo resolver un problema. Cada implementación concreta dependerá del contexto del programa.

#### Diferencia entre patrón y algoritmo
Ambos describen soluciones típicas, pero no son lo mismo:

- **Algoritmo:**  
    Define una secuencia clara de pasos para lograr un objetivo.  
    Ejemplo: una receta de cocina.

- **Patrón de diseño:**  
    Describe una solución a alto nivel.  
    No indica pasos exactos, sino la estructura general de la solución.  
    Ejemplo: un plano arquitectónico.

El mismo patrón puede implementarse de formas distintas en programas diferentes.

---

### Historia de los patrones de diseño
Los patrones no fueron “inventados” de una sola vez. Surgen cuando una solución se repite muchas veces y alguien la documenta y le da un nombre.

El concepto original proviene del arquitecto **Christopher Alexander**, en su libro _El lenguaje de patrones_, donde describía soluciones reutilizables para el diseño urbano.

La idea fue adoptada en programación por cuatro autores:
- Erich Gamma
- John Vlissides
- Ralph Johnson
- Richard Helm

En 1995 publicaron el libro **Design Patterns**, donde presentaron **23 patrones de diseño orientados a objetos**.  
Este libro se volvió muy influyente y se lo conoce como el libro de la **Gang of Four (GoF)**.

Desde entonces:
- Se han identificado muchos más patrones.
- La metodología se extendió a otras áreas de la programación, no solo a orientación a objetos.

---

### ¿Por qué aprender patrones de diseño?
Un desarrollador puede programar durante años sin conocerlos, pero aprender patrones aporta ventajas importantes:

- Permiten resolver problemas comunes con soluciones probadas.
- Mejoran la comunicación entre desarrolladores al usar un vocabulario compartido.
- Facilitan escribir código más mantenible, flexible y reutilizable.
- Ayudan a reconocer buenas prácticas de diseño.

---

### Críticas a los patrones

**1. Parche para lenguajes flojos**  
A veces existen porque el lenguaje no tiene buenas abstracciones (ej: Strategy hoy puede ser una simple lambda).

**2. Complejidad innecesaria**  
Si se aplican rígidamente, pueden complicar el código al pedo.

**3. Uso excesivo**  
Cuando recién se aprenden, se quieren usar en todo, incluso cuando algo simple alcanza.

---

## Clasificación por **escala** 
Responde: **¿Qué tan grande es el problema que resuelve el patrón?**


### Idioms (nivel bajo)
Son patrones muy pequeños y específicos de un lenguaje.

Ejemplos:
- Cómo recorrer colecciones en un lenguaje
- Cómo manejar errores en un lenguaje

Se aplican a nivel **código**.


### Patrones de diseño (nivel medio)
Resuelven problemas de **clases y objetos**.
Se aplican al diseño interno del software.

- [[Patrones Creacionales]]
- [[Patrones Estructurales]]
- [[Patrones de Comportamiento]]


### Patrones de arquitectura (nivel alto)
Resuelven la estructura de **todo el sistema**.

##### Ejemplos:
- MVC
- Microservicios
- Cliente–Servidor

Se aplican a nivel **aplicación completa**.



