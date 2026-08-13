
### Enlaces absolutos
Son aquellos que apuntan a documentos externos al sitio actual.

Utilizan la URL completa del recurso.

Ejemplo:
```HTML
<a href="https://www.misitio.com">
    Mi página
</a>
```

---

### Enlaces relativos

Son aquellos que apuntan a documentos que se encuentran dentro del mismo proyecto.

No utilizan la URL completa, sino la ubicación del archivo.

Si el archivo está en el mismo directorio:
```HTML
<a href="acercade.html">
    Acerca de
</a>
```

Si se encuentra dentro de otro directorio:
```HTML
<a href="assets/mi_ubicacion.png">
    Ver ubicaciones
</a>
```

---

### Enlaces a una sección específica

También es posible acceder a una parte determinada de un documento utilizando un identificador (`id`).

**Ejemplo**:
```HTML
<a href="contacto.html#formulario">
    Formulario de contacto
</a>
```

El enlace accederá al elemento que tenga:
```HTML
id="formulario"
```

dentro del documento `contacto.html`.

---
#Programación 
#ProgramaciónIII 