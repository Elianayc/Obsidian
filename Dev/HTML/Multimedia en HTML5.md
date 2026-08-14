HTML5 incorpora soporte nativo para contenido multimedia mediante nuevos elementos.

Antes de HTML5 era común depender de plugins externos para reproducir audio y video.

![[Pasted image 20260814150434.png]]

---

## `<audio>`

Permite insertar archivos de audio dentro de una página web.

**Ejemplo**:
```html
<audio src="audio.mp3" controls>
    Tu navegador no implementa el elemento audio.
</audio>
```

El atributo `controls` agrega controles para que el usuario pueda:

- Reproducir.
- Pausar.
- Controlar el volumen.

---

## `<video>`

Permite insertar videos dentro de un documento HTML.

**Ejemplo**:
```html
<video src="video.mp4" controls>
    Tu navegador no implementa el elemento video.
</video>
```

También permite agregar mensajes alternativos para navegadores que no soporten este elemento.
