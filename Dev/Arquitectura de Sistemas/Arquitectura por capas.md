---
tags:
---
La arquitectura en capas es un modelo de organización del software que divide un sistema en **niveles con responsabilidades claramente separadas**. 

Cada capa se encarga de una parte específica del funcionamiento del sistema y solo interactúa con las capas necesarias según su posición en la estructura.

El objetivo principal de este enfoque es **reducir el acoplamiento entre componentes**, mejorar la **mantenibilidad** del código y facilitar su **evolución**. 

Al separar responsabilidades, se evita que una misma parte del sistema se encargue simultáneamente de la **interfaz de usuario**, la **lógica de negocio** y el **almacenamiento de datos**.

Este enfoque permite que cada capa pueda modificarse o evolucionarse con menor impacto en las demás, siempre que se respeten los contratos entre ellas.

---

# Capas

### 1. Presentación
Responsable de la interacción con el usuario y la entrada/salida de información.

### 2. Lógica de negocio
Donde se aplican las reglas del dominio y se define el comportamiento del sistema.

### 3. Datos
Encargada de la persistencia y recuperación de información.

### 4. Modelo
Donde se definen las entidades y estructuras que representan el dominio del problema.

---

> [!example]
> #### Ejemplo aplicado al sistema de inmobiliaria
> 
> En un sistema de gestión de inmuebles, la arquitectura en capas se puede aplicar de la siguiente manera:
> 
>---
>
> **Presentación:**
>     - index.ts
>       
>     Se encarga de iniciar el sistema, crear instancias y mostrar resultados.
> 
>---
>
> **Lógica de negocio:**
>     - InmobiliariaService.ts
>       
>     Se encarga de validar inmuebles, aplicar reglas del sistema y coordinar operaciones.
>
>---
>     
> **Datos:**
>     - InmuebleRepository.ts
>       
>     Se encarga de almacenar los inmuebles en memoria y recuperarlos cuando sea necesario.
>
>---
>     
> **Modelo:**
>     - Inmueble
>     - Casa
>     - Departamento
>     - Contacto
>     - Dirección
>     - Ambiente
>     
>     Representan las entidades del dominio y sus atributos.
>
>---
> 
> **Flujo general del sistema:**
>  
> ```mermaid
> %%{init: {
   'theme': 'dark',
   'themeVariables': {
                        'background': '#121212',
                        'lineColor': '#a5d7f7',
                        'fontFamily': 'Cascadia Code, Fira Code, Consolas, Courier New, monospace',
                        'fontSize': '14px'
        },
        'themeCSS': 'path { stroke-width: 1.5px !important; }'
    } }%%
>flowchart TD
>A[Presentation<br/>index.ts]
>B[Business<br/>Service]
>C[Data<br/>Repository]
>D[Model]
>A --> B --> C --> D
>%%Colores de las clases
>classDef default fill:#362b2b,stroke:#f39bce,color:#e4dcd2
> ```
> 
 
---
#ArquitecturadeSistemas
