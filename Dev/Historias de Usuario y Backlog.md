Las **Historias de Usuario** permiten transformar necesidades del negocio en funcionalidades concretas que aporten valor al usuario.

No son simples frases: son **vehículos de entendimiento compartido** entre el negocio y el equipo técnico. Son dinámicas y evolucionan mediante conversaciones, refinamiento y validación.

> Una buena historia de usuario es una conversación que evoluciona hacia un compromiso concreto entre lo que el negocio necesita y lo que el equipo puede entregar.
> — Mike Cohn (2004)

---

## Estructura de una Historia de Usuario

El formato básico es:

> **Como [rol], quiero [funcionalidad], para [beneficio].**

Una historia efectiva debe incluir:

- **Descripción:** qué necesita el usuario.
- **Reglas de negocio:** condiciones o reglas que deben respetarse.
- **Criterios de aceptación:** condiciones que deben cumplirse para considerar terminada la historia.
- **Criterios de rechazo:** condiciones que indican que la funcionalidad no debe aceptarse.

---

## Criterios INVEST

INVEST es una guía para evaluar la calidad de una Historia de Usuario y determinar si está lista para ser trabajada por el equipo.

- **I — Independent (Independiente):** debe poder desarrollarse y entregarse sin depender de otras historias.
- **N — Negotiable (Negociable):** no es un contrato fijo. Su detalle y alcance pueden ajustarse mediante conversación entre el equipo y el cliente/Product Owner.
- **V — Valuable (Valiosa):** debe aportar valor real al usuario o al negocio.
- **E — Estimable (Estimable):** el equipo debe poder estimar el esfuerzo necesario. Si no puede, puede ser demasiado grande, ambigua o faltar conocimiento.
- **S — Small (Pequeña):** debe ser lo suficientemente pequeña para completarse en un sprint. Las historias grandes o épicas deben dividirse.
- **T — Testable (Testeable):** debe poder verificarse si está completa o no, mediante criterios de aceptación claros.

### ¿Por qué INVEST es una buena práctica?

- Mejora la calidad del backlog.
- Reduce malentendidos, retrabajo y bloqueos.
- Facilita la planificación de los sprints.
- Fomenta la colaboración entre negocio y desarrollo.
- Reduce el desperdicio al evitar funcionalidades innecesarias o imposibles de verificar.

### Ejemplo

> **Como usuario registrado, quiero poder restablecer mi contraseña por email, para recuperar el acceso a mi cuenta si la olvido.**

- **Independent:** no depende de otras historias.
- **Negotiable:** el flujo exacto puede ajustarse.
- **Valuable:** permite recuperar el acceso.
- **Estimable:** el equipo puede dimensionar el trabajo.
- **Small:** puede completarse en un sprint.
- **Testable:** se puede verificar que el email llegue y que el enlace funcione.

---

## Criterios de aceptación

Los **criterios de aceptación** son las condiciones que debe cumplir una funcionalidad para ser aceptada por el usuario, cliente u otros sistemas.

Describen el **resultado final esperado**, no el proceso técnico utilizado para conseguirlo.

Deben:

- Definirse antes de comenzar a desarrollar la historia.
- Ser claros.
- Ser concisos.
- Ser verificables.
- Estar orientados a resultados.
- Permitir determinar si la historia fue completada correctamente.

### Historia de Usuario vs. Criterios de Aceptación

La **Historia de Usuario** expresa la necesidad de alto nivel.

Los **criterios de aceptación** especifican las condiciones que deben cumplirse para considerar satisfecha esa necesidad.

Una historia puede dividirse en diferentes criterios de aceptación que permitan comprobar su cumplimiento.

### Ejemplo

**Historia:**

> Como analista de pagos, quiero importar órdenes desde Excel, para reducir errores.

**Reglas de negocio:**

- El archivo debe utilizar el formato oficial.
- Los montos deben ser positivos.
- El proveedor debe existir.

**Criterios de aceptación:**

- Validar los datos del archivo.
- Mostrar una vista previa.
- Generar un reporte de errores.

**Criterios de rechazo:**

- Formato inválido.
- Proveedor inexistente.
- Montos negativos.

---

## Refinamiento de una Historia de Usuario

La historia evoluciona mediante un proceso de conversación y validación:

1. **Capturar la necesidad.**
2. **Explorarla conjuntamente.**
3. **Reformularla** como historia + reglas + criterios.
4. **Validarla** entre negocio, equipo y líder.
5. **Revisarla después de la entrega.**

> Las historias de usuario son promesas de conversación.
> — Alistair Cockburn (2002)

---

## Roles y vínculos

En el desarrollo de una Historia de Usuario participan distintos roles:

- **Usuario experto de negocio:** expresa la necesidad y las reglas del negocio.
- **Product Owner (PO):** representa al negocio, traduce la necesidad en valor y prioriza.
- **Equipo técnico:** analiza, estima y construye la solución.
- **Líder de proyecto / Scrum Master:** facilita el proceso y la comunicación.
- **QA / Tester:** realiza las pruebas y valida los criterios de aceptación y rechazo.

La colaboración entre estos roles permite mantener el foco en el valor que se quiere entregar.

---

## Product Backlog

El **Product Backlog** es un instrumento vivo que contiene y organiza el trabajo que el equipo debe realizar para generar valor.

No es simplemente una lista de tareas: evoluciona a medida que aumenta el conocimiento del negocio y del equipo.

El **Product Owner** es responsable de mantenerlo actualizado y priorizado.

Los elementos del backlog pueden incluir:

- Épicas.
- Features.
- Historias de Usuario.

### Del requerimiento al Product Backlog

El proceso parte de una necesidad o problema del negocio:

**Requerimiento → Épica → Feature → Historia de Usuario → Product Backlog**

Cada nivel reduce la abstracción y aumenta el detalle hasta llegar a algo que pueda construirse y probarse.

---

## Niveles de backlog

### Requerimiento de negocio

Es la **necesidad original** del cliente o stakeholder.

Ejemplo:

> "Necesitamos que los usuarios puedan autenticarse de forma segura."

Indica **qué necesita lograr la organización**, pero no cómo construirlo.

### Épica

Es una necesidad o funcionalidad demasiado grande para completarse en un solo sprint.

Representa un objetivo funcional de alto nivel.

Ejemplo:

> "Gestión completa de autenticación de usuarios."

### Feature

Es una **capacidad concreta y entregable** que se desprende de una épica.

Ejemplo:

> "Autenticación con redes sociales."

### Historia de Usuario

Es una funcionalidad pequeña y concreta que puede completarse en un sprint.

Ejemplo:

> "Como usuario, quiero iniciar sesión con mi cuenta de Google, para no tener que recordar una contraseña nueva."

La Historia de Usuario es la **unidad mínima de valor testeable**.

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

Estas historias pueden distribuirse en diferentes **sprints**.

---

## Refinamiento continuo del Product Backlog

El backlog debe:

- Revisarse constantemente.
- Ajustarse y detallarse.
- Mantenerse alineado con los objetivos del negocio.
- Generar espacios de conversación y aprendizaje conjunto.

---

## Entrega de valor

Entregar valor no significa simplemente entregar una funcionalidad.

El objetivo es generar un **impacto positivo para el usuario o el proceso**.

Por ejemplo:

> Una validación automática puede reducir errores y aumentar la confianza en el sistema.

La definición del valor se consensúa entre los participantes correspondientes del proceso, como usuario, Product Owner y Scrum Master.

---

## Sprint

Un **Sprint** es un ciclo de trabajo en el que el equipo desarrolla un conjunto de funcionalidades con el objetivo de entregar un **incremento funcional y útil** al finalizarlo.

- Duración recomendada: **2 semanas**.
- En proyectos más complejos puede extenderse hasta **3 semanas**.
- Cada sprint debe generar un incremento de valor.
- Las historias seleccionadas deben poder completarse dentro del sprint.

---

## Errores frecuentes

- Tratar el backlog como una simple lista de tareas.
- Confundir deseos con requerimientos.
- No validar el valor entregado con el negocio.
- No realizar revisiones ni aprendizajes.
- Crear historias demasiado grandes.
- Crear historias sin criterios claros.

---

## Buenas prácticas

- Mantener el backlog visible y compartido.
- Redactar los ítems con propósito y lenguaje común.
- Promover el feedback continuo del usuario.
- Mantener las historias pequeñas, claras y testeables.
- Mantener el backlog alineado con los objetivos del negocio.
- Reconocer los logros del equipo para reforzar la motivación.

---
