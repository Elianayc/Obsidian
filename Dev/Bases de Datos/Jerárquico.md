---
tags:
  - DBI1erparcial
  - DB
---

**1950**

## Definición general
Un sistema de base de datos jerárquico es aquel que guarda la información en una estructura jerárquica en forma de árbol invertido.

Los registros se organizan mediante relaciones padre-hijo:
- Un nodo padre puede tener múltiples nodos hijos
- Un nodo hijo tiene un único nodo padre

## Características generales

- Estructura en forma de árbol invertido
- Relaciones padre-hijo estrictas
- Modelo temprano en la evolución de bases de datos (aprox. 1950)
- Base de modelos posteriores más flexibles

Es un modelo eficiente en acceso, pero rígido, poco flexible y difícil de mantener.

---

## Definición técnica
Los sistemas jerárquicos enlazan los registros en forma de árbol invertido donde:
- Un nodo padre puede tener varios nodos hijos
- Un nodo hijo sólo puede tener un único padre

---

## Funcionamiento
Este modelo permite implementar relaciones padre-hijo (1 a N), como mejora respecto a los sistemas basados en archivos.

### Características de las relaciones
- Son unidireccionales
- Se pueden consultar desde los nodos hijos hacia los nodos padre
- No es posible la navegación inversa directa

La consulta inversa debe realizarse de forma secuencial.

---

### Limitaciones de acceso
- No presenta mecanismos de indexación avanzados
- No optimiza lecturas como otros modelos más modernos

---

### Nivel físico vs nivel lógico
A diferencia del modelo relacional, las relaciones entre datos se representan a nivel físico y no lógico.

- Las relaciones se basan en direcciones de memoria
- Cada registro hijo contiene la dirección del registro padre como metadato
- Esto permite accesos directos y rápidos entre registros

---

## Mejora respecto a File Systems
- Permite relaciones 1 a N
- Mayor organización de los datos
- Acceso más directo entre registros

---

## Desventajas

### Duplicidad de registros
- No garantiza la inexistencia de registros duplicados
- No existe el concepto de clave primaria
- No existen campos únicos
- Puede haber redundancia de datos

### Integridad referencial
- Un registro hijo puede quedar sin un padre válido
- Es posible eliminar un nodo padre sin eliminar los hijos
- Se generan registros huérfanos

### Desnormalización
- No existen controles de normalización
- No hay restricciones de campos clave o únicos
- Se permite redundancia de datos

### Mantenibilidad
- Difícil mantenimiento del modelo
- Cambios en la estructura afectan todo el sistema
- Agregar nuevas relaciones puede implicar rediseño completo

#BasesdeDatos