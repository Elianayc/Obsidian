El **renderizado** es el proceso mediante el cual los datos de una aplicación se convierten en elementos visibles de la interfaz.

Los frameworks proporcionan diferentes mecanismos para decidir **qué mostrar** y **cuántas veces mostrarlo**.

---

# Renderizado condicional

Permite mostrar un elemento solamente cuando se cumple determinada condición.

Por ejemplo:

```
¿está cargando?
      │
      ├── SÍ → mostrar "Cargando..."
      │
      └── NO → mostrar contenido
```

Puede utilizarse para:

- Estados de carga.
- Errores.
- Usuarios autenticados.
- Resultados vacíos.
- Mostrar u ocultar partes de una pantalla.
    

---

# Renderizado de listas

Permite generar elementos de la interfaz a partir de una colección de datos.

Por ejemplo:

```
mensajes
├── mensaje 1
├── mensaje 2
└── mensaje 3
```

puede generar:

```
MensajeComponent
MensajeComponent
MensajeComponent
```

Cada framework proporciona su propio mecanismo para recorrer la colección y generar los elementos correspondientes.

---

## Identificación de elementos

Cuando se renderizan listas, los frameworks suelen necesitar alguna forma de identificar cada elemento.

Por ejemplo:

```
mensaje
├── id: 1
└── texto: "Hola"
```

El identificador permite reconocer qué elemento cambió, fue agregado o fue eliminado.

Ver:

- [[Angular]]
- [[React]]
- [[Vue]]

---
