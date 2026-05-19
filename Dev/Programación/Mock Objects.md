---
tags:
  - Programación
  - ProgramaciónII
---
Un mock es un objeto simulado que reemplaza a un objeto real con comportamiento controlado.

#### Usos de mocks
- Valores no controlables (ej: fecha y hora).
- Estados difíciles de reproducir (ej: errores de red).
- Objetos lentos o pesados (ej: bases de datos).
- Objetos aún no implementados.
- Evitar incluir lógica de testeo dentro del objeto real.

#### Características
- Mantienen la misma interfaz que el objeto real (polimorfismo).
- Permiten definir llamadas, parámetros y respuestas esperadas.

#### Ejemplo conceptual
Un reloj mock puede simular la hora del sistema para probar alarmas sin esperar al tiempo real.