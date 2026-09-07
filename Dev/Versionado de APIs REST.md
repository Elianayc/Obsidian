El **versionado** permite evolucionar una API sin romper los clientes existentes, manteniendo la **retrocompatibilidad** mientras se incorporan nuevas características.

---

### Estrategias de versionado

La clase presenta dos estrategias principales:

1. Versionado mediante la **URL**.
2. Versionado mediante **parámetros enviados en el request**.

---

#### URL-Based Versioning

Consiste en incluir la versión directamente en la URL.
Es la estrategia **recomendada**.

```text
https://api.example.com/v1/users
https://api.example.com/v2/users
```

##### Ventajas

- Claridad.
- Simplicidad.
- Fácil de verificar mediante testing.
- Facilita el debugging.

##### Implementación

Las rutas pueden separarse por versión:

```js
app.use('/api/v1', v1Routes);
app.use('/api/v2', v2Routes);
```

Una estructura posible:

```text
/routes
├── v1
│   ├── users.js
│   └── products.js
└── v2
    ├── users.js
    └── products.js
```

##### Mejores prácticas

1. Utilizar **versionado semántico**, por ejemplo:
    - `v1.0`
    - `v1.1`
    - `v2.0`
        
2. Mantener versiones anteriores durante períodos de transición.
    
3. Comunicar con anticipación la **deprecación** de una versión.
    
4. Documentar claramente los cambios entre versiones.
    

---

#### Versionado mediante parámetros enviados en el request

Consiste en indicar la versión de la API mediante un **parámetro de la solicitud HTTP**, en lugar de incluir la versión directamente en la URL.

Por ejemplo:
   ```text
   https://api.example.com/users?version=1
   https://api.example.com/users?version=2
```


En este caso, `version=1` y `version=2` son **parámetros de consulta (query parameters)** que indican qué versión de la API debe utilizarse.

La URL del recurso sigue siendo `/users`, y la versión se especifica mediante el parámetro `version`.


Eso es lo que le faltaba al punto 2: **qué es, dónde se coloca y un ejemplo concreto**.
