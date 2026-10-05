Los componentes Angular atraviesan diferentes etapas durante su existencia.

Angular proporciona **hooks de ciclo de vida** que permiten ejecutar código en determinados momentos.

Entre los principales se encuentran:

```
ngOnChanges
ngOnInit
ngOnDestroy
```

---

## `ngOnInit()`

Se ejecuta durante la inicialización del componente.

```
ngOnInit() {
  this.cargarDatos();
}
```

Es habitual utilizarlo para realizar tareas iniciales del componente.

Conceptualmente:

```
Angular crea componente
        ↓
     ngOnInit()
        ↓
inicialización
```

---

## `ngOnChanges()`

Se utiliza para reaccionar ante cambios en determinados valores recibidos mediante `@Input()`.

Conceptualmente:

```
PADRE cambia dato
       ↓
@Input recibe nuevo valor
       ↓
ngOnChanges()
```

---

## `ngOnDestroy()`

Se ejecuta cuando Angular está por destruir el componente.

Puede utilizarse para limpiar recursos que ya no deben continuar activos.

Por ejemplo:

- Suscripciones.
    
- Timers.
    
- Listeners.
    

```
componente deja de utilizarse
            ↓
       ngOnDestroy()
            ↓
       limpieza
```

---

## Resumen

```
ngOnInit
→ inicialización

ngOnChanges
→ cambios de inputs

ngOnDestroy
→ limpieza antes de destruir
```

Ver [[Ciclo de Vida de Componentes]].

---
