El **versionado** permite evolucionar una API sin romper los clientes existentes, manteniendo la **retrocompatibilidad** mientras se incorporan nuevas características.

---

### Estrategias de versionado

La clase presenta dos estrategias principales:

1. Versionado mediante la **URL**.
2. Versionado mediante **parámetros enviados en el request**.
    

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

#### Implementación

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

### Mejores prácticas

1. Utilizar **versionado semántico**, por ejemplo:
    - `v1.0`
    - `v1.1`
    - `v2.0`
        
2. Mantener versiones anteriores durante períodos de transición.
    
3. Comunicar con anticipación la **deprecación** de una versión.
    
4. Documentar claramente los cambios entre versiones.
    

---