---
tags:
  - Programación
  - ProgramaciónII
---
Es la capacidad de una clase derivada de **redefinir un método heredado de la clase padre** para modificar su comportamiento.

Esto permite que distintas clases hijas respondan de forma diferente al mismo método, lo cual es una base del **polimorfismo**.

La sobreescritura debe respetar la **misma firma del método** (nombre, parámetros y tipo de retorno).

> En TypeScript, la palabra clave `override` no es obligatoria, pero se recomienda usarla para mayor claridad y seguridad.

Incluso cuando se aplica **upcasting**, si un método fue sobrescrito, se ejecutará la versión de la clase hija en tiempo de ejecución por polimorfismo.
