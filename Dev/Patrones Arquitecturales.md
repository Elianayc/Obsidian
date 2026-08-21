
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

## Principales patrones arquitectónicos

- [[Arquitectura Monolítica]]
- [[Arquitectura en Capas]]
- [[Arquitectura de Microservicios]]

Cada arquitectura presenta **ventajas, desventajas y casos de uso** diferentes.

---

# Comparación de enfoques arquitectónicos

Los siguientes enfoques pueden **combinarse** y no representan necesariamente alternativas excluyentes.

Por ejemplo, una aplicación puede tener una **arquitectura monolítica**, estar organizada **en capas** y utilizar una **API REST** para comunicarse con otros sistemas.

Por eso, la comparación sirve para distinguir sus características, pero no significa que haya que elegir uno solo.

> [!important]
>Monolítica, En Capas y Microservicios son **patrones arquitectónicos** que definen principalmente cómo se organiza y estructura una aplicación. 
>
>**REST**, en cambio, es un **estilo arquitectónico para diseñar sistemas de comunicación orientados a recursos**, generalmente mediante HTTP. 
> 
>Por eso REST puede utilizarse junto con cualquiera de los otros enfoques.

|             Criterio             |       Monolítica        | En Capas  | Microservicios |      REST      |
| :------------------------------: | :---------------------: | :-------: | :------------: | :------------: |
|     **Complejidad inicial**      |          Baja           |   Media   |      Alta      |     Media      |
|        **Escalabilidad**         |        Limitada         | Moderada  |      Alta      |      Alta      |
| **Tiempo de desarrollo inicial** |         Rápido          |   Medio   |     Lento      |     Medio      |
| **Mantenibilidad a largo plazo** | Disminuye con el tamaño |   Buena   |     Buena      |     Buena      |
|     **Tolerancia a fallos**      |          Baja           |   Media   |      Alta      |      Alta      |
|   **Flexibilidad tecnológica**   |          Baja           |   Media   |      Alta      |      Alta      |
|     **Curva de aprendizaje**     |          Baja           |   Media   |      Alta      |     Media      |
|  **Costos de infraestructura**   |          Bajos          |  Medios   |     Altos      |     Medios     |
| **Facilidad de refactorización** | Disminuye con el tiempo |   Media   |      Alta      |     Media      |
|    **Coherencia del código**     |          Alta           |   Alta    |    Variable    |     Media      |
|   **Estándares / principios**    |        Variables        | Definidos |   Variables    | Bien definidos |
|         **Orientación**          |        Funcional        | Por capas |  Por dominio   |  Por recursos  |

---

## Relación entre enfoques
Una misma aplicación puede combinar diferentes enfoques. 

> [!example]
> **Arquitectura de una aplicación:**
> 
>```
> Arquitectura Monolítica
>         │
>         ├── Capa de Presentación
>         ├── Capa de Negocio
>         └── Capa de Datos
>                  │
>                  └── API REST
> ```
> 
> En este caso:
> 
> - **Monolítica** → define que toda la aplicación se despliega como una única unidad.
> - **En Capas** → define cómo se organiza internamente el código.
> - **REST** → define cómo se diseñan los recursos y la comunicación mediante una API.
> 
> También podría utilizarse **Microservicios + REST**, donde cada microservicio es independiente y expone sus funcionalidades mediante APIs REST.

---

### Idea clave

**No hay que elegir entre Monolítica, Capas y REST como si fueran opciones excluyentes.** Responden a preguntas diferentes:

- **¿Cómo se despliega la aplicación?** → Monolítica / Microservicios.
- **¿Cómo se organiza internamente?** → En Capas.
- **¿Cómo se comunican los recursos?** → REST.

---

