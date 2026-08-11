Un formulario requiere principalmente tres atributos:

---

## `action`

Indica el documento encargado de recibir y procesar los datos enviados.

Generalmente puede ser un archivo desarrollado en:

- JavaScript.
- PHP.
- Python.

**Ejemplo**:
```html
<form action="procesar.php">
```

Si no se especifica un valor, el formulario enviará los datos al mismo documento donde se encuentra.

---

## `method`

Indica cómo serán enviados los datos del formulario.

Define el método HTTP utilizado para realizar el envío.

Los métodos más utilizados son:
- `GET`
- `POST`

También existen otros métodos HTTP como:
- `PUT`
- `DELETE`

Si no se especifica, el valor predeterminado es:
```html
method="GET"
```

---

## `enctype`

Define cómo se codificará la información enviada por el formulario.

Es especialmente importante cuando el método utilizado es `POST`.

Los valores posibles son:

|Valor|Uso|
|---|---|
|`application/x-www-form-urlencoded`|Valor predeterminado para enviar datos|
|`multipart/form-data`|Se utiliza cuando se envían archivos|
|`text/plain`|Incorporado en HTML5|

**Ejemplo**:
```html
<form 
method="POST" 
enctype="multipart/form-data">
```


---
#Programación 
#ProgramaciónIII 
