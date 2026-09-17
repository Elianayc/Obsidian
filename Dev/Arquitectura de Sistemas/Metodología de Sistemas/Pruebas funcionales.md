Las **pruebas funcionales** verifican si el sistema se comporta de acuerdo con los **requisitos funcionales** especificados, validados y consensuados.

Algunos tipos son:

---

### Caja negra

El tester no necesita conocer la implementación interna del sistema.

Se centra en el comportamiento observable a partir de entradas y salidas.

---

### Caja blanca

El tester conoce la estructura interna y lógica del software.

Permite verificar ramas, caminos y estructuras internas del código.

---

### Pruebas ad hoc

Se intenta encontrar errores sin seguir casos de prueba o documentación previamente definida.

Son improvisadas y pueden utilizar variaciones de pruebas existentes.

La evidencia debe documentarse después de la ejecución, explicando cómo se encontró el defecto para facilitar el feedback al equipo de desarrollo.

---

### Pruebas de API

Verifican que las interfaces entre componentes funcionen de manera correcta y confiable.

Son importantes para garantizar la comunicación entre diferentes componentes de software.

---

### Pruebas exploratorias

Permiten descubrir escenarios difíciles de predecir y errores ocultos.

No utilizan casos de prueba completamente predefinidos. El tester explora, aprende, diseña y ejecuta pruebas de manera iterativa.

Se pueden dividir en tres actividades relacionadas:

- **Aprendizaje:** comprender la aplicación y su contexto.
- **Diseño:** decidir cómo realizar la exploración.
- **Ejecución:** realizar las pruebas y aprender de los resultados.

Buscan responder preguntas como:

- ¿La aplicación realiza la función para la que fue diseñada?
- ¿Funciona en diferentes escenarios?
- ¿Tiene un rendimiento adecuado?
- ¿Qué errores potenciales existen?

---

### Pruebas de regresión

Verifican que los cambios realizados en el software no afecten negativamente funcionalidades que anteriormente funcionaban.

Se realizan después de:

- Correcciones de errores.
- Nuevas funcionalidades.
- Mejoras.
- Cambios de versión.
- Migraciones de entorno.

Su objetivo es comprobar que las pruebas que anteriormente eran exitosas continúen siéndolo.

Es recomendable ejecutarlas periódicamente y pueden automatizarse.

---

### Pruebas de aceptación del usuario (UAT)

Son realizadas por usuarios finales para verificar que el sistema satisface sus necesidades en **escenarios reales de negocio** y está preparado para pasar a producción.

Un caso UAT debe incluir:

- Descripción.
- Pasos a seguir.
- Resultado esperado.
- Resultado real.
- Nombre del tester.
- Fecha.
- Estado: aprobado o fallido.
- Comentarios o errores encontrados.

---

