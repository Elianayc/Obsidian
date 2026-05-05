#### 1. Compartir datos
Permite que múltiples aplicaciones y usuarios accedan a la misma información sin modificar la base de datos.

#### 2. Reducir la redundancia
Evita la duplicación innecesaria de datos.  
No toda redundancia es mala, pero debe estar controlada.

#### 3. Evitar inconsistencias
Ocurren cuando un mismo dato tiene valores distintos en diferentes partes del sistema.  
Se reducen con un buen control de redundancia.

#### 4. Manejo de transacciones
Una transacción es una unidad lógica de trabajo compuesta por operaciones que se ejecutan todas o ninguna.

#### 5. Integridad de los datos
Garantiza que los datos sean correctos y consistentes.

#### 6. Seguridad
Controla el acceso a los datos mediante permisos y restricciones.

---

# Independencia de los datos
La independencia de los datos es un objetivo de los sistemas de bases de datos.

### Definición

Es la inmunidad de las aplicaciones a cambios en la representación física y técnicas de acceso a los datos.

Permite modificar la base sin afectar las aplicaciones.

#### 1. Representación de los datos
- Cambios en sistemas numéricos (binario, decimal, etc.)
- Separación de parte entera y decimal
- Cambios en codificación (UTF-8, Unicode, ISO-8859-1)

#### 2. Codificación de los datos
**Ejemplo:**
Rojo, Verde, Azul → 1, 2, 3

#### 3. Materialización de los datos
El dato que ve la aplicación puede ser resultado de un cálculo interno de la base de datos.

#### 4. Extensibilidad del sistema
La base de datos puede crecer sin afectar a las aplicaciones que no utilizan los nuevos campos.