Las **pruebas de software** son el proceso de evaluar y verificar que un componente o aplicación funciona correctamente, de forma **segura y eficiente**, de acuerdo con sus requisitos.

Sus principales beneficios son:

- Detectar errores.
- Mejorar el rendimiento.
- Aumentar la confiabilidad.
- Entregar software de mayor calidad.
- Reducir riesgos y costos.

---

## Importancia de las pruebas

Los defectos de software pueden provocar:

- Retrasos en las entregas.
- Daños en la reputación de una organización.
- Frustración e insatisfacción de los usuarios.
- Fallos en sistemas interconectados.
- Pérdidas económicas.

Las pruebas tempranas permiten detectar problemas antes de que el producto llegue al mercado, como:

- Defectos de arquitectura.
- Decisiones de diseño incorrectas.
- Funcionalidades inválidas.
- Vulnerabilidades de seguridad.
- Problemas de escalabilidad.

Cuanto antes se detecten los problemas, más fácil y económico resulta corregirlos.

Las pruebas son especialmente importantes al integrar software de terceros en sistemas complejos o críticos.

---

## Evolución de las pruebas de software

### Depuración y control de calidad

Inicialmente, la **depuración ([[debugging]])** era el principal método para encontrar y corregir errores.

Durante la década de 1980, las pruebas comenzaron a adoptar una visión más amplia, incorporando el **control y la garantía de calidad** como parte fundamental del desarrollo.

Las pruebas pasaron a integrarse al **[Ciclo de Vida del Desarrollo de Software (SDLC)](Ciclo%20de%20Vida%20del%20Desarrollo%20de%20Software)**.

### Caja negra y caja blanca

Durante los años 70 se sistematizaron dos enfoques:

- **Caja negra:** se prueba el sistema desde afuera, sin conocer su código interno. Se analizan principalmente entradas y salidas.
- **Caja blanca:** se prueba teniendo en cuenta la estructura interna, lógica, ramas y caminos del código.

Glenford Myers también planteó que el programador no debería ser necesariamente quien pruebe su propio código, debido al posible sesgo al buscar errores en algo que él mismo desarrolló.

### Automatización

Durante los años 80 y 90 aparecieron herramientas de automatización para poder ejecutar pruebas repetitivas a mayor escala.

### Agile y TDD

Con el **Manifiesto Ágil de 2001**, desarrollo y [[testing]] dejaron de verse como etapas completamente separadas.

Kent Beck formalizó el **Test-Driven Development (TDD)**, donde se escribe primero la prueba y luego el código necesario para hacerla pasar.

### DevOps y [[testing]] continuo

Con **CI/CD (Integración Continua y Entrega o Despliegue Continuo)**, las pruebas pasaron a formar parte de un flujo permanente.

Actualmente las pruebas pueden ser:

- Continuas.
- Automatizadas.
- Integradas durante todo el desarrollo.
- Ejecutadas en diferentes entornos.

---

## Inteligencia artificial en las pruebas

La IA generativa utiliza aprendizaje automático, [[procesamiento]] del lenguaje natural y análisis predictivo para optimizar las pruebas.

Algunos usos son:

### Generación de casos de prueba

Puede generar casos a partir de:

- Requisitos.
- [[Historias de usuario]].
- Código fuente.

También puede detectar escenarios límite (_edge cases_) que podrían pasar desapercibidos.

### Automatización

Puede generar scripts de prueba a partir de descripciones en lenguaje natural y convertir flujos de usuario en pruebas de regresión automatizadas.

### Análisis de código y detección de bugs

Puede detectar:

- Vulnerabilidades.
- Errores lógicos.
- Problemas de rendimiento.

También puede sugerir correcciones y explicar las causas de los fallos.

### Pruebas de UI y UX

Puede analizar interfaces para detectar inconsistencias visuales y generar pruebas de accesibilidad, por ejemplo utilizando **WCAG**.

---

## Pruebas manuales y automatizadas

Las pruebas se pueden realizar principalmente de dos formas:

### Pruebas manuales

Los testers o desarrolladores ejecutan los casos de prueba sin herramientas de automatización.

Simulan la interacción de un usuario:

- Hacer clic.
- Introducir información.
- Verificar resultados.

Son útiles especialmente para:

- Pruebas exploratorias.
- Pruebas de usabilidad.
- Aplicaciones pequeñas.

### Pruebas automatizadas

Utilizan scripts y herramientas para ejecutar pruebas automáticamente.

Son especialmente útiles para:

- Pruebas repetitivas.
- Sistemas grandes.
- Pruebas que deben ejecutarse muchas veces.

Permiten aumentar la velocidad y consistencia, reducir errores humanos y mejorar la eficiencia.

---

## Niveles de pruebas

Las pruebas pueden realizarse en diferentes niveles del **[Ciclo de Vida del Desarrollo de Software (SDLC)](Ciclo%20de%20Vida%20del%20Desarrollo%20de%20Software)**:

### Pruebas unitarias

Validan que cada **unidad de software**, es decir, el componente comprobable más pequeño de una aplicación, funcione correctamente.

### Pruebas de integración

Verifican que diferentes componentes o [[funciones]] funcionen correctamente **en conjunto**.

### Pruebas de sistema

Evalúan el funcionamiento integral del sistema.

Pueden incluir:

- Pruebas funcionales.
- Pruebas no funcionales.
- Pruebas de [[interfaz]].
- Pruebas de estrés.
- Pruebas de recuperación.

### Pruebas de aceptación

Verifican que el sistema satisfaga las necesidades y expectativas del usuario o cliente.

---

## Pruebas funcionales

Las **pruebas funcionales** verifican si el sistema se comporta de acuerdo con los **requisitos funcionales** especificados, validados y consensuados.

Algunos tipos son:

### Caja negra

El tester no necesita conocer la implementación interna del sistema.

Se centra en el comportamiento observable a partir de entradas y salidas.

### Caja blanca

El tester conoce la estructura interna y lógica del software.

Permite verificar ramas, caminos y estructuras internas del código.

### Pruebas ad hoc

Se intenta encontrar errores sin seguir casos de prueba o documentación previamente definida.

Son improvisadas y pueden utilizar variaciones de pruebas existentes.

La evidencia debe documentarse después de la ejecución, explicando cómo se encontró el defecto para facilitar el feedback al [[equipo de desarrollo]].

### Pruebas de API

Verifican que las interfaces entre componentes funcionen de manera correcta y confiable.

Son importantes para garantizar la comunicación entre diferentes componentes de software.

### Pruebas exploratorias

Permiten descubrir escenarios difíciles de predecir y errores ocultos.

No utilizan casos de prueba completamente predefinidos. El tester explora, aprende, diseña y ejecuta pruebas de manera iterativa.

Se pueden dividir en tres actividades relacionadas:

- **Aprendizaje:** comprender la aplicación y su contexto.
- **Diseño:** decidir cómo realizar la exploración.
- **Ejecución:** realizar las pruebas y aprender de los resultados.

Buscan responder preguntas como:

- ¿La aplicación realiza la [[función]] para la que fue diseñada?
- ¿Funciona en diferentes escenarios?
- ¿Tiene un rendimiento adecuado?
- ¿Qué errores potenciales existen?

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

## Pruebas no funcionales

Las **pruebas no funcionales** evalúan propiedades y restricciones del sistema, como rendimiento, seguridad, disponibilidad y comportamiento bajo diferentes condiciones.

### Pruebas de recuperación

Verifican cómo responde el sistema ante fallos y si puede recuperar correctamente sus datos y procesos.

**Ejemplo:** provocar una caída del servidor y comprobar que la base de datos se restaure correctamente y el sistema vuelva a funcionar.

### Pruebas de rendimiento

Evalúan el comportamiento del software bajo diferentes cargas de trabajo.

Analizan:

- Velocidad.
- Tiempo de respuesta.
- Estabilidad.
- Consumo de recursos.

Permiten detectar cuellos de botella y verificar que el sistema soporte la cantidad esperada de usuarios o [[transacciones]].

### Pruebas de compatibilidad

Comprueban que el software funcione correctamente en diferentes:

- Navegadores.
- Sistemas operativos.
- Hardware.
- Configuraciones [[de red]].
- Dispositivos.

---

## Pruebas de carga y estrés

### Pruebas de carga

Verifican que el sistema pueda manejar la **cantidad esperada de usuarios, datos o [[transacciones]]** sin degradar su rendimiento.

Permiten evaluar:

- Rendimiento.
- Escalabilidad.
- Fiabilidad.
- Estabilidad.
- Cuellos de botella.

Para realizarlas se deben:

1. Definir las métricas.
2. Crear escenarios realistas.
3. Ejecutar cargas crecientes.
4. Monitorear el comportamiento.
5. Analizar los resultados.

### Pruebas de estrés

Llevan al sistema **más allá de las condiciones normales de funcionamiento** para determinar cuánto puede soportar antes de fallar.

Se pueden simular:

- Tráfico extremo.
- Picos de usuarios.
- Agotamiento de recursos.
- Cargas excesivas.

Permiten identificar:

- Límites del sistema.
- Vulnerabilidades.
- Cuellos de botella.
- Puntos de fallo.
- Capacidad de recuperación.
- Problemas de integridad de datos.

---

## Pruebas de seguridad

Buscan detectar vulnerabilidades y garantizar la protección del sistema.

### Application Security [[Testing]] (AST)

Se enfoca específicamente en las **aplicaciones**, incluyendo aplicaciones web, móviles y APIs.

Analiza:

- Código.
- Dependencias.
- Configuraciones.
- Comportamiento durante la ejecución.

Busca amenazas como:

- Inyección.
- Autenticación insegura.
- Configuraciones incorrectas.
- Exposición de información confidencial.

### Software Security [[Testing]] (SST)

Tiene un alcance más amplio e incluye componentes como:

- Bibliotecas de código abierto.
- Sistemas operativos.
- Componentes de terceros.
- Infraestructura.

También contempla:

- Seguridad de la cadena de suministro.
- Cumplimiento normativo.
- Dependencias vulnerables.

**Diferencia principal:**

- **AST →** seguridad de la aplicación.
- **SST →** seguridad del ecosistema de software en general.

Ambos enfoques pueden combinarse para obtener una protección integral.

---

## Pruebas de usabilidad

Evalúan qué tan correctamente un usuario puede utilizar la [[interfaz]] para completar una tarea de manera eficaz.

Buscan:

- Detectar fallos de diseño.
- Identificar áreas de mejora.
- Optimizar la experiencia del usuario.
- Crear interfaces intuitivas y fáciles de utilizar.

### Beneficios

- Detectar problemas de diseño tempranamente.
- Reducir retrabajo.
- Mejorar la satisfacción del usuario.
- Mejorar la experiencia general.
- Fundamentar decisiones de diseño.
- Reducir riesgos antes del lanzamiento.

### Pruebas cualitativas y cuantitativas

**Cualitativas:** buscan comprender las razones detrás del comportamiento del usuario.

Utilizan datos no numéricos, como:

- Observaciones.
- Entrevistas.
- Comentarios.
- Percepciones.
- Sentimientos.

Permiten comprender **por qué** ocurre determinado comportamiento.

**Cuantitativas:** recopilan datos numéricos, como:

- Tasas de éxito.
- Tasas de error.
- Promedios.
- Métricas de rendimiento.

Permiten analizar patrones, comparar resultados y trabajar con muestras grandes.

**Ventaja:** son escalables y producen resultados medibles.

**Desventaja:** pueden no explicar las razones profundas detrás del comportamiento.

---

## Buenas prácticas de [[testing]]

Una estrategia de pruebas debe comenzar con un **plan de pruebas sólido** que defina:

- Alcance.
- Enfoque.
- Recursos.
- Actividades de validación.

Es recomendable utilizar un marco de pruebas que permita:

- Automatización.
- Validación continua.
- Diseño de pruebas.
- Ejecución.
- Análisis de resultados.

También son importantes las **revisiones de código**, porque permiten detectar defectos y aplicar estándares antes de las pruebas.

### Seguimiento de errores

El seguimiento de defectos permite:

- Registrar errores.
- Medir su impacto.
- Analizar problemas relacionados.
- Mejorar la calidad del software.

### Métricas e informes

Permiten comunicar:

- Estado de las pruebas.
- Objetivos.
- Resultados.
- Estado general del proyecto.

Los dashboards pueden reunir estas métricas y facilitar el seguimiento del proyecto.

---

## [[Relación]] con otros conceptos

Las pruebas verifican que lo definido en los **[Requerimientos](Requerimientos.md)** se cumpla correctamente.

En metodologías ágiles, los **[[Criterios de Aceptación]]** permiten definir qué debe verificarse para considerar terminada una historia de usuario.

Por eso, una cadena lógica sería:

**[[Requerimientos]] → [[Historias de Usuario]] → [[Criterios de Aceptación]] → Pruebas → Validación**

Y dentro de las pruebas:

**Pruebas funcionales → verifican qué hace el sistema**

**Pruebas no funcionales → verifican cómo se comporta y qué propiedades cumple**