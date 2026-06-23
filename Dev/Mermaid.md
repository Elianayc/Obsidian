Mermaid permite crear diagramas escribiendo texto.

En Obsidian, GitHub y VS Code podés escribir:

```  m e r m a i d
classDiagram  
class Persona
```

y automáticamente se renderiza un diagrama.

---

## Estructura básica

> [!example]
> 
> ``` m e r m a i d
> classDiagram
> 
> class Persona {
>     - nombre: string
>     - edad: number
>     + saludar(): void
> }
> ```
> 
> **Resultado**:
> ``` mermaid
> classDiagram
> 
> class Persona {
>     - nombre: string
>     - edad: number
>     + saludar(): void
> }
> ```
> 

---

## Privacidad

| **Símbolo** | **Significado** |
| :---------: | :-------------: |
|      +      |     public      |
|      -      |     private     |
|      #      |    protected    |

> [!example]
> **Ejemplo**:
> ``` m e r m a i d
> classDiagram
> 
> class Persona {
>     - nombre: string
>     + saludar(): void
> }
> ```
> 
> **Se representa como**:
> ```mermaid
> classDiagram
> 
> class Persona {
>     - nombre: string
>     + saludar(): void
> }
> ```
> 

---

## Constructor

> [!example]
> **Ejemplo**:
> ``` m e r m a i d
> classDiagram
> 
> class Persona {
>     + constructor(nombre: string)
> }
> ```
> 
> **Se representa como**:
> ```mermaid
> classDiagram
> 
> class Persona {
>     + constructor(nombre: string)
> }
> ```


---

## Herencia

> [!example]
> 
> **Sintaxis**
> ```
> Padre <|-- Hijo
> ```
> 
> **Representación**
> ```mermaid
> classDiagram  
>   
> Padre <|-- Hijo
> ```
> 
> 

---

## Clase abstracta

> [!example]
> **Sintaxis**
> ```m e r m a i d
> classDiagram  
>   
> class Herramienta {  
> <<abstract>>  
> }
> ```
> 
> **Representación**
> 
> ```mermaid
> classDiagram  
>   
> class Herramienta {  
> <<abstract>>  
> }
> ```
> 

---

## Interfaces

> [!example]
> **Sintaxis**
> ```m e r m a i d
> classDiagram  
>   
> Volador <|
> ```
> 
> **Representación**
> 
> ```mermaid
> classDiagram  
>   
> class Herramienta {  
> <<abstract>>  
> }
> ```
> 

---

## Relaciones

##### Asociación

Una clase conoce o utiliza otra.

Lectura:

> Un Cliente tiene relación con un Pedido.

---

## Dependencia

Uso temporal.

Lectura:

> Pedido utiliza una Impresora.

---

## Agregación

La parte puede existir sin el todo.

Lectura:

> Un Auto tiene Ruedas.
> 
> Las Ruedas pueden existir independientemente.

---

## Composición

La parte pertenece completamente al todo.

Lectura:

> Una Casa está compuesta por Habitaciones.
> 
> Si desaparece la Casa, desaparecen las Habitaciones.

---

## Multiplicidades

### Uno a muchos

Lectura:

> Un Cliente puede tener muchos Pedidos.

---

### Uno a uno

---

### Muchos a muchos

---

## Ejemplo completo

---

## Chuleta rápida

|Relación|Mermaid|
|---|---|
|Herencia|`<|
|Implementa interfaz|`<|
|Asociación|`-->`|
|Dependencia|`..>`|
|Agregación|`o--`|
|Composición|`*--`|

---

## Flujo recomendado para la facultad

```
Análisis   ↓UML (Mermaid)   ↓TypeScript   ↓Testing
```

Primero pensá las clases y relaciones.

Después escribí el código.

Eso suele hacer mucho más fácil detectar errores de diseño antes de programar. 🚀