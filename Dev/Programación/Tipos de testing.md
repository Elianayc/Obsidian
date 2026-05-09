---
tags:
  - Programación
  - ProgramaciónII
---

#### Según el enfoque
- **Caja negra**: se prueba el sistema como un todo sin conocer su implementación interna. Puede ser manual o automatizado.
- **Caja blanca**: se prueba el código interno del sistema. Requiere acceso al código fuente.
- **QA (Quality Assurance / Aseguramiento de calidad)**: proceso global de control de calidad del software, no solo pruebas sino también prevención de errores.


#### Según nivel de granularidad

- **Unit testing (pruebas unitarias)**: prueban funciones o métodos aislados.
    - Base del TDD (Test-Driven Development): desarrollo guiado por pruebas.

- **Integration testing (pruebas de integración)**: prueban la interacción entre distintos módulos del sistema. Generalmente se realizan como caja negra.

- **System testing (pruebas de sistema)**: prueban el sistema completo desde el punto de vista funcional. Generalmente caja negra.
    - **Smoke test**: pruebas rápidas para verificar que lo básico del sistema funciona.
    - **Functional testing**: pruebas de casos de uso o flujos específicos.

- **Regression testing (pruebas de regresión)**: aseguran que cambios en el código no rompan funcionalidades que ya funcionaban correctamente. Aplica a todos los niveles de integración.
