Las **props** son el mecanismo utilizado para pasar datos desde un componente padre hacia un componente hijo.

El flujo de datos es **unidireccional**, de arriba hacia abajo:

```text
App
 ↓ props
ConversacionList
 ↓ props
ConversacionItem
```

Esto permite:

- Hacer el código más predecible.
    
- Rastrear fácilmente de dónde proviene cada dato.
    
- Evitar que los componentes hijos modifiquen directamente los datos del padre.
    

Una **prop no debería modificarse desde el hijo**.

Si un hijo necesita comunicar información o una acción al padre, utiliza **eventos**.

Esta filosofía es compartida por Angular, React y Vue.

---
