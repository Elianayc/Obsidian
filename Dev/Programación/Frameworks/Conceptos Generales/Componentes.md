Un **componente** es una pieza reutilizable de una interfaz que encapsula una responsabilidad determinada.

Una aplicación puede dividirse en un **árbol de componentes**, donde componentes grandes contienen componentes más pequeños.

```
App
├── Header
│   ├── Logo
│   └── NavMenu
├── Sidebar
└── Main
    ├── MensajeList
    └── CuadroDeTexto
```

Cada componente se ocupa de una parte determinada de la interfaz.

---

## Responsabilidad de un componente

Un componente normalmente se encarga de:

- Mostrar una parte de la interfaz.
- Mantener los datos necesarios para esa interfaz.
- Recibir acciones del usuario.
- Reaccionar a esas acciones.
- Comunicarse con otros componentes o servicios cuando sea necesario.
   
Por ejemplo:

```
LoginComponent
├── muestra el formulario
├── mantiene los datos ingresados
├── detecta el clic en "Ingresar"
└── comunica que el usuario quiere iniciar sesión
```

---

## ¿Cuándo crear un componente?

Conviene separar una parte de la interfaz cuando:

- Se reutiliza.
- Tiene una responsabilidad propia.  
- Tiene comportamiento propio.
- El componente actual se está volviendo demasiado grande. 

Por ejemplo:

```
ChatComponent
├── ConversacionListComponent
│   └── ConversacionItemComponent
├── BuscadorComponent
└── MensajesPanelComponent
```

Cada componente tiene una responsabilidad específica.

---

## Árbol de componentes

Los componentes pueden relacionarse como **padres e hijos**.

```
AppComponent
├── LoginComponent
└── ChatComponent
```

`AppComponent` es el padre.

`LoginComponent` y `ChatComponent` son hijos.

Esta relación permite que los componentes intercambien información.

Ver:

- [[Props]]
- [[Binding y Eventos]]
- [[Ciclo de Vida de Componentes]]
- [[Reactividad y Estado]]
- [[Renderizado]]
- [[Servicios]]

---
