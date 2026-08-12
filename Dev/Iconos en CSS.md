Para agregar y utilizar **iconos** dentro de una página web, podemos incluir una **hoja de estilos** y luego referenciar las clases proporcionadas por dicha hoja en cada elemento HTML donde necesitemos utilizar un icono.

---

## Font Awesome

Por ejemplo, podemos utilizar los iconos de **Font Awesome** incluyendo su hoja de estilos mediante la etiqueta `<link>`:

```css
<html>
<head>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/fontawesome/4.7.0/css/font-awesome.min.css">
</head>

<body>
    <i class="fa fa-car"></i>
    <i class="fa fa-car" style="font-size:48px;"></i>
    <i class="fa fa-car" style="font-size:60px;color:red;"></i>
</body>
</html>
```

En este ejemplo se utilizan diferentes tamaños y colores para el mismo icono.

---

## Google Material Icons

También podemos utilizar los iconos de **Google** mediante su hoja de estilos:

```css
<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons">
</head>

<body>
    <i class="material-icons">cloud</i>
    <i class="material-icons" style="font-size:48px;">cloud</i>
    <i class="material-icons" style="font-size:60px;color:red;">cloud</i>
</body>
</html>
```

---

## Iconos en un menú de navegación

Los iconos también pueden utilizarse dentro de un componente `<nav>` para acompañar los elementos de un menú navegable.

Ejemplo:

```css
<nav>
    <div class="list-group">
        <ul>
            <li>
                <a class="list-group-item" href="#">
                    <i class="fa fa-home fa-fw" aria-hidden="true"></i>
                    &nbsp; Home
                </a>
            </li>

            <li>
                <a class="list-group-item" href="#proyectos">
                    <i class="fa fa-book fa-fw" aria-hidden="true"></i>
                    &nbsp; <span>Proyectos</span>
                </a>
            </li>

            <li>
                <a class="list-group-item" href="#">
                    <i class="fa fa-pencil fa-fw" aria-hidden="true"></i>
                    &nbsp; Applications
                </a>
            </li>

            <li>
                <a class="list-group-item" href="#">
                    <i class="fa fa-cog fa-fw" aria-hidden="true"></i>
                    &nbsp; Settings
                </a>
            </li>
        </ul>
    </div>
</nav>
```

---
#ProgramaciónIII