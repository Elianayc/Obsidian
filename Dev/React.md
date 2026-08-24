**React** es una **biblioteca de JavaScript** desarrollada originalmente por Facebook (actualmente Meta) para crear **interfaces de usuario**.

Se utiliza principalmente en el **Frontend web** y permite construir interfaces mediante **componentes reutilizables**.

---

## Características principales

- Utiliza una arquitectura basada en **componentes**.
- Los componentes suelen definirse como **funciones que devuelven JSX**.
- Permite reutilizar elementos de la interfaz.
- Utiliza **props** para pasar datos de un componente padre a un componente hijo.
- Permite renderizar **listas** mediante `.map()`.
- Utiliza `key` para identificar los elementos de una lista y optimizar su actualización.
- Permite realizar **renderizado condicional** mediante `if` o expresiones condicionales.
- Facilita la creación de interfaces **interactivas y reactivas**.
- Puede utilizarse para desarrollar aplicaciones web de una sola página (**SPA**).
- El **routing** puede implementarse mediante bibliotecas como **React Router**.

---

## Componentes

Un componente React suele ser una **función** que recibe datos y devuelve la interfaz mediante **JSX**.

```typescript
function Mensaje({ autor, contenido }) {
  return (
    <div className="mensaje">
      <span>{autor}</span>
      <p>{contenido}</p>
    </div>
  );
}
```

---

## Props

Las **props** permiten pasar datos desde un componente padre hacia un componente hijo.

```
Componente padre
      ↓
    props
      ↓
Componente hijo
```

El hijo recibe las props y no debería modificarlas directamente.

---

## Renderizado de listas

Las listas pueden generarse utilizando `.map()`:

```typescript
{mensajes.map(msg => (
  <Mensaje
    key={msg.id}
    autor={msg.autor}
    contenido={msg.contenido}
  />
))}
```

La propiedad **`key`** permite identificar cada elemento de la lista para que React pueda actualizar correctamente los elementos que cambian.

---

## Renderizado condicional

Permite mostrar diferentes elementos según una condición.

Por ejemplo:

```typescript
{cargando && <div>Cargando...</div>}
```

---

## Routing

React no incluye un sistema de routing completo en su núcleo. Para manejar la navegación entre vistas puede utilizarse **React Router**.

Permite definir rutas como:

```
/login
/chat
/chat/:id
```

y navegar entre ellas sin recargar toda la página.

---

## Ejemplo

Una aplicación puede tener componentes independientes para el **menú, formulario de inicio de sesión, lista de productos y carrito de compras**, que pueden reutilizarse y combinarse para construir la interfaz completa.

---
