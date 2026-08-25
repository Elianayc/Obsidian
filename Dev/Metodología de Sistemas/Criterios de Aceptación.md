Los **criterios de aceptación** son condiciones que permiten validar si una **Historia de Usuario** fue implementada correctamente.

Ayudan:

- Al desarrollador, a implementar la funcionalidad correctamente.
- Al equipo de **QA**, a verificar que la funcionalidad cumpla lo requerido.
- A determinar cuándo una Historia de Usuario puede considerarse completa.

Los criterios de aceptación, junto con la historia de usuario, deben definir claramente la funcionalidad que se debe implementar.

Describen el **resultado final esperado**, no el proceso técnico utilizado para conseguirlo.

Deben definirse **antes de que el [[equipo de desarrollo]] comience a trabajar** en la historia.

---

## Características

Los criterios de aceptación deben ser:

- **Claros:** sencillos y fáciles de entender para todos los miembros del equipo.
- **Concisos:** comunican la información necesaria sin detalles innecesarios.
- **Atómicos:** cada criterio debe tener únicamente dos resultados posibles: **éxito o fracaso**. No existe un éxito parcial.
- **No ambiguos:** deben poder interpretarse de una única manera, evitando expresiones subjetivas.
- **Verificables:** deben poder ser comprobados rápidamente por el cliente o el equipo de QA.
- **Completos:** el conjunto de criterios debe contemplar todos los requisitos funcionales de la historia.
- **Orientados a resultados:** deben enfocarse en el resultado útil para el usuario.

Los criterios de aceptación son **únicos para cada Historia de Usuario** y definen el comportamiento esperado desde la perspectiva del usuario final.

---

## Historia de Usuario vs. Criterios de Aceptación

La **Historia de Usuario** expresa la necesidad de [[alto nivel]].

Los **criterios de aceptación** especifican las condiciones que deben cumplirse para considerar satisfecha esa necesidad.

Por ejemplo:

> **Historia:** Como usuario, quiero poder filtrar los resultados de búsqueda por fecha, precio y ubicación.

Los criterios de aceptación podrían especificar qué filtros deben aparecer y qué resultado debe obtenerse al utilizarlos.

Los criterios de aceptación describen **qué resultado debe obtenerse**, pero no detallan **cómo debe programarse**.

---

## Ejemplo — Acceso a la agenda

**Historia de Usuario:**

> Como enfermera, quiero acceder a la agenda de enfermería de forma segura, para verificar la disponibilidad horaria del personal.

**Criterios de aceptación:**

- El nombre de usuario debe tener un valor.
- El nombre de usuario debe tener formato de email.
- La contraseña debe tener un valor.
- El nombre de usuario debe coincidir con el registrado en la base de datos.
- Si el usuario y la contraseña son correctos, debe permitirse el acceso a la aplicación y a la pantalla **Agenda**.
- La información de la Agenda debe mostrarse según los permisos del usuario autenticado.

---

## Ejemplo — Área de Pagos

**Historia de Usuario:**

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

## Ejemplo — Portal de Beneficios

**Historia de Usuario:**

> Como usuario, quiero ver mi historial de solicitudes, para hacer seguimiento.

**Regla de negocio:**

- La consulta histórica se alimenta de otra aplicación.

**Criterios de aceptación:**

- Mostrar la lista de solicitudes.
- Permitir aplicar filtros.
- Actualizar la información automáticamente.

**Criterios de rechazo:**

- No existen registros disponibles.
- Se produce un error de [[backend]].

---

## Validación

Los criterios de aceptación deben permitir comprobar objetivamente si la Historia de Usuario está completa.

El **QA / Tester** los utiliza durante las pruebas para validar que la funcionalidad cumple con lo acordado.

Por eso, una buena Historia de Usuario debe estar acompañada por criterios de aceptación **claros, completos y verificables**.

---
