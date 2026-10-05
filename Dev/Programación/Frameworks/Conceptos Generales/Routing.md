El **routing** permite determinar qué vista o componente debe mostrarse según la URL.

Por ejemplo:

```
/login       → Login
/productos   → Productos
/perfil      → Perfil
```

---

## Routing en una SPA

En una **Single Page Application (SPA)** la navegación normalmente no recarga completamente la página.

El router detecta la URL y determina qué componente debe mostrarse.

```
URL
 ↓
ROUTER
 ↓
COMPONENTE
```

---

## Ruta

Una **ruta** establece la relación entre una URL y una vista.

Por ejemplo:

```
/productos → ProductosComponent
```

---

## Parámetros de ruta

Una ruta puede contener información dinámica.

Por ejemplo:

```
/productos/42
```

El `42` puede representar el identificador del producto.

---

## Navegación

El router también permite cambiar de ruta desde la aplicación.

```
usuario hace clic
       ↓
router
       ↓
cambia la URL
       ↓
se muestra otro componente
```

---

## Router outlet

Es el lugar de la interfaz donde el router coloca el componente correspondiente a la ruta activa.

Conceptualmente:

```
Aplicación
├── Header
├── Menú
└── Router Outlet
       ↓
   componente
   de la ruta
```

---

## Guards

Un **guard** permite comprobar una condición antes de permitir determinada navegación.

Por ejemplo:

```
usuario intenta entrar
        ↓
¿está autorizado?
   ↓           ↓
  sí           no
   ↓           ↓
entra       se bloquea
```

Cada framework implementa el routing de manera diferente.

Ver:

- [[Routing en Angular]]
- [[React]]
- [[Vue]]

---
