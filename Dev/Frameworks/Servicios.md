Un **servicio** es una clase o función con una **responsabilidad específica** que puede ser utilizada por distintos componentes.

Su objetivo principal es **separar la lógica de obtención y procesamiento de datos de la lógica de la interfaz**.

> **Idea clave:** el componente **muestra e interactúa**; el servicio **resuelve la lógica y obtiene los datos**.

---

## ¿Por qué utilizar servicios?

Un componente puede necesitar información proveniente de un **Backend o una API**. Obtener esos datos implica:

- Realizar llamadas HTTP.
- Esperar respuestas asincrónicas.
- Transformar los datos.
- Manejar errores.
- Reintentar operaciones si es necesario.

Si toda esta lógica se coloca dentro del componente, aparecen problemas:

- **Acoplamiento:** el componente queda demasiado ligado a la forma en que se obtienen los datos. Si cambia el Backend, hay que modificar los componentes.
- **Duplicación:** distintos componentes pueden realizar las mismas llamadas y mantener copias diferentes de los mismos datos.
- **Mantenimiento:** el código se vuelve más difícil de leer, probar y modificar.

Por eso, esta responsabilidad se extrae a un **servicio**.

---

## ¿Qué puede contener un servicio?

Un servicio puede encargarse de:

- **Llamadas HTTP** al Backend o APIs externas.
- **Estado compartido** entre componentes que no están directamente relacionados.
- **Transformación y procesamiento de datos.**
- **Lógica reutilizable** que necesitan varios componentes.

---

## Separación de responsabilidades

La idea es que cada parte tenga una responsabilidad clara:

```
Componente
    ↓
Solicita datos
    ↓
Servicio
    ↓
Backend / API
```

El componente **no necesita saber cómo se obtienen los datos**. Solo utiliza el servicio.

Esto permite que, si cambia el Backend, se modifique principalmente el servicio y no todos los componentes que utilizan esos datos.

---

# Servicios en Angular, React y Vue

Cada tecnología implementa esta separación de una manera diferente:

| Tecnología  |                   Forma habitual                    |
| :---------: | :-------------------------------------------------: |
| **Angular** |      Clases con **Inyección de Dependencias**       |
|  **React**  |   Funciones, hooks y mecanismos como **Context**    |
|   **Vue**   | Funciones o composables y mecanismos como **Pinia** |

### Angular

Angular utiliza servicios mediante clases y **Inyección de Dependencias**:

```Typescript
@Injectable({ providedIn: 'root' })
export class UserService {
  // lógica del servicio
}
```

Un componente puede recibir el servicio mediante el constructor:

```Typescript
@Component({
  // ...
})
export class ChatComponent {

  constructor(private userService: UserService) {}

}
```

Angular se encarga de proporcionar la instancia del servicio.

Cuando se utiliza:

```Typescript
@Injectable({ providedIn: 'root' })
```

el servicio queda disponible como una **instancia compartida a nivel de aplicación**, siguiendo el patrón **Singleton**.

---

### React

React no tiene un sistema de servicios equivalente al de Angular. Es habitual utilizar **funciones, hooks y Context** para separar y compartir la lógica.

Por ejemplo:

```Javascript
export function getUsers() {
  // llamada al Backend
}
```

Y un componente puede utilizar esa función:

```Javascript
const usuarios = await getUsers();
```

Para compartir estado entre componentes pueden utilizarse mecanismos como **Context API**.

---

### Vue

Vue también suele utilizar **funciones o composables** para separar la lógica:

```Javascript
export function getUsers() {
  // llamada al Backend
}
```

Para compartir estado entre componentes se puede utilizar **Pinia**.

---

# Servicios con Estado Global

Un servicio también puede mantener información que necesitan varios componentes.

Esto combina dos conceptos:

- **Servicio:** se encarga de obtener, transformar o gestionar los datos.
- **Estado global:** mantiene datos compartidos entre diferentes componentes.

Por ejemplo, después de iniciar sesión, el Backend puede devolver los datos del usuario:

```
Usuario logueado
       ↓
   AuthService
       ↓
Estado global
   ↙   ↓   ↘
Header Sidebar Perfil
```

De esta manera, los distintos componentes pueden acceder al mismo usuario sin tener que realizar nuevamente la misma llamada al Backend.

---

## Servicio con Estado Global en Angular

Angular puede combinar un servicio con un estado global:

```Typescript
@Injectable({ providedIn: 'root' })
export class AuthService {

  private usuario = signal(null);

  getUsuario() {
    return this.usuario();
  }

  login(user: Usuario) {
    this.usuario.set(user);
  }

  logout() {
    this.usuario.set(null);
  }
}
```

Como el servicio es una instancia compartida, los componentes que utilizan `AuthService` acceden al **mismo estado de usuario**.

---

## Servicio vs. Estado Global

Son conceptos relacionados, pero **no son lo mismo**:

- **No todo estado global tiene que ser un servicio.**
- **No todo servicio tiene que tener estado global.**

Un servicio puede simplemente encargarse de realizar llamadas al Backend.

Un estado global puede simplemente almacenar información compartida.

También pueden combinarse cuando resulta necesario.

---

