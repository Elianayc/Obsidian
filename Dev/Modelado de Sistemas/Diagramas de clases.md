---
tags:
---
Representan la **estructura estática** de un sistema orientado a objetos.  
Muestran clases, atributos, métodos y las relaciones entre ellas.

Sirven para visualizar cómo está organizado el sistema antes de programar.

---

## Cómo se representa una clase en UML

Una clase se dibuja como un rectángulo dividido en **3 secciones**:

1. **Nombre de la clase**  
2. **Atributos** (propiedades / variables)  
3. **Métodos** (funciones / comportamientos)

![[diagramadeclases|500]]

---

## Visibilidad

Indican desde dónde se puede acceder los métodos y atributos.

| **Símbolo** |   Visibilidad   |             Significado              |
| :---------: | :-------------: | :----------------------------------: |
|   **`+`**   |     Público     |   Accesible desde cualquier clase    |
|   **`-`**   |     Privado     |  Solo accesible dentro de la clase   |
|   **`#`**   |    Protegido    | Accesible desde la clase y sus hijas |
|   **`~`**   | Paquete/Default |  Accesible dentro del mismo paquete  |

**Ejemplo:**
```ts
+ nombre : string // Atributo público
- edad : int // Atributo privado
# calcularEdad() // Método Protegido
```

---

## Relaciones entre clases
Las clases se conectan mediante líneas con distintos símbolos.

![[relacionesclases|300]]

---

## Clases abstractas
No se pueden instanciar.  
Sirven como base para otras clases.

En UML se representan de dos formas:
• Nombre de la clase en _cursiva_ 
• O usando estereotipo:
		<<*ClaseAbstracta*>>
		<<*a*>> o <<*abstract*>>

También los métodos abstractos se escriben en _cursiva_.

---

## Interfaces (extra útil para sumar)
Se representan con estereotipo:
<<*Interface*>>

---

## Multiplicidad
Indica **cuántos objetos** participan en la relación.

![[multiplicidadderelaciones|250]]

---

### [[Mermaid]]
Se utiliza para generar diagramas UML a partir de código o escribiendo texto.

--- 

#ModeladodeSistemas