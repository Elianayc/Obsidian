Los componentes Angular pueden intercambiar información.
La comunicación básica entre un componente padre y un hijo tiene dos direcciones.

```
PADRE
  │
  │ @Input()
  ▼
HIJO

PADRE
  ▲
  │ @Output()
  │
HIJO
```

---

# Padre → Hijo

Para enviar información desde el padre hacia el hijo se utiliza:

```
@Input() + property binding [ ]
```

El hijo declara qué dato puede recibir:

```
@Input() nombre = '';
```

El padre proporciona el valor:

```
<app-hijo [nombre]="nombreUsuario"></app-hijo>
```

El recorrido es:

```
nombreUsuario
     │
     │ [nombre]
     ▼
@Input() nombre
```

### Machete

```
[ ] = paso datos
```

---

# Hijo → Padre

Cuando el hijo necesita avisarle algo al padre utiliza:

```
@Output()
+
EventEmitter
```

El hijo declara el evento:

```
@Output() seleccionado = new EventEmitter<string>();
```

Cuando ocurre algo puede emitirlo:

```
seleccionar() {
  this.seleccionado.emit('producto-1');
}
```

El padre escucha el evento:

```
<app-hijo
  (seleccionado)="procesarSeleccion($event)">
</app-hijo>
```

---

## `$event`

`$event` representa el dato enviado por el hijo mediante:

```
.emit(...)
```

Por ejemplo:

```
this.seleccionado.emit('producto-1');
```

hace que:

```
$event = 'producto-1'
```

en el padre.

---

## Flujo completo

```
PADRE
 │
 │ [nombre]="nombreUsuario"
 ▼
HIJO
 │
 │ seleccionado.emit(valor)
 ▼
@Output
 │
 ▼
PADRE
 │
 └── procesarSeleccion($event)
```

---

## Machete

```
PADRE → HIJO
@Input + [dato]="valor"

HIJO → PADRE
@Output + (evento)="funcion($event)"

[ ] = paso datos
( ) = escucho eventos

$event = dato enviado mediante emit()
```

---
