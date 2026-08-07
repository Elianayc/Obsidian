# Niveles de encabezado
Los encabezados HTML no representan solamente un cambio visual de tamaño o negrita.

Los niveles de encabezado representan una **jerarquía dentro del documento**.

**HTML posee diferentes niveles**:
```
<h1>
<h2>
<h3>
<h4>
<h5>
<h6>
```

El encabezado `<h1>` representa el nivel más importante y los siguientes niveles representan subtítulos o secciones internas.

**Ejemplo**:
```html
<h1>Título principal</h1>

<h2>Subtítulo</h2>

<h3>Sección dentro del subtítulo</h3>
```

La jerarquía debe respetarse. Por ejemplo, antes de utilizar un `<h3>` debería existir un encabezado de nivel superior como `<h2>`.
