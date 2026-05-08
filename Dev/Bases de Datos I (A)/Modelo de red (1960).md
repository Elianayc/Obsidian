Es una evolución del modelo jerárquico.
Permite que una tabla hijo tenga múltiples padres, lo que habilita relaciones más complejas entre datos.

---

## Definición
Un sistema de base de datos de red es aquel que almacena los datos como una colección de registros conectados entre sí mediante enlaces, formando una estructura de red.

---

## Funcionamiento
Los datos se organizan como registros conectados entre sí mediante estructuras llamadas sets.
Los sets representan las relaciones entre los datos y deben ser definidos en el esquema de la base de datos.

### Características de los sets
- Un registro owner (propietario de la relación)
- Uno o más registros members (miembros de la relación)
- Los sets están ordenados
- Las relaciones se definen a nivel del esquema

---

## Mejora respecto al modelo jerárquico
- Permite relaciones N a M
- Un nodo hijo puede tener múltiples nodos padres
- Mayor flexibilidad en la representación de datos

---

## Implementación
- Se utilizan estructuras de sets para representar relaciones
- En muchos casos se utilizan tablas intermedias
- La navegación de datos se realiza mediante estructuras enlazadas

---

## Ventajas
- Permite representar más tipos de relaciones que el modelo jerárquico
- Mayor flexibilidad en la estructura de datos
- Representa relaciones complejas de forma más natural que el modelo jerárquico

---

## Desventajas
- Es necesario conocer toda la estructura para poder consultar los datos
- Alta complejidad de diseño
- Curva de aprendizaje elevada
- Los cambios estructurales afectan la aplicación
- La navegación de datos sigue siendo rígida
- Las relaciones son físicas y no lógicas, lo que reduce flexibilidad
