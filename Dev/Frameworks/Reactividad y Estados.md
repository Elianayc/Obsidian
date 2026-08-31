La **reactividad** es el mecanismo mediante el cual un framework mantiene la **interfaz sincronizada con los datos** automáticamente.

El desarrollador declara **qué debe mostrarse**, y el framework se encarga de actualizar la interfaz cuando los datos cambian.

---

## Antes de los frameworks

Antes de utilizar frameworks, había diferentes formas de actualizar la interfaz:

- **Recargar la página:** el servidor genera nuevamente el HTML con los datos actualizados y el navegador recarga toda la página.
- **Reemplazar fragmentos de HTML:** se obtiene una parte actualizada del HTML y se reemplaza manualmente en el DOM.
- **Manipular el DOM con JavaScript:** se modifica el dato y también se actualiza manualmente el elemento correspondiente del DOM.

El problema es que en todos estos casos el desarrollador debe encargarse de **mantener sincronizados los datos y la interfaz**.

En aplicaciones grandes esto se vuelve difícil de mantener.

---

## Reactividad

Con reactividad:

**Estado cambia → framework detecta el cambio → UI se actualiza**

Por ejemplo, sin reactividad:

```Javascript
let contador = 0;

function incrementar() {
  contador++;
  document.getElementById('display').textContent = contador;
}
```

El DOM debe actualizarse manualmente cada vez que cambia `contador`.

Con reactividad, se establece una relación entre el dato y la interfaz:

```Javascript
contador = 0;
```

```HTML
<h1>Mi Contador</h1>
<p>{{ contador }}</p>
```

Cuando `contador` cambia, el framework actualiza automáticamente la parte de la interfaz que depende de ese dato.

No es necesario actualizar manualmente todo el DOM.

---

## ¿Cómo funciona la reactividad?

Los frameworks utilizan mecanismos diferentes para conseguir el mismo resultado.

### React y Vue: Virtual DOM

React y Vue utilizan un **Virtual DOM**, que es una representación del DOM mantenida en memoria.

Cuando cambia el estado:

1. Se genera un nuevo Virtual DOM.
2. Se compara con el anterior (**diffing**).
3. Se identifican los cambios necesarios.
4. Se aplican esos cambios al DOM real (**patching**).

```
Estado cambia
      ↓
Nuevo Virtual DOM
      ↓
Comparación con Virtual DOM anterior
      ↓
Se detectan diferencias
      ↓
Se actualiza el DOM real
```

### Angular: Change Detection

Angular **no utiliza Virtual DOM**.

Utiliza **Change Detection**, un mecanismo que detecta cambios en el estado de los componentes y actualiza el DOM de manera eficiente.

En versiones modernas de Angular también existen los **Signals**, que permiten una detección de cambios más granular.

Aunque la implementación es diferente, el concepto es el mismo:

> **Cambian los datos → la interfaz se actualiza automáticamente.**

---

# Estado

El **estado** es toda la información que un componente o una aplicación necesita **conocer o recordar** en un momento determinado para mostrar correctamente la interfaz.

Por ejemplo, en una aplicación de chat, el estado puede indicar:

- Qué usuario está logueado.
- Qué conversación está seleccionada.
- Qué mensajes tiene esa conversación.
- Si se están cargando datos.
- Si ocurrió algún error.

La relación entre estado y reactividad es:

```
Estado cambia
      ↓
Framework detecta el cambio
      ↓
UI se actualiza
```

---

# Estado Local

El **estado local** son los datos que pertenecen a un único componente.

Vive dentro de ese componente y desaparece cuando el componente se desmonta.

Puede incluir:

- **Datos de formularios:** texto escrito y valores de campos.
- **Estado de carga:** si se está esperando una respuesta.
- **Estado de error:** si ocurrió un error y qué mensaje mostrar.
- **Listas:** mensajes, conversaciones o resultados.
- **Estado de la UI:** menú abierto, pestaña activa o elemento seleccionado.

### Cómo se declara

**Angular**

```Typescript
text = '';
```

**React**

```Javascript
const [text, setText] = useState('');
```

**Vue**

```Javascript
const text = ref('');
```

Si un dato solamente lo necesita un componente, normalmente debe mantenerse como **estado local**.

---

# Estado local + Props

Cuando un componente hijo necesita información que pertenece al padre, el padre puede enviarle ese estado mediante **Props**.

```
Estado del padre cambia
        ↓
Framework detecta el cambio
        ↓
El padre se actualiza
        ↓
El hijo recibe el nuevo valor mediante Props
```

Por ejemplo, un componente `Composer` puede tener:

```Typescript
texto = '';
enviando = false;

enviar() {
  this.enviando = true;

  // llamada al servicio o API

  this.enviando = false;
  this.texto = '';
}
```

Y pasar `enviando` a un componente hijo:

```HTML
<app-boton-enviar
  [cargando]="enviando">
</app-boton-enviar>
```

El componente hijo recibe ese dato:

```Typescript
@Input() cargando: boolean = false;
```

Y lo utiliza para mostrar el estado correspondiente:

```HTML
<button [disabled]="cargando">
  {{ cargando ? 'Enviando...' : 'Enviar' }}
</button>
```

Así, cuando `enviando` cambia en el padre, el hijo recibe automáticamente el nuevo valor mediante Props.

---

# Estado Global

El **estado global** es un lugar centralizado donde se almacenan datos que necesitan **múltiples componentes**.

El principio es:

> **Un dato, un lugar, muchos consumidores.**

Por ejemplo:

```
App
├── Header
├── Sidebar
│   └── ConversacionItem
└── Main
    └── MensajesPanel
```

Varios componentes pueden necesitar información como:

```
Estado global
├── usuario
├── conversacionActiva
└── conversaciones
```

Si `Sidebar` cambia `conversacionActiva`, `MensajesPanel` puede detectar el cambio y actualizarse sin que los componentes intermedios tengan que pasar el dato mediante Props.

### Cómo se implementa

|  Framework  |             Mecanismo              |
| :---------: | :--------------------------------: |
| **Angular** | Servicios con `providedIn: 'root'` |
|  **React**  |            Context API             |
|   **Vue**   |               Pinia                |

**Importante:** estado global no significa que **todo** el estado deba ser global.

Si un dato solamente lo necesita un componente, conviene mantenerlo como **estado local**. El estado global se utiliza cuando realmente es necesario compartir información entre varios componentes.

---

# Conceptos adicionales

Son conceptos que pueden aparecer en proyectos reales a medida que crecen:

- **Provide / Inject:** permite compartir datos entre componentes de una misma rama del árbol sin pasar props por todos los componentes intermedios.
- **Contenedor / Presentacional:** separa componentes que manejan lógica y servicios de aquellos que solamente muestran datos.
- **Memoización:** evita cálculos o renderizados innecesarios cuando los datos relevantes no cambiaron.
- **Code splitting:** divide el código JavaScript en archivos más pequeños para cargar solamente lo necesario.
- **Lazy loading:** permite cargar el código de una ruta o funcionalidad únicamente cuando se necesita.
- **Inmutabilidad:** consiste en no modificar directamente determinados estados, sino reemplazarlos por una nueva versión. Es especialmente importante en React.

Estos conceptos son complementarios y suelen aparecer a medida que los proyectos aumentan de tamaño.

---

