**Angular** es un framework de desarrollo Frontend basado en [[Typescript]] y desarrollado por Google.

Permite construir aplicaciones web mediante una arquitectura basada en **componentes**.

---

## Conceptos principales

Angular proporciona mecanismos para:

- Crear componentes.
- Comunicar componentes.
- Realizar binding entre TypeScript y HTML.
- Renderizar contenido dinámicamente.
- Manejar eventos.
- Crear servicios.
- Navegar mediante rutas.
- Comunicarse mediante HTTP.
- Trabajar con asincronismo y Observables.

---

## Estructura básica

Una aplicación Angular puede pensarse inicialmente de esta forma:

```
index.html
    ↓
<app-root>
    ↓
AppComponent
    ↓
otros componentes
```

El navegador carga `index.html`.

Angular inicia la aplicación y monta el componente principal dentro de su **selector**.

Por ejemplo:

```
@Component({
  selector: 'app-root'
})
export class AppComponent {}
```

El selector:

```
app-root
```

permite utilizar el componente en HTML:

```
<app-root></app-root>
```

---

## Componentes

Los componentes representan partes de la interfaz.

Ver [[Componentes en Angular]].

---

## Comunicación entre componentes

Angular permite comunicar componentes padres e hijos mediante:

- `@Input()`
- `@Output()`
- `EventEmitter`
- Property binding `[ ]`
- Event binding `( )`

Ver [[Comunicación entre Componentes en Angular]].

---

## Binding

El **binding** es la forma en que Angular **conecta el HTML con el TypeScript**.

Las marcas indican **qué tipo de conexión se hace y en qué dirección**:

```
{{ }}   → TS → HTML    → mostrar un dato

[ ]     → TS → HTML    → asignar un dato a una propiedad

( )     → HTML → TS    → escuchar un evento y ejecutar una acción

[()]    → TS ↔ HTML    → mantener un dato sincronizado en ambos sentidos
```

#### Interpolación `{{ }}`

```
{{ displayName }}
```

Trae `displayName` del TypeScript y lo muestra en el HTML.

#### Property binding `[ ]`

```
[value]="displayName"
```

Toma `displayName` del TypeScript y lo asigna a la propiedad `value` del elemento HTML.

#### Event binding `( )`

```
(click)="guardar()"
```

Cuando ocurre el evento `click` en el HTML, ejecuta `guardar()` en el TypeScript.

#### Two-way binding `[()]`

```
[(ngModel)]="displayName"
```

Mantiene sincronizados el elemento HTML y `displayName`:

```
HTML ↔ TypeScript
```

Si cambia uno, se actualiza el otro.

---

## Directivas

Angular proporciona directivas que modifican el comportamiento o renderizado del HTML.

Ver [[Directivas en Angular]].

---

## Ciclo de vida

Los componentes Angular poseen hooks como:

```
ngOnInit
ngOnChanges
ngOnDestroy
```

Ver [[Ciclo de Vida en Angular]].

---

## Servicios

Angular utiliza servicios para separar lógica de los componentes.

Ver [[Servicios en Angular]].

---

## Routing

Angular incluye su propio sistema de routing.

Ver [[Routing en Angular]].

---

## HTTP y Observables

Los servicios Angular pueden utilizar `HttpClient` para realizar solicitudes HTTP.

`HttpClient` trabaja normalmente con **Observables**.

Ver [[RxJS y Observables en Angular]].

---

## Esquema general

```
USUARIO
   ↓
COMPONENTE
   ↓
SERVICIO ANGULAR
   ↓
BACKEND
   ↓
API / BASE DE DATOS
```

El componente se ocupa principalmente de la interfaz.

El servicio Angular permite separar la comunicación y lógica reutilizable.

El Backend procesa las solicitudes del Frontend y puede comunicarse con otros sistemas.

---

Temas Relacionados:

- [[Formularios Reactivos en Angular]]


----



