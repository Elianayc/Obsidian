---
tags:
  - ArquitecturadeSistemas
---
La **Arquitectura en Capas** organiza el software en diferentes niveles de abstracción, donde cada capa tiene una **responsabilidad específica** y se comunica principalmente con las capas adyacentes.

Su objetivo es **separar responsabilidades**, reducir el acoplamiento y facilitar el mantenimiento y evolución del sistema.

A diferencia de la arquitectura monolítica, existe una **regla de comunicación entre capas**: una capa debe solicitar servicios a la capa inmediatamente inferior y **no puede acceder directamente a capas inferiores no adyacentes**.

El procesamiento de una solicitud puede involucrar a **todas o casi todas las capas**, ya que cada una utiliza los servicios de la capa inmediatamente inferior para completar la operación.

![[Pasted image 20260821121524.png|718]]

---

## Características

- **Organización jerárquica:** cada capa tiene responsabilidades específicas.
- **Comunicación restringida:** las capas se comunican principalmente con las adyacentes.
- **Abstracciones progresivas:** cada capa proporciona servicios a la capa superior.
- **Despliegue flexible:** puede implementarse como un monolito o distribuirse en diferentes servicios.

---

## Capas típicas

### 1. Presentación
Se encarga de la **interacción con el usuario** y de presentar la información.

**Responsabilidades:**
- Capturar entradas del usuario.
- Mostrar información.
- Realizar validaciones básicas.
- Comunicarse con la capa de aplicación.

Debe evitar contener lógica de negocio.

---

### 2. Aplicación
Coordina las operaciones y **orquesta los casos de uso** de la aplicación.

**Responsabilidades:**
- Coordinar flujos de trabajo.
- Implementar casos de uso.
- Transformar datos entre capas.
- Coordinar diferentes servicios o componentes.

Debe mantenerse relativamente delgada y delegar las reglas de negocio a la capa de dominio.

---

### 3. Dominio / Negocio
Contiene la **lógica de negocio central**, las reglas y las entidades principales del sistema.

**Responsabilidades:**
- Implementar reglas de negocio.
- Definir comportamientos y estados válidos.
- Aplicar validaciones complejas.
- Representar el dominio del problema.

Debe ser independiente de frameworks, bases de datos y tecnologías de interfaz.

---

### 4. Acceso a Datos
Se encarga de la **persistencia y recuperación de información**.

**Responsabilidades:**
- Guardar y recuperar datos.
- Gestionar operaciones con bases de datos.
- Traducir entre el modelo de dominio y el modelo de datos.
- Ocultar los detalles de almacenamiento.

Puede utilizar repositorios, ORM o DAO.

---

### 5. Infraestructura
Proporciona servicios técnicos que utiliza el resto de la aplicación.

Puede encargarse de:
- Logging.
- Autenticación y autorización.
- Comunicación con APIs y sistemas externos.
- Configuración.
- Serialización y otros servicios técnicos.

Su objetivo es **aislar los detalles tecnológicos** del resto de la aplicación.

---

## Ejemplo aplicado a un sistema de inmobiliaria
En un sistema de gestión de inmuebles:

**Presentación:**
- `index.ts`
- Inicia el sistema y muestra resultados.

**Aplicación / Lógica de negocio:**
- `InmobiliariaService.ts`
- Coordina operaciones y aplica las reglas del sistema.

**Acceso a datos:**
- `InmuebleRepository.ts`
- Almacena y recupera los inmuebles.

**Dominio / Modelo:**
- `Inmueble`
- `Casa`
- `Departamento`
- `Contacto`
- `Dirección`
- `Ambiente`

Representan las entidades y conceptos del dominio.

**Infraestructura:**
- Componentes encargados de servicios técnicos externos, configuración, logging, etc.


### Flujo general

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

## Ventajas

1. **Separación de responsabilidades:** cada capa tiene una función definida.
2. **Facilidad de mantenimiento:** los cambios pueden quedar aislados en una capa.
3. **Desarrollo en paralelo:** diferentes equipos pueden trabajar en distintas capas.
4. **Reutilización:** las capas inferiores pueden ser utilizadas por varias capas superiores.

---

## Desventajas

1. **Complejidad inicial:** requiere mayor planificación y estructura.
2. **Sobrecarga de comunicación:** los datos deben atravesar varias capas.
3. **Rigidez potencial:** una mala definición de las capas puede dificultar algunos flujos.
4. **Riesgo de acoplamiento:** pueden aparecer dependencias incorrectas entre capas no adyacentes.

---

## Casos de uso

- Aplicaciones empresariales complejas.
- Sistemas con lógica de negocio compleja.
- Proyectos con equipos grandes y diversos.
- Aplicaciones que requieren alta mantenibilidad.

---

## Ejemplo

Una **aplicación bancaria** puede utilizar:

- **Presentación:** formularios de transacciones.
- **Aplicación:** coordinación de una transferencia.
- **Dominio:** reglas como límites de transferencia.
- **Datos:** persistencia de las operaciones.
- **Infraestructura:** autenticación, logging y comunicación con servicios externos.

---

