Los **criterios de aceptación** son condiciones que permiten validar si una historias de usuario fue implementada correctamente.

Ayudan:

- Al desarrollador, a implementar la funcionalidad correctamente.
- Al equipo de **QA**, a verificar que la funcionalidad cumpla lo requerido.
- A determinar cuándo una historia de usuario puede considerarse completa.

Los criterios de aceptación, junto con el título de la historia, deben definir claramente la funcionalidad que se debe implementar.

---

## Características

- **Atomicidad:** cada criterio debe tener únicamente dos resultados posibles: **éxito o fracaso**. No existe un éxito parcial.
- **No ambiguos:** deben poder interpretarse de una única manera, evitando expresiones subjetivas.
- **Verificables:** deben poder ser comprobados rápidamente por el cliente o el equipo de QA.
- **Completos:** el conjunto de criterios debe contemplar todos los requisitos funcionales de la historia.

---

## Ejemplo

**Historia de usuario:**

> Como enfermera, quiero acceder a la agenda de enfermería de forma segura, para verificar la disponibilidad horaria del personal.

**Criterios de aceptación:**

- El nombre de usuario debe tener un valor.
- El nombre de usuario debe tener formato de email.
- La contraseña debe tener un valor.
- El nombre de usuario debe coincidir con el registrado en la base de datos.
- Si el usuario y la contraseña son correctos, debe permitirse el acceso a la aplicación y a la pantalla **Agenda**.
- La información de la Agenda debe mostrarse según los permisos del usuario autenticado.

---

