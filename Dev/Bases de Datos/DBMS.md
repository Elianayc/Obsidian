---
tags:
  - 
  
---
## Sistemas de Bases de Datos
Un sistema de bases de datos es un conjunto de datos estructurados e interrelacionados, junto con el software que permite acceder, almacenar, recuperar y manipular dicha información.

Permite la gestión eficiente de grandes volúmenes de datos, asegurando su organización, consistencia y disponibilidad.

---

#### Estructura de una base de datos
- Datos organizados (tablas / archivos físicos)
- Metadatos (describen la estructura: tipo de dato, nombre, longitud, etc.)

---

#### Modelo de base de datos
Concepto que especifica cómo van a estar organizados los datos y cómo se van a relacionar.

#### Componentes
- [[Gestor de almacenamiento]]
- [[Procesador de consultas]]

---
### Ventajas

##### Compartir datos
Permite que múltiples aplicaciones y usuarios accedan a la misma información sin modificar la base de datos.

##### Reducir la redundancia
Evita la duplicación innecesaria de datos.  
No toda redundancia es mala, pero debe estar controlada.

##### Evitar inconsistencias
Ocurren cuando un mismo dato tiene valores distintos en diferentes partes del sistema.  
Se reducen con un buen control de redundancia.

##### Manejo de transacciones
Una transacción es una unidad lógica de trabajo compuesta por operaciones que se ejecutan todas o ninguna.

##### Integridad de los datos
Garantiza que los datos sean correctos y consistentes.

##### Seguridad
Controla el acceso a los datos mediante permisos y restricciones.

---

## Independencia de los datos
La independencia de los datos es un objetivo de los sistemas de bases de datos.

#### Definición
Es la inmunidad de las aplicaciones a cambios en la representación física y técnicas de acceso a los datos.
Permite modificar la base sin afectar las aplicaciones.

##### Representación de los datos
- Cambios en sistemas numéricos (binario, decimal, etc.)
- Separación de parte entera y decimal
- Cambios en codificación (UTF-8, Unicode, ISO-8859-1)

##### Codificación de los datos
**Ejemplo:**
Rojo, Verde, Azul → 1, 2, 3

##### Materialización de los datos
El dato que ve la aplicación puede ser resultado de un cálculo interno de la base de datos.

##### Extensibilidad del sistema
La base de datos puede crecer sin afectar a las aplicaciones que no utilizan los nuevos campos.

---

#### Apartados Relacionados:
- [[Modelos de Bases de Datos]]
- [[Tipos de Bases de Datos]]
- [[ANSI SPARC]]
- [[Transacciones]]
- [[Normalización]]
- [[Funciones]]

#BasesdeDatos