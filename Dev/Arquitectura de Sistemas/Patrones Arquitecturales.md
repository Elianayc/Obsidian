
> "Sin simplicidad en la arquitectura, no puede haber usabilidad."  
> — Robert C. Martin

## Introducción
Los **patrones arquitectónicos** son soluciones generales y reutilizables para problemas comunes relacionados con la organización y estructura de un sistema de software.

Determinan cómo se organizan los componentes de una aplicación, cómo interactúan entre sí y cómo se gestionan aspectos como la **escalabilidad, el mantenimiento y el rendimiento**.

La elección de un patrón arquitectónico adecuado es una decisión importante, ya que puede afectar todo el ciclo de vida de una aplicación.

Esta decisión debe considerar factores como:

- Tamaño del proyecto.
- Requisitos de escalabilidad.
- Complejidad del dominio.
- Equipo de desarrollo disponible.
- Tecnologías utilizadas.
    
---

## Principales enfoques arquitectónicos

Los **enfoques arquitectónicos** definen principalmente cómo se **organiza, estructura y despliega una aplicación**:

- [[Arquitectura Monolítica]] → **Cómo se despliega la aplicación:** toda la aplicación se despliega como una única unidad.

- [[Arquitectura en Capas]] → **Cómo se organiza internamente:** la aplicación se divide en capas según responsabilidades.

- [[Arquitectura de Microservicios]] → **Cómo se divide la aplicación:** se organiza en múltiples servicios independientes, generalmente orientados a dominios o funcionalidades específicas.

- [[Arquitectura REST]] → **Cómo se comunican los recursos:** estilo arquitectónico para diseñar sistemas de comunicación orientados a recursos, generalmente mediante HTTP.

> **Importante:** REST no es mutuamente excluyente con los otros enfoques. Puede utilizarse junto con cualquiera de ellos.

---

### Cómo se relaciona REST con los otros enfoques

- **Con arquitectura monolítica:** una aplicación monolítica puede exponer una **API REST** para comunicarse con clientes u otros sistemas.
- **Con arquitectura en capas:** REST puede implementarse como parte de la **capa de presentación** o mediante una **capa de API separada**.
- **Con microservicios:** REST puede utilizarse para la comunicación entre **microservicios** y con clientes externos.

---
