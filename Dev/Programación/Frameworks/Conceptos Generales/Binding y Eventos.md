El **binding** establece una relación entre los datos de un componente y su interfaz.

Permite que los valores del componente aparezcan en pantalla y que las acciones realizadas en la interfaz puedan ejecutar código.

---

## Dirección de los datos

Existen diferentes formas de comunicación.

### Datos hacia la interfaz

```
COMPONENTE
    │
    │ dato
    ▼
INTERFAZ
```

Por ejemplo, mostrar el nombre de un usuario.

---

### Eventos desde la interfaz

```
INTERFAZ
    │
    │ evento
    ▼
COMPONENTE
```

Por ejemplo:

```
usuario hace clic
       ↓
se produce un evento
       ↓
se ejecuta una función
```

---

## Tipos habituales de binding

|       Tipo       |       Dirección       |            Función            |
| :--------------: | :-------------------: | :---------------------------: |
|  Interpolación   | Componente → interfaz |        Mostrar valores        |
| Property binding | Componente → interfaz | Asignar valores a propiedades |
|  Event binding   | Interfaz → componente |      Responder a eventos      |
| Two-way binding  | Componente ↔ interfaz |  Sincronizar ambos sentidos   |

Cada framework proporciona su propia sintaxis para implementar estos mecanismos.

Ver:

- [[Angular]]
- [[React]]
- [[Vue]]

---
