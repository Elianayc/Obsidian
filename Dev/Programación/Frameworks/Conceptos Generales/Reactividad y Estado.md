La **reactividad** permite mantener automáticamente sincronizados los datos de una aplicación con su interfaz.

La idea fundamental es:

```
CAMBIA UN DATO
      ↓
EL FRAMEWORK DETECTA EL CAMBIO
      ↓
SE ACTUALIZA LA INTERFAZ
```

Sin un sistema reactivo, el desarrollador tendría que modificar manualmente el DOM cada vez que cambia un dato.

---

# Estado

El **estado** es la información que una aplicación necesita recordar en un momento determinado.

Por ejemplo:

```
usuario
conversacionSeleccionada
mensajes
cargando
error
```

La interfaz puede depender de esos datos.

Por ejemplo:

```
cargando = true
       ↓
se muestra "Cargando..."
```

Cuando el estado cambia, la reactividad permite actualizar la interfaz.

---

## Estado local

El **estado local** pertenece a un componente determinado.

Por ejemplo:

```
BuscadorComponent
└── textoBuscado
```

Si solamente ese componente necesita el dato, normalmente no hace falta compartirlo con toda la aplicación.

---

## Estado compartido

Algunos datos necesitan ser utilizados por varios componentes.

Por ejemplo:

```
 usuarioLogueado
          │
   ┌───┼────┐
   ▼   ▼    ▼
Header Menu Perfil
```

En estos casos puede utilizarse algún mecanismo de estado compartido.

La implementación depende del framework.

---

## Estado y Props

Un componente padre también puede compartir parte de su estado con un hijo mediante [[Props]].

```
ESTADO DEL PADRE
       ↓
     PROPS
       ↓
COMPONENTE HIJO
```

---

## Idea principal

```
ESTADO
  ↓
REACTIVIDAD
  ↓
INTERFAZ
```

El estado representa los datos actuales.

La reactividad permite que los cambios de esos datos se reflejen en la interfaz.

---
