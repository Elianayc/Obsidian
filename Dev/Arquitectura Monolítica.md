La **Arquitectura Monolítica** es un enfoque en el que todos los componentes de una aplicación, como la **interfaz, lógica de negocio y acceso a datos**, forman una **única unidad** que se desarrolla y despliega conjuntamente.

Los módulos pertenecen a la misma aplicación y pueden comunicarse entre sí.

![[Pasted image 20260821121028.png]]

---

## Características

- **Estructura unificada:** toda la aplicación forma un único bloque.
- **Base de código compartida:** los módulos comparten el mismo repositorio.
- **Despliegue único:** se despliega toda la aplicación como una unidad.
- **Tecnología homogénea:** generalmente utiliza un mismo lenguaje y framework.

---

## Ventajas

- **Simplicidad de desarrollo:** fácil de comenzar y organizar inicialmente.
- **Facilidad de depuración:** permite seguir el flujo de ejecución de forma directa.
- **Buen rendimiento:** la comunicación entre módulos es eficiente.
- **Despliegue sencillo:** se implementa un único artefacto.

---

## Desventajas

- **Escalabilidad limitada:** es necesario escalar toda la aplicación.
- **Mayor complejidad:** el código puede volverse difícil de mantener al crecer.
- **Menor flexibilidad tecnológica:** dificulta incorporar tecnologías diferentes en partes específicas.
- **Despliegues más largos:** un cambio puede requerir reconstruir toda la aplicación.
- **Menor disponibilidad:** un fallo puede afectar a toda la aplicación.

---

## Casos de uso

- Aplicaciones pequeñas o medianas.
- **MVPs** y proyectos en etapas iniciales.
- Equipos pequeños.
- Aplicaciones donde el rendimiento sea prioritario.

---

## Ejemplo

Una aplicación de blog que incluye **creación de contenido, autenticación y administración**, desarrollada como una única aplicación con **Ruby on Rails, Django o Laravel**.

---

