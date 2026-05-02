Un sistema de bases de datos es un conjunto de datos estructurados e interrelacionados junto con el software que permite acceder, almacenar, recuperar y manipular dichos datos.

Permite almacenar, recuperar y manipular datos.

### Estructura de una base de datos
- Datos organizados (tablas / archivos físicos)
- Metadatos (describen la estructura: tipo de dato, nombre, longitud, etc.)

### Modelo de base de datos
Concepto que especifica cómo van a estar organizados los datos y cómo se van a relacionar.


## Componentes
#### Gestor de almacenamiento
Administra el almacenamiento físico de los datos.  
Permite almacenar, recuperar y actualizar información.  
Actúa como interfaz entre el nivel lógico y el almacenamiento físico.

##### Conformado por:
- **Gestor de archivos** → organiza datos en disco  
- **Gestor de memoria** → gestiona RAM y caché  


#### Procesador de consultas
Interpreta y ejecuta las consultas del usuario.

##### Componentes:
- **Intérprete DDL** → define la estructura de la base de datos  
- **Compilador DML** → traduce consultas a planes de ejecución  
- **Motor de evaluación** → ejecuta las consultas

[[Ventajas]]
[[Modelos de Bases de Datos]]
[[Tipos de Bases de Datos]]
[[Arquitectura de Sistemas de Bases de Datos ANSI SPARC]]