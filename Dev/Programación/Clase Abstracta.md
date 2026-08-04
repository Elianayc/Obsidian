---
tags:
  - Programación
  - ProgramaciónII
---
Una clase abstracta es una clase que **no puede ser instanciada directamente**.

Su objetivo es servir como **base para otras clases**, definiendo una estructura común.

**Puede contener:**
- [[Método Abstracto|Métodos abstractos]] (sin implementación)
- Métodos concretos (con implementación)
- Atributos

Representa características comunes necesarias para las subclases, pero no lo suficientemente específicas como para existir como objeto por sí misma.

> [!example]
> **Vehículo (concepto general)**
> - Auto
> - Camión
> - Bicicleta
> - Moto

> La palabra `super` se utiliza para acceder a la **clase padre desde una clase hija**, permitiendo invocar su **constructor** o sus **métodos heredados**.
#Programación