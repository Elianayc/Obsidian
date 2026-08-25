Un **requerimiento o requisito** es una característica o descripción de algo que el sistema debe hacer para satisfacer un objetivo. Debe ser **validado y documentado** junto con quien lo solicita.

Los requisitos definen **qué debe hacer el sistema y cómo debe hacerlo**:

- **Requerimientos funcionales (RF):** definen **qué** debe hacer el sistema.
- **Requerimientos no funcionales (RNF):** definen **cómo** debe hacerlo y qué propiedades o restricciones debe cumplir.

---

## Requerimientos funcionales

Definen los **servicios y comportamientos** que debe proporcionar el sistema. También pueden indicar lo que el sistema **no debe hacer**, siempre que represente un comportamiento funcional válido.

Pueden involucrar:

- Entradas.
- Procesamiento.
- Salidas.
- Interacciones con otros sistemas.
- Eventos o estímulos externos.
- Respuestas automáticas.
- Procesos predefinidos.

Las entradas no necesariamente provienen del usuario; también pueden originarse en otros sistemas, eventos externos o procesos automáticos.

---

### Especificación

Los requisitos pueden ser **inexactos, ambiguos o incompletos**, porque los usuarios pueden dar información por supuesta y los desarrolladores pueden interpretar un requisito ambiguo de la forma más simple.

El analista debe:

- No asumir ni inferir información.
- Validar lo entendido con el usuario.
- Detectar omisiones y ambigüedades.
- Documentar claramente.
- Dividir requisitos complejos en **subrequisitos** más fáciles de entender, desarrollar, probar, rastrear y entregar.

La especificación debe ser:

- **Completa:** todos los servicios solicitados están definidos.
- **Coherente:** no existen requisitos contradictorios.

**Ejemplo:**

> Como usuario, quiero que se muestre un tutorial al iniciar sesión por primera vez, para conocer el uso de cada opción de la pantalla de inicio.

Permite identificar:

- **Qué:** un tutorial.
- **Qué debe explicar:** las opciones de la pantalla.
- **Cuándo:** en el primer inicio de sesión.

También deben aclararse aspectos como si puede omitirse, repetirse o consultarse posteriormente.

---

## Requerimientos no funcionales

Definen **propiedades, restricciones o condiciones** del sistema y se enfocan en **cómo** debe realizar sus funciones.

Pueden referirse a:

- Rendimiento.
- Seguridad.
- Disponibilidad.
- Usabilidad.
- Fiabilidad.
- Portabilidad.
- Interoperabilidad.
- Mantenimiento.

Pueden surgir de necesidades de usuarios, restricciones presupuestarias, políticas organizativas, interoperabilidad, regulaciones de seguridad, privacidad y otros factores externos.

---

### Tipos

**Requisitos del producto:** especifican propiedades y comportamiento del producto, como rendimiento, velocidad, memoria, fiabilidad, portabilidad y usabilidad.

**Requisitos organizativos:** derivan de políticas, estándares y procedimientos de la organización, como procesos, lenguajes de programación, implementación, fechas de entrega y documentación.

**Necesidades externas:** derivan de factores externos e incluyen:

- **Interoperabilidad:** interacción con otros sistemas.
- **Legales:** normas que debe cumplir.
- **Éticos:** condiciones necesarias para su aceptación por los usuarios.

---

### Especificación de RNF

Definir RNF cuantitativamente puede ser difícil porque los clientes no siempre pueden convertir sus objetivos en métricas.

Por eso deben **documentarse cuidadosamente** y analizarse con las áreas involucradas en soporte, calidad, buenas prácticas y estándares.

Un RNF puede abordarse durante **cualquier fase del proyecto**, incluso antes del desarrollo o durante el mantenimiento.

**Mal ejemplo:**

> El sistema debe ser seguro.

Es ambiguo porque no define qué significa seguro, en qué situaciones, qué normativa aplica, dónde debe aplicarse ni qué comportamiento se espera.

Un RNF mal definido puede generar una implementación **problemática, costosa y lenta**.

**Buen ejemplo:**

> Todas las comunicaciones externas entre los servidores de datos, la aplicación y el cliente deben estar cifradas utilizando RSA.

Es preciso porque define:

- **Qué:** comunicaciones externas.
- **Qué deben hacer:** estar cifradas.
- **Cómo:** utilizando RSA.

---

## Relación con las Historias de Usuario

Las **Historias de Usuario** expresan necesidades del usuario y pueden dar origen a requisitos funcionales y no funcionales.

Por ejemplo:

> Como usuario, quiero que la aplicación sea fácil de usar, para no pasar mucho tiempo aprendiendo.

Plantea un posible **RNF de usabilidad**, pero debe especificarse para determinar:

- Para quién debe ser fácil.
- Cómo se medirá.
- Cómo se comprobará.
- Contra qué criterios se evaluará.

---

## Relación con los usuarios

Los requisitos surgen de las **necesidades de los usuarios y otras partes interesadas**, por lo que deben identificarse y validarse mediante la comunicación entre usuarios, analistas y equipo técnico.

→ **Usuarios del Sistema**

---
