---
tags:
  - ArquitecturadeSistemas
---
Las **Historias de Usuario** son un elemento clave de las metodologías ágiles. Permiten transformar necesidades del negocio en funcionalidades concretas que aporten **valor al usuario**.

No son simples frases: son **vehículos de entendimiento compartido** entre el negocio y el equipo técnico. Evolucionan mediante conversaciones, refinamiento y validación.

---

## Estructura de una Historia de Usuario

El formato básico es:

> **Como [rol], quiero [funcionalidad], para [beneficio].**

Permite identificar:

- **Quién:** el usuario o rol que necesita la funcionalidad.
- **Qué:** la acción o funcionalidad que necesita.
- **Para qué:** el beneficio o valor esperado.

**Ejemplo:**

> **Como cliente, quiero poder buscar transacciones, para detectar gastos innecesarios en mi cuenta.**

Una historia puede complementarse con:

- **Descripción:** contexto y detalles de la necesidad.
- **Reglas de negocio:** condiciones que deben respetarse.
- [[Criterios de Aceptación]]: condiciones que permiten verificar que la funcionalidad fue implementada correctamente.
- Diseños o mockups.
- User flows.
- Limitaciones.

---

## Criterios INVEST

**INVEST** es una guía para evaluar la calidad de una Historia de Usuario y determinar si está lista para ser trabajada.

- **I — Independent (Independiente):** debe poder desarrollarse y entregarse sin depender de otras historias.
- **N — Negotiable (Negociable):** no es un contrato fijo. Su detalle puede ajustarse mediante conversación entre el equipo y el Product Owner.
- **V — Valuable (Valiosa):** debe aportar valor real al usuario o al negocio.
- **E — Estimable (Estimable):** el equipo debe poder estimar el esfuerzo necesario. Si no puede, puede ser demasiado grande, ambigua o faltar conocimiento.
- **S — Small (Pequeña):** debe ser suficientemente pequeña para completarse en un sprint. Las historias demasiado grandes deben dividirse.
- **T — Testable (Testeable):** debe poder verificarse mediante criterios de aceptación claros.

### Beneficios de INVEST

- Mejora la calidad del backlog.
- Reduce malentendidos y retrabajo.
- Facilita la planificación de los sprints.
- Favorece la colaboración entre negocio y desarrollo.
- Evita funcionalidades difíciles de verificar o innecesarias.

---

## Refinamiento de una Historia de Usuario

Una historia evoluciona mediante conversación y validación:

1. **Capturar la necesidad.**
2. **Explorarla** conjuntamente.
3. **Reformularla** como historia + reglas + criterios.
4. **Validarla** entre negocio y equipo.
5. **Revisarla y ajustarla** a medida que aumenta el conocimiento.

> Las historias de usuario son promesas de conversación.  
> — Alistair Cockburn

---

## Roles y vínculos

En el desarrollo de una Historia de Usuario participan diferentes roles:

- **Usuario experto de negocio:** expresa la necesidad y las reglas del negocio.
- **Product Owner (PO):** representa al negocio, prioriza y busca maximizar el valor del producto.
- **Equipo técnico:** analiza, estima y construye la solución.
- **Scrum Master:** facilita la colaboración y ayuda a eliminar impedimentos.
- **QA / Tester:** verifica la funcionalidad mediante pruebas y criterios de aceptación.

La **colaboración entre estos roles** permite comprender la necesidad, construir la solución y validar que entregue el valor esperado.

---

# Product Backlog

El **Product Backlog** es un instrumento vivo que contiene y organiza el trabajo necesario para desarrollar y mejorar el producto.

No es simplemente una lista de tareas: evoluciona a medida que aumenta el conocimiento del negocio y del equipo.

El **Product Owner** es responsable de su gestión y priorización.

Puede contener:

- Épicas.
- Features.
- Historias de Usuario.
- Otros elementos necesarios para desarrollar y mantener el producto.

---

## Del requerimiento al Product Backlog

Una necesidad del negocio puede descomponerse progresivamente:

**Requerimiento → Épica → Feature → Historia de Usuario → Product Backlog**

Cada nivel reduce la abstracción y aumenta el detalle hasta llegar a funcionalidades que puedan construirse y probarse.

### Requerimiento de negocio

Representa la **necesidad original** del cliente o stakeholder.

> "Necesitamos que los usuarios puedan autenticarse de forma segura."

Indica qué necesita lograr la organización, pero no cómo construirlo.

### Épica

Es una funcionalidad o necesidad **demasiado grande para completarse en un solo sprint** y debe dividirse en elementos más pequeños.

> "Gestión completa de autenticación de usuarios."

### Feature

Es una **capacidad concreta del producto** que se desprende de una épica.

> "Autenticación con redes sociales."

### Historia de Usuario

Es una funcionalidad pequeña y concreta que puede desarrollarse y probarse dentro de un sprint.

> "Como usuario, quiero iniciar sesión con mi cuenta de Google, para no tener que recordar una contraseña nueva."

---

## Ejemplo de descomposición

**Requerimiento:**

> "Necesitamos agilizar las aprobaciones."

↓

**Épica:**

> "Automatización de flujos de aprobación."

↓

**Historias de Usuario:**

> "Como supervisor, quiero aprobar desde el móvil."

> "Como analista, quiero recibir notificaciones cuando el pago esté listo."

Las historias pueden distribuirse en diferentes **sprints**.

---

## Refinamiento continuo del Product Backlog

El backlog debe:

- Revisarse constantemente.
- Ajustarse y detallarse.
- Mantenerse alineado con los objetivos del negocio.
- Incorporar nuevos conocimientos y cambios.
- Priorizar los elementos según su valor.

---

## Entrega de valor

Entregar valor no significa simplemente entregar una funcionalidad.

El objetivo es generar un **impacto positivo para el usuario o el negocio**.

Por ejemplo:

> Una validación automática puede reducir errores y aumentar la confianza en el sistema.

El **Product Owner** busca maximizar el valor del producto teniendo en cuenta las necesidades de usuarios y stakeholders.

---

## Sprint

Un **Sprint** es un ciclo de trabajo en el que el equipo desarrolla un conjunto de funcionalidades con el objetivo de entregar un **incremento funcional y útil**.

- Tiene una duración fija de hasta **un mes**.
- Es habitual utilizar Sprints de **1 a 4 semanas**.
- Las historias seleccionadas deben poder completarse dentro del Sprint.
- Al finalizar, debe existir un incremento que cumpla con la **Definition of Done**.

---

## Errores frecuentes

- Tratar el backlog como una simple lista de tareas.
- Confundir deseos con requerimientos.
- No validar el valor entregado con el negocio.
- Crear historias demasiado grandes.
- Crear historias sin criterios claros.
- No revisar ni actualizar el backlog.
- Escribir historias desde la perspectiva del sistema en lugar de la del usuario.

---

## Buenas prácticas

- Mantener el backlog visible y actualizado.
- Utilizar lenguaje común entre negocio y desarrollo.
- Promover el feedback continuo.
- Mantener las historias pequeñas, claras y testeables.
- Definir criterios de aceptación claros.
- Mantener el backlog alineado con los objetivos del negocio.
- Refinar las historias antes de incorporarlas a un Sprint.

---

