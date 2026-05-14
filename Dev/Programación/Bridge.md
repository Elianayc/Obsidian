---
tags:
  - ProgramaciónII
  - Programación
---
También llamado: Puente

---

##  Propósito

**Bridge** es un patrón de diseño estructural que te permite dividir una clase grande, o un grupo de clases estrechamente relacionadas, en dos jerarquías separadas (abstracción e implementación) que pueden desarrollarse independientemente la una de la otra.

<p align="center"> <img src="https://refactoring.guru/images/patterns/content/bridge/bridge.png?id=bd543d4fb32e11647767301581a5ad54"> </p>

---

##  Problema

¿_Abstracción?_ ¿_Implementación_? ¿Asusta? Mantengamos la calma y veamos un ejemplo sencillo.

Supongamos que tenés una clase geométrica `Forma` con un par de subclases: `Círculo` y `Cuadrado`. Querés extender esta jerarquía de clases para que incorpore colores, así que planeás crear las subclases de forma `Rojo` y `Azul`. Sin embargo, como ya tenés dos subclases, tenés que crear cuatro combinaciones de clase, como `CírculoAzul` y `CuadradoRojo`.

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/bridge/problem-es.png?id=15670d9922988494a1fa39591a205297"> </p>

El número de combinaciones de clases crece en progresión geométrica.

Agregar nuevos tipos de forma y color a la jerarquía hará que ésta crezca exponencialmente. Por ejemplo, para agregar una forma de triángulo deberás introducir dos subclases, una para cada color. Y después, para agregar un nuevo color habrá que crear tres subclases, una para cada tipo de forma. Cuanto más avancemos, peor será.

---

##  Solución

Este problema aparece porque intentamos extender las clases de forma en dos dimensiones independientes: forma y color. Es algo muy común cuando se usa herencia.

El patrón Bridge busca resolverlo pasando de herencia a composición de objetos. O sea, se extrae una de las dimensiones a una jerarquía de clases separada, para que las clases originales referencien un objeto de esa nueva jerarquía en vez de tener todo el estado y comportamiento en una sola clase.

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/bridge/solution-es.png?id=ea5b0ca5eb04228838c3079bd7d877d6"> </p>

Así podés evitar la explosión de jerarquías transformándola en varias jerarquías relacionadas.

Con esta solución, el código del color se extrae a su propia clase con dos subclases: `Rojo` y `Azul`. La clase `Forma` pasa a tener una referencia a un objeto color y delega ahí todo lo relacionado al color. Esa referencia funciona como un puente entre `Forma` y `Color`. A partir de ahí, agregar nuevos colores ya no requiere modificar las clases de forma.

----

#### Abstracción e implementación

El libro de la GoF presenta los términos _Abstracción_ e _Implementación_ dentro del patrón Bridge, pero suenan más complejos de lo que realmente son. Después del ejemplo de formas y colores, la idea se vuelve mucho más clara.

La _Abstracción_ es una capa de control de alto nivel que no hace el trabajo pesado, sino que lo delega a la capa de _implementación_.

No se refiere a interfaces o clases abstractas del lenguaje, sino a conceptos más generales.

En una app real, la abstracción puede ser la GUI y la implementación la API del sistema operativo a la que la GUI llama cuando el usuario interactúa.

La aplicación puede crecer en dos direcciones independientes:

- Tener distintas GUIs (por ejemplo, para usuarios comunes o administradores).
- Soportar distintas APIs (por ejemplo, Windows, Linux y macOS).

En el peor de los casos, esta aplicación podría asemejarse a un plato gigante de espagueti, en el que cientos de condicionales conectan distintos tipos de GUI con varias API por todo el código.

<p align="center"> <img src="https://refactoring.guru/images/patterns/content/bridge/bridge-3-es.png?id=adab9e8324ca6f2db4a3af44616d0af3"> </p>

Hacer incluso un cambio simple en una base monolítica es difícil porque tenés que entender _todo_ el sistema. En módulos más chicos y bien definidos, los cambios son mucho más fáciles.

Podés ordenar el caos separando el código de combinaciones interfaz-plataforma en clases independientes, pero eso termina generando _muchísimas_ clases. La jerarquía crece exponencialmente porque cada nueva GUI o nueva API obliga a crear más clases.

El patrón Bridge propone dividir en dos jerarquías:

- **Abstracción:** la capa GUI de la app.
- **Implementación:** las APIs de los sistemas operativos.

<p align="center"> <img src="https://refactoring.guru/images/patterns/content/bridge/bridge-2-es.png?id=aa4df8805e6cae965df234d7dcd3d477"> </p>

Es una forma de estructurar una aplicación multiplataforma.

El objeto de la **abstracción** controla la apariencia de la app y delega el trabajo real al objeto de **implementación** vinculado. Las implementaciones son intercambiables mientras respeten una interfaz común, así la misma GUI puede funcionar tanto en Windows como en Linux.

Como resultado, podés modificar las clases de la GUI sin tocar las de la API. Y si querés soportar otro sistema operativo, solo necesitás crear una nueva subclase en la jerarquía de implementación.

##  Estructura

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/bridge/structure-es-indexed.png?id=53438bb41db049e24b4ce8fab5289b51"> </p>

1. La **Abstracción** ofrece lógica de control de alto nivel. Depende de que el objeto de la implementación haga el trabajo de bajo nivel.
    
2. La **Implementación** declara la interfaz común a todas las implementaciones concretas. Una abstracción sólo se puede comunicar con un objeto de implementación a través de los métodos que se declaren aquí.
    
    La abstracción puede enumerar los mismos métodos que la implementación, pero normalmente la abstracción declara funcionalidades complejas que dependen de una amplia variedad de operaciones primitivas declaradas por la implementación.
    
3. Las **Implementaciones Concretas** contienen código específico de plataforma.
    
4. Las **Abstracciones Refinadas** proporcionan variantes de lógica de control. Como sus padres, trabajan con distintas implementaciones a través de la interfaz general de implementación.
    
5. Normalmente, el **Cliente** sólo está interesado en trabajar con la abstracción. No obstante, el cliente tiene que vincular el objeto de la abstracción con uno de los objetos de la implementación.
    

---

##  Pseudocódigo

Este ejemplo ilustra cómo puede ayudar el patrón **Bridge** a dividir el código monolítico de una aplicación que gestiona dispositivos y sus controles remotos. Las clases `Dispositivo` actúan como implementación, mientras que las clases `Remoto` actúan como abstracción.

<p align="center"> <img src="https://refactoring.guru/images/patterns/diagrams/bridge/example-es.png?id=89c406a189c45885004d7fa094f616b1"> </p>

La jerarquía de clase original se divide en dos partes: dispositivos y controles remotos.

La clase base de control remoto declara un campo de referencia que la vincula con un objeto de dispositivo. Todos los controles remotos funcionan con los dispositivos a través de la interfaz general de dispositivos, que permite al mismo remoto soportar varios tipos de dispositivos.

Puedes desarrollar las clases de control remoto independientemente de las clases de dispositivo. Lo único necesario es crear una nueva subclase de control remoto. Por ejemplo, puede ser que un control remoto básico cuente tan solo con dos botones, pero puedes extenderlo añadiéndole funciones, como una batería adicional o pantalla táctil.

El código cliente vincula el tipo deseado de control remoto con un objeto específico de dispositivo a través del constructor del control remoto.

---

La interfaz de "implementación" declara métodos comunes a todas las clases concretas de implementación. No tiene por qué coincidir con la interfaz de la abstracción. De hecho, las dos interfaces pueden ser completamente diferentes.
Normalmente, la interfaz de implementación únicamente proporciona operaciones primitivas, mientras que la abstracción define operaciones de más alto nivel.

```ts
interface Device {
  isEnabled(): boolean;
  enable(): void;
  disable(): void;
  getVolume(): number;
  setVolume(volume: number): void;
  getChannel(): number;
  setChannel(channel: number): void;
}
```

La "abstracción" define la interfaz para la parte de "control" de las dos jerarquías de clase. Mantiene una referencia a un objeto de la jerarquía de "implementación" y delega todo el trabajo real a este objeto.
```ts
class RemoteControl {
  protected device: Device;

  constructor(device: Device) {
    this.device = device;
  }

  togglePower(): void {
    if (this.device.isEnabled()) {
      this.device.disable();
    } else {
      this.device.enable();
    }
  }

  volumeDown(): void {
    this.device.setVolume(this.device.getVolume() - 10);
  }

  volumeUp(): void {
    this.device.setVolume(this.device.getVolume() + 10);
  }

  channelDown(): void {
    this.device.setChannel(this.device.getChannel() - 1);
  }

  channelUp(): void {
    this.device.setChannel(this.device.getChannel() + 1);
  }
}
```

Puedes extender clases de la jerarquía de abstracción independientemente de las clases de dispositivo.
```ts
class AdvancedRemoteControl extends RemoteControl {
  mute(): void {
    this.device.setVolume(0);
  }
}
```

--- 

##  Aplicabilidad

Usá el patrón Bridge cuando quieras dividir y ordenar una clase monolítica que tenga muchas variantes de una misma funcionalidad (por ejemplo, si la clase puede trabajar con distintos servidores de base de datos).

Cuanto más crece una clase, más difícil es entender cómo funciona y más tiempo lleva modificarla. Cambiar una sola variante puede obligarte a tocar muchas partes del código, lo que aumenta la probabilidad de errores o de dejar efectos colaterales sin contemplar.

El patrón Bridge permite separar esa clase gigante en varias jerarquías de clases. Después podés modificar cada jerarquía de forma independiente, lo que simplifica el mantenimiento y reduce el riesgo de romper lo que ya funciona.

Usalo también cuando necesites extender una clase en varias dimensiones independientes.

La idea es extraer una jerarquía de clases para cada dimensión. La clase original delega el trabajo a objetos de esas jerarquías en lugar de hacerlo todo por sí misma.

También sirve cuando necesitás cambiar implementaciones en tiempo de ejecución.

Aunque es opcional, Bridge te deja reemplazar el objeto de implementación dentro de la abstracción de forma simple, básicamente asignando otro objeto al campo correspondiente.

---

## ## Cómo implementarlo

1. Identificá las dimensiones independientes de tus clases (por ejemplo: abstracción/plataforma, dominio/infraestructura, front end/back end o interfaz/implementación).

2. Revisá qué operaciones necesita el cliente y definilas en la clase base de la abstracción.

3. Determiná qué operaciones están disponibles en todas las plataformas y declaralas en la interfaz general de implementación si la abstracción las necesita.

4. Creá clases concretas de implementación para cada plataforma de tu dominio, asegurándote de que todas sigan la misma interfaz de implementación.

5. Dentro de la clase de abstracción agregá un campo que referencie a la implementación. La abstracción delega la mayor parte del trabajo en ese objeto.

6. Si hay muchas variantes de lógica de alto nivel, creá abstracciones refinadas extendiendo la clase base.

7. El código cliente debe pasar el objeto de implementación al constructor de la abstracción para vincularlos. Después de eso, el cliente puede trabajar solo con la abstracción e ignorar la implementación.

---

## ## Pros y contras

**Pros**
- Podés crear clases y aplicaciones independientes de la plataforma.
- El código cliente trabaja con abstracciones de alto nivel y no queda expuesto a los detalles de la plataforma.
- _Principio abierto/cerrado_: podés agregar nuevas abstracciones e implementaciones sin que dependan entre sí.
- _Principio de responsabilidad única_: separás la lógica de alto nivel (abstracción) de los detalles de la plataforma (implementación).

**Contras**
- Puede que el código se vuelva más complejo si aplicás el patrón a una clase que ya es muy cohesionada.

---

## Relaciones con otros patrones

- Bridge suele pensarse desde el inicio del diseño para poder desarrollar partes de la app de forma independiente. En cambio, Adapter se usa más con apps ya existentes para lograr que clases incompatibles puedan trabajar juntas sin problemas.

- Bridge, State, Strategy (y en parte Adapter) tienen estructuras muy parecidas porque todos se basan en composición y delegan trabajo a otros objetos. Aun así, cada patrón resuelve problemas distintos. Un patrón no es solo una forma de estructurar código, también sirve para comunicar a otros devs qué problema está resolviendo.

- Podés usar Abstract Factory junto con Bridge. Esta combinación es útil cuando algunas abstracciones del Bridge solo pueden funcionar con implementaciones específicas.