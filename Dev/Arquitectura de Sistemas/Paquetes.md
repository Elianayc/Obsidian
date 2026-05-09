---
tags:
  - Arquitecturadesistemas
---
Son **carpetas o subdirectorios** que agrupan archivos relacionados bajo un mismo criterio.

#### Ejemplo de organización:
`src/`
- `usuarios/`
    - `Usuario.ts`
    - `UsuarioService.ts`
    - `UsuarioValidator.ts`
- `libros/`
    - `Libro.ts`
    - `LibroService.ts`
    - `LibroRepository.ts`
- `prestamos/`
    - `Prestamo.ts`
    - `PrestamoService.ts`
    - `CalculadorMulta.ts`

Cada carpeta es un **paquete** que agrupa clases relacionadas con una misma funcionalidad:

• paquete **usuarios** → todo lo relacionado a usuarios  
• paquete **libros** → todo lo relacionado a libros  
• paquete **prestamos** → todo lo relacionado a préstamos

La organización del código fuente suele definirse según los lineamientos de arquitectura establecidos para el proyecto.

