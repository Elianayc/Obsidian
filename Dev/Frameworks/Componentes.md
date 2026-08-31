Un **componente** es una pieza reutilizable e independiente de la interfaz que encapsula **estructura, lógica y, opcionalmente, estilo**.

Una aplicación puede dividirse en un **árbol de componentes**, donde componentes grandes contienen componentes más pequeños.

```text
App
├── Header
│   ├── Logo
│   └── NavMenu
├── Sidebar
│   ├── ConversacionItem
│   └── ConversacionItem
└── Main
    ├── MensajeList
    └── CuadroDeTexto
```

### Características de un buen componente

- **Una responsabilidad:** hace una cosa y la hace bien.
    
- **Reutilizable:** puede utilizarse en distintos contextos y con distintos datos.
    
- **Encapsulado:** sus detalles internos no afectan a quien lo utiliza.
    
- **Predecible:** ante el mismo input produce el mismo resultado.
    

Un componente puede entenderse de forma similar a una **función**: recibe datos de entrada, ejecuta lógica interna y produce un resultado visible en la interfaz.

---

# ¿Cuándo crear un componente?

Conviene extraer una parte de la interfaz a un componente separado cuando:

- **Se repite:** el mismo bloque HTML aparece varias veces.
    
- **Es demasiado grande:** puede contener más de una responsabilidad.
    
- **Tiene lógica propia:** posee estado o comportamiento independiente.
    
- **Es reutilizable:** puede utilizarse en diferentes contextos con distintos datos.
    

### Ejemplo

Un componente de chat que hace todo:

```text
ChatComponent
├── lista de conversaciones
├── cada ítem de conversación
├── buscador
└── panel de mensajes
```

Puede dividirse en componentes con responsabilidades específicas:

```text
ChatComponent
├── ConversacionListComponent
│   └── ConversacionItemComponent
├── BuscadorComponent
└── MensajesPanelComponent
```

**Regla práctica:** si para describir lo que hace un componente necesitás utilizar la palabra **“y”**, probablemente tenga más de una responsabilidad y convenga dividirlo.

---

- [[Props]] 
- [[Renderizado de listas]]
- [[Routing]]
- [[Ciclo de Vida de los Componentes]]
- [[Binding y Eventos]]
- [[Reactividad y Estados]]
- [[Servicios]]

---

