Angular utiliza **servicios** para separar de los componentes lógica que no pertenece directamente a la interfaz.

Por ejemplo:

```
COMPONENTE
→ muestra datos
→ recibe acciones

SERVICIO
→ obtiene datos
→ procesa datos
→ se comunica con Backend
→ contiene lógica reutilizable
```

---

## `@Injectable`

Un servicio Angular puede declararse mediante:

```
@Injectable({
  providedIn: 'root'
})
export class ProductosService {
}
```

`@Injectable` indica que Angular puede administrar ese servicio mediante su sistema de **inyección de dependencias**.

---

## Inyección de dependencias

Un componente puede solicitar el servicio que necesita.

Por ejemplo:

```
constructor(
  private productosService: ProductosService
) {}
```

Angular proporciona la instancia correspondiente.

Conceptualmente:

```
COMPONENTE
    │
    │ necesita
    ▼
ProductosService
```

El componente no tiene que crear manualmente el servicio.

---

## Comunicación con el Backend

Un servicio puede realizar solicitudes HTTP.

El flujo habitual es:

```
COMPONENTE
    ↓
SERVICIO ANGULAR
    ↓
HTTP
    ↓
BACKEND
```

El componente solicita la información al servicio.

El servicio se encarga de comunicarse con el Backend.

---

## Ejemplo conceptual

```
export class ProductosComponent {

  constructor(
    private productosService: ProductosService
  ) {}

  cargarProductos() {
    this.productosService.obtenerProductos();
  }
}
```

La responsabilidad queda separada:

```
ProductosComponent
→ decide cuándo necesita productos

ProductosService
→ sabe cómo obtener los productos
```

---

## Servicios y Observables

Cuando un servicio utiliza `HttpClient`, Angular trabaja habitualmente con **Observables**.

Conceptualmente:

```
HttpClient
    ↓
Observable
    ↓
subscribe
├── next
├── error
└── complete
```

- `next` → llegó un valor.
    
- `error` → ocurrió un error.
    
- `complete` → terminó el flujo.
    

Ver [[RxJS y Observables en Angular]].

---

## En una arquitectura Frontend + Backend

```
USUARIO
   ↓
COMPONENTE
   ↓
SERVICIO ANGULAR
   ↓
HTTP
   ↓
BACKEND / BFF
   ↓
API EXTERNA / BASE DE DATOS
```

Es importante no confundir:

**Servicio Angular**  
→ pertenece al Frontend.

**Backend / BFF**  
→ es el servidor que recibe las solicitudes del Frontend.

El Backend puede aplicar lógica del lado servidor y comunicarse con APIs externas o bases de datos.

---
