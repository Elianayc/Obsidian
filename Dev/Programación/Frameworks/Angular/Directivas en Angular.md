Las **directivas** permiten modificar el comportamiento o la forma en que Angular procesa elementos del HTML.

---

## `*ngIf`

Permite mostrar un elemento solamente cuando se cumple una condición.

```
<div *ngIf="cargando">
  Cargando...
</div>
```

Conceptualmente:

```
cargando = true
       ↓
se muestra el elemento
```

Si la condición no se cumple, el elemento no se renderiza.

---

## `*ngFor`

Permite generar elementos a partir de una colección.

```
<div *ngFor="let mensaje of mensajes">
  {{ mensaje.texto }}
</div>
```

Conceptualmente:

```
mensajes
├── mensaje 1
├── mensaje 2
└── mensaje 3

        ↓ *ngFor

<div>mensaje 1</div>
<div>mensaje 2</div>
<div>mensaje 3</div>
```

---

## Otras directivas

También existen directivas como:

### `ngSwitch`

Permite seleccionar qué contenido mostrar entre varias alternativas.

### `ngClass`

Permite aplicar clases CSS dinámicamente.

### `ngStyle`

Permite aplicar estilos dinámicamente.

Estas directivas se utilizan según las necesidades de la interfaz.

---
