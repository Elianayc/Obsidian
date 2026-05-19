---
tags:
  - ProgramaciónII
  - Programación
---
También llamado: Objeto compuesto, Object Tree

---

##  Propósito

**Composite** es un patrón de diseño estructural que te permite componer objetos en estructuras de árbol y trabajar con esas estructuras como si fueran objetos individuales.

<p align="center"> <img src="https://refactoring.guru/images/patterns/content/composite/composite.png?id=73bcf0d94db360b636cd745f710d19db"> </p>

---

##  Problema

El uso del patrón Composite sólo tiene sentido cuando el modelo central de tu aplicación puede representarse en forma de árbol.

Por ejemplo, imagina que tienes dos tipos de objetos: `Productos` y `Cajas`. Una `Caja` puede contener varios `Productos` así como cierto número de `Cajas` más pequeñas. Estas `Cajas` pequeñas también pueden contener algunos `Productos` o incluso `Cajas` más pequeñas, y así sucesivamente.

Digamos que decides crear un sistema de pedidos que utiliza estas clases. Los pedidos pueden contener productos sencillos sin envolver, así como cajas llenas de productos... y otras cajas. ¿Cómo determinarás el precio total de ese pedido?

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/composite/problem-es.png?id=3b02eaf4b7744eb05b261ac48d3d3e4a"> </p>

Un pedido puede incluir varios productos empaquetados en cajas, que a su vez están empaquetados en cajas más grandes y así sucesivamente. La estructura se asemeja a un árbol boca abajo.

Puedes intentar la solución directa: desenvolver todas las cajas, repasar todos los productos y calcular el total. Esto sería viable en el mundo real; pero en un programa no es tan fácil como ejecutar un bucle. Tienes que conocer de antemano las clases de `Productos` y `Cajas` a iterar, el nivel de anidación de las cajas y otros detalles desagradables. Todo esto provoca que la solución directa sea demasiado complicada, o incluso imposible.

---

##  Solución

El patrón Composite sugiere que trabajes con `Productos` y `Cajas` a través de una interfaz común que declara un método para calcular el precio total.

¿Cómo funcionaría este método? Para un producto, sencillamente devuelve el precio del producto. Para una caja, recorre cada artículo que contiene la caja, pregunta su precio y devuelve un total por la caja. Si uno de esos artículos fuera una caja más pequeña, esa caja también comenzaría a repasar su contenido y así sucesivamente, hasta que se calcule el precio de todos los componentes internos. Una caja podría incluso añadir costos adicionales al precio final, como costos de empaquetado.

<p align="center"> <img src="https://refactoring.guru/images/patterns/content/composite/composite-comic-1-es.png?id=7925738e1b255eacd97b27da3a88f50e"> </p>

El patrón Composite te permite ejecutar un comportamiento de forma recursiva sobre todos los componentes de un árbol de objetos.

La gran ventaja de esta solución es que no tienes que preocuparte por las clases concretas de los objetos que componen el árbol. No tienes que saber si un objeto es un producto simple o una sofisticada caja. Puedes tratarlos a todos por igual a través de la interfaz común. Cuando invocas un método, los propios objetos pasan la solicitud a lo largo del árbol.

---

##  Analogía en el mundo real

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/composite/live-example.png?id=548a7cec45b493af66e8bfe524a137d3"> </p>

Un ejemplo de estructura militar.

Los ejércitos de la mayoría de países se estructuran como jerarquías. Un ejército está formado por varias divisiones; una división es un grupo de brigadas y una brigada está formada por pelotones, que pueden dividirse en escuadrones. Por último, un escuadrón es un pequeño grupo de soldados reales. Las órdenes se dan en la parte superior de la jerarquía y se pasan hacia abajo por cada nivel hasta que todos los soldados saben lo que hay que hacer.

##  Estructura

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/composite/structure-es-indexed.png?id=33bb9d4f3056f2f523111a90c92c7af1"> </p>

1. La interfaz **Componente** describe operaciones que son comunes a elementos simples y complejos del árbol.
    
2. La **Hoja** es un elemento básico de un árbol que no tiene subelementos.
    
    Normalmente, los componentes de la hoja acaban realizando la mayoría del trabajo real, ya que no tienen a nadie a quien delegarle el trabajo.
    
3. El **Contenedor** (también llamado _compuesto_) es un elemento que tiene subelementos: hojas u otros contenedores. Un contenedor no conoce las clases concretas de sus hijos. Funciona con todos los subelementos únicamente a través de la interfaz componente.
    
    Al recibir una solicitud, un contenedor delega el trabajo a sus subelementos, procesa los resultados intermedios y devuelve el resultado final al cliente.
    
4. El **Cliente** funciona con todos los elementos a través de la interfaz componente. Como resultado, el cliente puede funcionar de la misma manera tanto con elementos simples como complejos del árbol.
    

---

##  Pseudocódigo

En este ejemplo, el patrón **Composite** te permite implementar el apilamiento (_stacking_) de formas geométricas en un editor gráfico.

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/composite/example.png?id=98ba81d07c979038dd2ebf3c83a2e19f"> </p>

> [!example]
> Ejemplo del editor de formas geométricas.
> 
> La clase `GráficoCompuesto` es un contenedor que puede incluir cualquier cantidad de subformas, incluyendo otras formas compuestas. Una forma compuesta tiene los mismos métodos que una forma simple. Sin embargo, en lugar de hacer algo por su cuenta, una forma compuesta pasa la solicitud de forma recursiva a todos sus hijos y “suma” el resultado.
> 
> El código cliente trabaja con todas las formas a través de la interfaz común a todas las clases de forma. De este modo, el cliente no sabe si está trabajando con una forma simple o una compuesta. El cliente puede trabajar con estructuras de objetos muy complejas sin acoplarse a las clases concretas que forman esa estructura.
> 
> La interfaz componente declara operaciones comunes para objetos simples y complejos de una composición.
> ```ts
> interface Graphic {
>     move(x: number, y: number): void
>     draw(): void
> }
> ```
> 
> La clase hoja representa objetos finales de una composición.
> Un objeto hoja no puede tener ningún subobjeto. Normalmente, son los objetos hoja los que hacen el trabajo real, mientras que los objetos compuestos se limitan a delegar a sus subcomponentes.
> ```ts
> class Dot implements Graphic {
>     protected x: number
>     protected y: number
> 
>     constructor(x: number, y: number) {
>         this.x = x
>         this.y = y
>     }
> 
>     move(x: number, y: number): void {
>         this.x += x
>         this.y += y
>     }
> 
>     draw(): void {
>         // Dibuja un punto en X e Y.
>         console.log(`Dibujando punto en (${this.x}, ${this.y})`)
>     }
> }
> ```
> 
> Todas las clases de componente pueden extender otros componentes.
> ```ts
> class Circle extends Dot {
>     private radius: number
> 
>     constructor(x: number, y: number, radius: number) {
>         super(x, y)
>         this.radius = radius
>     }
> 
>     draw(): void {
>         // Dibuja un círculo en X y Y con radio R.
>         console.log(`Dibujando círculo en (${this.x}, ${this.y}) con radio ${this.radius}`)
>     }
> }
> ```
> 
> La clase compuesta representa componentes complejos que pueden tener hijos. Normalmente los objetos compuestos delegan el trabajo real a sus hijos y después "recapitulan" el resultado.
> ```ts
> class CompoundGraphic implements Graphic {
>     private children: Graphic[] = []
> 
>     // Un objeto compuesto puede añadir o eliminar otros
>     // componentes (tanto simples como complejos) a o desde su
>     // lista hija.
>     add(child: Graphic): void {
>         // Añade un hijo a la matriz de hijos.
>         this.children.push(child)
>     }
> 
>     remove(child: Graphic): void {
>         // Elimina un hijo de la matriz de hijos.
>         const index = this.children.indexOf(child)
>         if (index >= 0) {
>             this.children.splice(index, 1)
>         }
>     }
> 
>     move(x: number, y: number): void {
>         for (const child of this.children) {
>             child.move(x, y)
>         }
>     }
> 
>     // Un compuesto ejecuta su lógica primaria de una forma
>     // particular. Recorre recursivamente todos sus hijos,
>     // recopilando y recapitulando sus resultados.
>     draw(): void {
>         for (const child of this.children) {
>             child.draw()
>         }
>     }
> }
> ```
> 

--- 

##  Aplicabilidad

Usá el patrón **Composite** cuando tengas que modelar objetos con estructura de árbol.

El patrón te da dos tipos de elementos con la misma interfaz: **hojas** (objetos simples) y **contenedores** (objetos complejos). Un contenedor puede tener hojas u otros contenedores adentro, lo que permite armar estructuras recursivas tipo árbol.

También sirve cuando querés que el código cliente trate **igual** a objetos simples y complejos. Como todos comparten la misma interfaz, el cliente no necesita saber con qué tipo concreto está trabajando.

---

##  Cómo implementarlo

1. Primero fijate que el modelo de tu app pueda representarse como un **árbol**. Separalo en elementos simples y contenedores que puedan contener ambos tipos.

2. Definí una **interfaz componente** con métodos que tengan sentido tanto para objetos simples como complejos.

3. Creá una o varias **clases hoja** para representar los elementos simples.

4. Creá la **clase contenedora** para los elementos complejos. Tiene que tener un array donde guarde subelementos (hojas o contenedores) usando el tipo de la interfaz.
    
     Cuando implementes los métodos, el contenedor debería delegar la mayor parte del trabajo a sus hijos.

5. Definí los métodos para **agregar y eliminar hijos** dentro del contenedor.
    
     Podés poner estos métodos en la interfaz componente, aunque rompa un poco el principio de segregación de interfaces (porque las hojas no los usan). A cambio, el cliente puede tratar todos los elementos de la misma forma.

---

##  Pros y contras

**Pros**
- Podés trabajar con árboles complejos mucho más fácil, aprovechando polimorfismo y recursividad.  
- Principio abierto/cerrado: podés agregar nuevos tipos de elementos sin romper el código existente.

**Contras**
- Puede ser difícil definir una interfaz común si las clases son muy distintas. A veces terminás generalizando demasiado y la interfaz se vuelve confusa.

---

## Relaciones con otros patrones

- Builder se puede usar para construir árboles Composite complejos de forma recursiva.  

- Chain of Responsibility suele combinarse: una hoja puede pasar la solicitud hacia sus padres hasta la raíz.  

- Iterator sirve para recorrer el árbol Composite.  

- Visitor permite ejecutar operaciones sobre todo el árbol.  

- Flyweight puede usarse para compartir nodos hoja y ahorrar memoria.