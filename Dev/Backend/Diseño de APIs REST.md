El diseño de una **API REST** bien estructurada permite crear servicios **mantenibles, escalables y fáciles de usar**.

REST (_Representational State Transfer_) se basa en principios arquitectónicos que guían el diseño de APIs efectivas.

---

### Recursos como entidades centrales

En REST, todo gira alrededor de **recursos**, que representan entidades o conceptos de negocio que pueden ser nombrados, direccionados y manipulados.

##### Características:

- **Identificación única:** cada recurso debe identificarse mediante una URL específica.
    
- **Sustantivos, no verbos:** las URLs representan entidades, no acciones.
    
- **Jerarquía lógica:** las relaciones padre-hijo pueden reflejarse en la estructura de la URL.
    
- **Colecciones e instancias:** se diferencia entre una colección de recursos y un recurso individual.
    

##### Ejemplo:

```text
/usuarios
/usuarios/123
/usuarios/123/pedidos
```

- `/usuarios` → colección de usuarios.
- `/usuarios/123` → usuario específico.
- `/usuarios/123/pedidos` → pedidos del usuario 123.
    

##### Ejemplos incorrectos:

```text
/obtenerUsuarios
/usuario123
/getUser?id=123
```

El último ejemplo utiliza un estilo **RPC**, basado en acciones, en lugar del enfoque REST.

---

### Stateless (sin estado)

Cada request debe contener **toda la información necesaria para ser procesada**, sin depender de información almacenada en el servidor sobre el estado de la sesión del cliente.

##### Esto implica:

1. **Autosuficiencia:** cada request incluye los datos de autenticación, contexto y parámetros necesarios.
2. **No dependencia de sesiones:** el servidor no mantiene el estado de conversaciones anteriores.
3. **Escalabilidad horizontal:** cualquier servidor puede procesar cualquier request.
4. **Tolerancia a fallos:** la pérdida de conexión no afecta el estado de la aplicación.
   
##### Ventajas:

- **Escalabilidad:** facilita el uso de _load balancers_ para distribuir la carga.
- **Confiabilidad:** reduce puntos de fallo relacionados con el estado del cliente.
- **Simplicidad:** simplifica la lógica del servidor y el debugging.
- **Cacheable:** facilita implementar estrategias de caché.

---

### Interfaz uniforme

Una API REST debe utilizar de manera consistente:

- Métodos [[HTTP (HyperText Transfer Protocol)]].
- Códigos de estado HTTP.
- Convenciones de nombres.

Esto proporciona una experiencia **predecible y estándar** para los consumidores de la API.

##### Beneficios

- **Predictibilidad:** permite anticipar cómo funciona la API.
- **Menor curva de aprendizaje:** utiliza patrones conocidos.
- **Interoperabilidad:** facilita la integración con herramientas y librerías existentes.
- **Mantenibilidad:** favorece un código limpio y fácil de mantener.
    
---

### Representaciones múltiples

Un mismo recurso puede tener diferentes **representaciones** según las necesidades del cliente.

Las más habituales son:

- **JSON**
- **XML**
    
Ver [[Representaciones de Recursos]].

---

