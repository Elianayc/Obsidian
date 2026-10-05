Un componente tiene un **ciclo de vida** desde que aparece en la aplicación hasta que deja de utilizarse.

Las etapas principales son:

```
CREACIÓN
   ↓
MONTAJE
   ↓
ACTUALIZACIONES
   ↓
DESMONTAJE
```

---

## Montaje

El componente se crea y aparece en la interfaz.
En esta etapa suelen realizarse tareas de inicialización.

Por ejemplo:

- Obtener datos.
- Inicializar valores.
- Crear determinadas suscripciones.
    

---

## Actualización

Mientras el componente existe, sus datos pueden cambiar.

Por ejemplo:

```
cambia un dato
      ↓
el framework detecta el cambio
      ↓
se actualiza la interfaz
```

Un componente puede actualizarse muchas veces durante su existencia.

---

## Desmontaje

Ocurre cuando el componente deja de formar parte de la interfaz.
En este momento puede ser necesario liberar recursos.

Por ejemplo:

- Cancelar suscripciones.
- Detener timers.
- Eliminar listeners.
   
---

## Hooks de ciclo de vida

Los frameworks proporcionan mecanismos que permiten ejecutar código automáticamente en determinados momentos del ciclo de vida.

Estos mecanismos suelen denominarse **hooks de ciclo de vida**.

Cada framework proporciona su propia implementación.

Ver:

- [[Ciclo de Vida en Angular]]
- [[React]]
- [[Vue]]

---
