---
tags:
  - Programación
  - ProgramaciónII
---
También llamado: Método fábrica, Constructor virtual

---

##  Propósito

**Factory Method** es un patrón de diseño creacional que proporciona una interfaz para crear objetos en una superclase, mientras permite a las subclases alterar el tipo de objetos que se crearán.
<p align="center">
  <img src="https://refactoring.guru/images/patterns/content/factory-method/factory-method-es.png">
</p>

---

##  Problema

<p align="center">
  <img src="https://refactoring.guru/images/patterns/diagrams/factory-method/problem1-es.png">
</p>

Imaginate que estás armando una app de logística. La primera versión solo maneja envíos en **camión**, así que casi todo el código vive dentro de la clase `Camión`.

Con el tiempo la app despega y empiezan a llegarte pedidos de empresas navieras para agregar transporte por **barco**.

El tema es que no es tan fácil como sumar una clase nueva. Gran parte del sistema ya está **acoplado a `Camión`**, así que para meter barcos tenés que tocar un montón de código existente. Y si después querés agregar trenes, aviones u otro transporte… otra vez lo mismo.

Resultado: el código se empieza a ensuciar, lleno de **if/else** que cambian el comportamiento según el tipo de transporte. Y eso se vuelve difícil de mantener y escalar.

---

##  Solución

El patrón Factory Method propone que, en vez de usar el operador `new` directamente para crear objetos, se llame a un **método fábrica** especial. Los objetos se siguen creando con `new`, pero ahora desde ese método. A los objetos que devuelve se los llama **productos**.

<p align="center">
  <img src="https://refactoring.guru/images/patterns/diagrams/factory-method/solution1.png">
</p>

Las subclases pueden cambiar qué tipo de objeto devuelve el método fábrica.

A primera vista parece un cambio medio inútil, porque solo movimos el lugar donde se crea el objeto. Pero la clave es que ahora podés **sobrescribir el método fábrica en subclases** y decidir qué producto crear.

Eso sí, hay una condición: los productos deben compartir una **clase base o interfaz común**. Por eso el método fábrica de la clase base devuelve ese tipo común.
<p align="center">
  <img src="https://refactoring.guru/images/patterns/diagrams/factory-method/solution2-es.png">
</p>

Todos los productos deben seguir la misma **interfaz**.

Por ejemplo, `Camión` y `Barco` implementan la interfaz `Transporte`, que tiene el método `entrega`. Cada uno lo implementa distinto: uno entrega por tierra y el otro por mar. Entonces, `LogísticaTerrestre` crea camiones y `LogísticaMarítima` crea barcos.

<p align="center">
  <img src="https://refactoring.guru/images/patterns/diagrams/factory-method/solution3-es.png">
</p>
Mientras todos los productos respeten la interfaz común, podés pasarlos al código cliente sin romper nada.

El código cliente usa el método fábrica y trata a todos los transportes como `Transporte`. Sabe que existe `entrega`, pero no necesita saber **cómo** funciona internamente.

---

##  Estructura

<p align="center">
  <img src="https://refactoring.guru/images/patterns/diagrams/factory-method/structure-indexed.png">
</p>

1. **Producto**  
    Es la interfaz común que comparten todos los objetos que la creadora puede generar.
2. **Productos Concretos**  
    Son las distintas implementaciones de esa interfaz. Cada uno representa una variante real del producto.
3. **Creadora**  
    Define el método fábrica que devuelve objetos del tipo Producto. El tipo de retorno debe ser la interfaz común.
	
	El método fábrica puede ser abstracto para obligar a las subclases a implementarlo, o puede traer una implementación por defecto.
	
	Ojo con esto: la creadora no existe principalmente para crear objetos. Su responsabilidad principal es la **lógica de negocio** que usa esos productos. El patrón sirve para desacoplar esa lógica de las clases concretas.  
	Una analogía simple: una empresa de software puede capacitar programadores, pero su objetivo principal sigue siendo desarrollar software.
	
4. **Creadores Concretos**  
    Sobrescriben el método fábrica para devolver un producto distinto.
	
	El método fábrica no siempre tiene que crear objetos nuevos: también puede devolver instancias ya existentes (por ejemplo, desde caché o pools de objetos).

---

##  Pseudocódigo

Este ejemplo muestra cómo usar **Factory Method** para crear componentes de interfaz (UI) multiplataforma sin acoplar el código a clases concretas.

<p align="center">
  <img src="https://refactoring.guru/images/patterns/diagrams/factory-method/example.png">
</p>

Ejemplo del diálogo multiplataforma.

La clase base del diálogo usa distintos elementos de UI para mostrar su ventana. Según el sistema operativo, esos elementos pueden verse distintos, pero deben comportarse igual. Un botón sigue siendo un botón, aunque cambie su apariencia.

Con Factory Method no hace falta reescribir toda la lógica del diálogo para cada sistema operativo. La clase base define un método fábrica que crea botones, y después cada subclase del diálogo puede sobrescribir ese método para devolver botones específicos (por ejemplo, estilo Windows).

Así, la subclase reutiliza la mayor parte del código del diálogo original, pero cambia el tipo de botón que se muestra en pantalla gracias al método fábrica.

Para que esto funcione, el diálogo debe trabajar con **botones abstractos** (una interfaz o clase base común). De esta forma, el código funciona sin importar qué tipo concreto de botón se use.

Este mismo enfoque podría aplicarse a otros componentes de UI. Pero si agregás muchos métodos fábrica distintos, te empezás a acercar al patrón **Abstract Factory**, que es una evolución de esta idea.

**Producto (Interfaz)**
Esta interfaz define qué puede hacer cualquier botón. El cliente solo conoce ESTA interfaz, no las clases concretas.
```ts

interface Button {
  render(): void;                 // dibujar el botón
  onClick(fn: () => void): void;  // asignar acción al hacer click
}
````

**Productos Concretos**
```ts
// Implementación concreta para Windows
class WindowsButton implements Button {

  // Cómo se dibuja el botón en Windows
  render(): void {
    console.log("Renderizando botón estilo Windows");
  }

  // Cómo se maneja el click en Windows
  onClick(fn: () => void): void {
    console.log("Evento click Windows vinculado");
    fn(); // ejecuta la función que le pasamos
  }
}


// Implementación concreta para Web
class HTMLButton implements Button {

  render(): void {
    console.log("Renderizando botón HTML");
  }

  onClick(fn: () => void): void {
    console.log("Evento click navegador vinculado");
    fn();
  }
}
```

**Creador Abstracto**
Esta es la clase CLAVE del patrón. NO sabe qué botón concreto va a crear. Solo define el método fábrica.
```ts
abstract class Dialog {
  // Factory Method
  // Las subclases estarán obligadas a implementarlo.
  abstract createButton(): Button;

  // Lógica de negocio del diálogo
  // Usa botones, pero sin saber cuáles concretos.
  render(): void {

    //  Crea el botón usando el método fábrica
    const okButton = this.createButton();

    // Usa el botón sin conocer su clase real
    okButton.onClick(this.closeDialog);

    // Lo dibuja
    okButton.render();
  }

  closeDialog() {
    console.log("Cerrando diálogo...");
  }
}
```

**Creadores Concretos**
Cada subclase decide QUÉ botón crear.
```ts
class WindowsDialog extends Dialog {
  createButton(): Button {
    // Devuelve botón específico de Windows
    return new WindowsButton();
  }
}

class WebDialog extends Dialog {
  createButton(): Button {
    // Devuelve botón específico de Web
    return new HTMLButton();
  }
}
```

**Aplicación (Cliente)**
```ts
class Application {
  private dialog!: Dialog; 
  // Guarda una referencia al creador,
  // pero SOLO conoce el tipo abstracto Dialog.

  initialize(os: string) {
    // Decide qué creador usar según el entorno
    if (os === "Windows") {
      this.dialog = new WindowsDialog();
    } 
    else if (os === "Web") {
      this.dialog = new WebDialog();
    } 
    else {
      throw new Error("Sistema operativo desconocido");
    }
  }

  main(os: string) {
    this.initialize(os);
    // El cliente usa el creador sin saber cuál es concreto
    this.dialog.render();
  }
}
```

**Ejecución**
```ts
const app = new Application();
app.main("Windows"); // Probá cambiar por "Web"
```

---

##  Aplicabilidad

Usá Factory Method cuando no sabés de antemano qué tipos concretos de objetos va a usar tu programa.

El patrón separa el código que **crea** objetos del código que **los usa**, así podés extender la creación sin tocar el resto. Si aparece un nuevo tipo de producto, solo creás una nueva subclase creadora y sobrescribís el Factory Method.

---

Usalo cuando quieras permitir que otros **extiendan un framework o librería**.

La herencia permite modificar comportamientos, pero el framework necesita saber cuándo usar tu versión. La solución es centralizar la creación en un Factory Method y dejar que cualquiera lo sobrescriba.

Ejemplo: el framework solo tiene botones cuadrados.  
Vos creás `BotónRedondo` y una subclase `UIConBotonesRedondos` que sobrescribe `crearBotón` para devolver ese nuevo botón. Luego usás esa subclase en vez del framework original. Listo.

---

Usalo cuando quieras **reutilizar objetos costosos** en lugar de crear nuevos siempre.
Esto pasa con conexiones a bases de datos, archivos o recursos de red.

Para reutilizar objetos necesitás:
1. Guardar los objetos creados.
2. Buscar uno disponible cuando alguien lo pida.
3. Devolverlo si existe.
4. Crear uno nuevo si no hay disponibles.

Ese código no puede ir en el constructor (porque el constructor siempre crea objetos nuevos).  
Por eso necesitás un método separado que pueda **crear o reutilizar** objetos → exactamente lo que hace Factory Method.

---

##  Cómo implementarlo

1. Primero hacé que todos los productos compartan la misma interfaz. Esa interfaz tiene que declarar métodos que tengan sentido para todos los productos.

2. Agregá un Factory Method vacío dentro de la clase creadora. El tipo de retorno debe ser la interfaz común de los productos.

3. Buscá todas las veces que la clase creadora usa `new` para crear productos y reemplazalas por llamadas al Factory Method. A medida que hacés esto, mové la lógica de creación al método fábrica.
    
    Puede que necesites agregar un parámetro temporal al Factory Method para indicar qué producto crear. Al principio puede quedar feo, incluso con un `switch` grande decidiendo qué instanciar. No pasa nada, es parte del proceso.

3. Creá subclases creadoras para cada tipo de producto. En cada una sobrescribí el Factory Method y mové ahí la lógica de creación que corresponda.

4. Si hay muchos productos y no tiene sentido crear una subclase por cada uno, podés reutilizar el parámetro de control.
	
    **Ejemplo:**  
    `Correo` → `CorreoAéreo` y `CorreoTerrestre`  
    `Transporte` → `Avión`, `Camión`, `Tren`
    
    `CorreoAéreo` usa solo `Avión`, pero `CorreoTerrestre` podría usar `Camión` o `Tren`. En vez de crear muchas subclases, el cliente puede pasar un parámetro al Factory Method de `CorreoTerrestre` para elegir el transporte.

5. Si después de todo esto el Factory Method base queda vacío, hacelo abstracto. Si todavía tiene algo, podés dejarlo como comportamiento por defecto.

---

##  Pros y contras

**Pros**
- Evita el acoplamiento fuerte entre la clase creadora y los productos concretos.
- **Principio de responsabilidad única:** podés separar la lógica de creación de objetos y llevarla a un solo lugar, haciendo el código más mantenible.
- **Principio abierto/cerrado:** podés agregar nuevos tipos de productos sin romper ni modificar el código cliente existente.

**Contras**
- El código puede volverse más complejo porque tenés que crear varias subclases nuevas para implementar el patrón. Lo ideal es aplicarlo cuando ya existe una jerarquía de clases creadoras.

---

##  Relaciones con otros patrones

- Muchos diseños arrancan con **Factory Method** porque es más simple y se adapta fácil usando subclases. Con el tiempo suelen evolucionar hacia **Abstract Factory, Prototype o Builder**, que son más flexibles pero también más complejos.

- **Abstract Factory** muchas veces se apoya en varios **Factory Method** para crear sus productos, aunque también puede usar **Prototype** para implementar esos métodos.

- **Factory Method** puede combinarse con **Iterator** para que distintas subclases de colecciones devuelvan distintos tipos de iteradores compatibles con esas colecciones.

- **Prototype** no usa herencia, por eso evita los problemas típicos de la herencia, pero requiere una inicialización más compleja del objeto clonado. **Factory Method**, en cambio, sí usa herencia pero no necesita ese paso extra de inicialización.

- **Factory Method** es una especialización de **Template Method**. De hecho, un Factory Method puede ser uno de los pasos dentro de un Template Method más grande.