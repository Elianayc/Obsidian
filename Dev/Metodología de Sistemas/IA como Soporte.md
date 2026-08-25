La **Inteligencia Artificial (IA)** puede utilizarse como herramienta de apoyo durante la gestión de [[Requerimientos]], la elaboración de [[Historias de Usuario]], la definición de [[Criterios de Aceptación]], el [[Pruebas de Software|testing]] y la documentación de un proyecto de software.

La IA permite **acelerar tareas y generar propuestas**, pero el criterio profesional del analista sigue siendo necesario para validar que la información sea correcta y corresponda al contexto real del negocio.

---

## IA en la gestión de requerimientos

La IA puede ayudar a:

- Generar borradores de **historias de usuario**.
- Detectar ambigüedades.
- Sugerir **criterios de aceptación**.
- Reformular requisitos mal escritos.
- Resumir reuniones de relevamiento.
- Generar plantillas de requerimientos.
- Traducir necesidades técnicas.
- Organizar el backlog.

### Ejemplo de prompt

> "Soy analista de sistemas. Tengo este requerimiento: [texto]. Reescribilo como historia de usuario con criterios de aceptación claros y medibles. Indicá si hay ambigüedades que deba resolver antes."

La IA puede:

- Reformular el requerimiento como historia de usuario.
- Identificar términos vagos como **"seguro", "rápido" o "fácil"**.
- Proponer criterios de aceptación concretos y medibles.

Pero la IA **no puede hacer por sí sola**:

- Conocer el contexto real del negocio.
- Validar la necesidad con el usuario final.
- Detectar todas las restricciones organizacionales.
- Conocer las políticas específicas de la empresa.

Por eso, el resultado generado por IA debe ser **revisado y validado por el analista**.

---

## IA en la generación de casos de prueba

La IA también puede utilizarse para generar propuestas de pruebas a partir de requisitos o historias de usuario.

Puede ayudar a:

- Generar casos de prueba funcionales.
- Proponer escenarios difíciles de predecir.
- Crear escenarios de **UAT (User Acceptance Testing)**.
- Detectar vulnerabilidades conocidas.
- Generar casos de validación de campos y formatos.
- Proponer escenarios básicos desde la perspectiva del usuario.

### Ejemplo de prompt

> "Generá casos de prueba para este requerimiento: [texto]. Incluí casos funcionales, al menos un caso no funcional de rendimiento y dos escenarios difíciles de predecir que podrían pasarse por alto en un testing básico."

Sin embargo, la IA puede omitir:

- Situaciones difíciles de predecir del negocio real.
- Escenarios de seguridad específicos.
- Casos relacionados con sistemas heredados.
- Particularidades de integración entre sistemas.

Por eso, los casos generados por IA también necesitan **revisión y validación humana**.

---

## Uso crítico y responsable de la IA

La IA es una herramienta de apoyo, pero tiene limitaciones.

### La IA no valida con el usuario real

Puede generar una historia de usuario perfecta en cuanto a su forma, pero vacía o incorrecta en cuanto al contenido si no recibe suficiente contexto del negocio.

### La IA puede alucinar

Puede generar requisitos o casos de prueba que parecen correctos, pero que **no corresponden al sistema real**.

Por eso, siempre hay que verificar sus resultados.

### La IA no conoce todas las restricciones

No necesariamente conoce:

- Sistemas utilizados por la organización.
- ERP existente.
- Presupuesto disponible.
- Estándares legales.
- Políticas internas.
- Restricciones técnicas.

### El rol del analista cambia, pero no desaparece

El analista pasa de escribir todo desde cero a tener que saber:

- **Qué pedirle a la IA.**
- **Cómo evaluar lo que devuelve.**
- **Qué información falta.**
- **Qué debe corregirse.**
- **Qué debe validarse con el usuario.**

Esto requiere **criterio profesional**.

---

## Caso práctico: TurnoYa

**TurnoYa** es un sistema para digitalizar los turnos de una clínica que actualmente trabaja mediante teléfonos y cuadernos.

El sistema debe atender las necesidades de **pacientes, médicos y administración**.

### Pacientes

Necesitan:

- Sacar turnos sin llamar.
- Ver sus turnos.
- Cancelar turnos.
- Recibir recordatorios.

**Contexto:** muchos pacientes son adultos mayores que no utilizan aplicaciones habitualmente.

### Médicos

Necesitan:

- Ver la agenda del día.
- Bloquear días de ausencia.
- Consultar el historial del paciente.

**Contexto:** cada especialidad puede tener diferentes reglas de disponibilidad.

### Administración

Necesita:

- Obtener reportes de ocupación mensual.
- Gestionar ausencias de médicos.
- Controlar cancelaciones.

**Contexto:** el sistema debe convivir con el teléfono durante el período de transición.

El objetivo es utilizar IA para **relevar requerimientos y generar casos de prueba**, pero posteriormente analizar y validar los resultados.

---

## Evaluación del resultado de la IA

Al utilizar IA para un proyecto, no alcanza con aceptar automáticamente lo que genera.

Se debe analizar:

1. **Qué está bien.**
2. **Qué falta.**
3. **Qué debe corregirse.**
4. **Qué escenarios no contempló.**
5. **Si el resultado puede validarse en el sistema real.**

Un caso particularmente importante es encontrar situaciones que la IA no haya previsto, especialmente aquellas relacionadas con las **reglas reales del negocio**.

El resultado puede clasificarse como:

- **Aprobado:** el resultado es correcto y suficiente.
- **Aprobado con reparos:** sirve como base, pero necesita correcciones.
- **Rechazado:** el resultado no es confiable o no se adapta al sistema.

---

## Relación con los requerimientos y testing

La IA puede intervenir en diferentes momentos del proceso:

**Requerimientos → Historias de Usuario → Pruebas de Software → IA como soporte**

La IA puede ayudar a **generar, analizar y mejorar** los elementos de cada etapa, pero no reemplaza la validación humana.

---

