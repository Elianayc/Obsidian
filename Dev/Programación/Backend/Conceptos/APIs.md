---
tags:
  - ArquitecturadeSistemas
---
**API** significa **Application Programming Interface** (_Interfaz de Programación de Aplicaciones_).

Una API es una **interfaz que permite la comunicación entre diferentes aplicaciones, sistemas o componentes de software**. Define un conjunto de reglas que indica cómo un sistema puede solicitar información o utilizar funcionalidades proporcionadas por otro sistema.

La API funciona como un **intermediario** entre el sistema que realiza una solicitud y el sistema que proporciona la información o funcionalidad. El sistema que utiliza la API no necesita conocer cómo está implementada internamente la funcionalidad que está utilizando.

---

<div style="text-align: center;">

<iframe width="560" height="315" src="https://www.youtube.com/embed/IwnIxk8DdHs?start=12" title="YouTube video" frameborder="0" allowfullscreen></iframe>

</div>

---

## ¿Para qué sirve?

Una API permite:

- Facilitar la **interoperabilidad** entre diferentes aplicaciones y sistemas.
- Permitir que distintos componentes de software se comuniquen.
- Acceder a **datos o funcionalidades** de otro sistema de una forma definida.
- Separar la implementación interna de un sistema de los programas que lo utilizan.
- Reutilizar funcionalidades sin tener que implementarlas nuevamente en cada aplicación.
    
---

## Funcionamiento básico

La comunicación mediante una API puede representarse de la siguiente manera:

```text
Cliente → Solicitud → API → Sistema
Cliente ← Respuesta ← API ← Sistema
```

El **cliente** realiza una solicitud a la API.

La API recibe esa solicitud, la comunica al sistema correspondiente y devuelve una respuesta al cliente.

Por ejemplo, una aplicación puede utilizar una API para consultar información almacenada en otro sistema sin acceder directamente a su base de datos.

---

## API como contrato

Una API puede entenderse como un **contrato de comunicación** entre sistemas.

Define qué funcionalidades están disponibles y establece cómo deben solicitarse. De esta manera, los sistemas pueden comunicarse siguiendo reglas conocidas, independientemente de cómo esté implementada internamente cada parte.

---

## API y backend

En una aplicación web, es habitual que el frontend utilice una API para comunicarse con el backend.

```text
Frontend
   ↓
  API
   ↓
Backend
```

De esta manera, el frontend no necesita acceder directamente a la lógica interna o a la base de datos del backend.

---

## Tipos de APIs

Existen diferentes tipos de APIs según la tecnología utilizada y el contexto en el que se emplean.

Algunos ejemplos son:

- **[[APIs REST]]:** utilizan los principios del estilo arquitectónico REST.
    
- **APIs SOAP:** utilizan SOAP (_Simple Object Access Protocol_) para la comunicación.
    
- **APIs GraphQL:** permiten que el cliente especifique qué datos necesita obtener.
    

Las APIs también pueden clasificarse según quién puede utilizarlas, por ejemplo, como APIs públicas, privadas o internas.

---