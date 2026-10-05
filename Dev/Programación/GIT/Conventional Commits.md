**Conventional Commits** es una convención para escribir mensajes de commits de manera consistente.

Estructura:

```
tipo: descripción
```

Por ejemplo:

```
feat: agregar pantalla de login
```

---

## `feat`

Nueva funcionalidad.

```
feat: agregar navegación entre pantallas
```

---

## `fix`

Corrección de un error.

```
fix: corregir redirección inicial
```

---

## `refactor`

Reorganización del código sin agregar funcionalidad ni corregir un bug.

```
refactor: unificar métodos de navegación
```

Por ejemplo, pasar de:

```
goToOne(): void {
  this.router.navigate(['/one']);
}

goToTwo(): void {
  this.router.navigate(['/two']);
}
```

a:

```
goTo(ruta: string): void {
  this.router.navigate([ruta]);
}
```

---

## `docs`

Cambios de documentación.

```
docs: actualizar README
```

---

## `style`

Cambios de formato que no modifican el comportamiento.

```
style: aplicar formato con Prettier
```

No significa necesariamente modificar el CSS visual de la aplicación.

---

## `test`

Agregar o modificar tests.

```
test: agregar pruebas del servicio
```

---

## `chore`

Tareas de mantenimiento.

```
chore: actualizar configuración
```

---

## `build`

Cambios relacionados con build o dependencias.

```
build: agregar dependencia
```

---

## `ci`

Cambios relacionados con integración continua.

```
ci: agregar workflow de GitHub Actions
```

---

# Scope

Opcionalmente podemos indicar qué parte del proyecto fue modificada.

```
tipo(scope): descripción
```

Por ejemplo:

```
feat(routing): agregar rutas principales
```

```
fix(journey): corregir carga del recorrido
```

```
refactor(auth): simplificar validación
```

---

# Machete de Conventional Commits

| Tipo       | Cuándo lo usarías en tu TP                                                            | Ejemplo de commit                                            |
| ---------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| `feat`     | Agregaste algo que antes el sistema no hacía.                                         | `feat(journey): agregar endpoint de recorrido actual`        |
| `fix`      | Algo debía funcionar y estaba funcionando mal.                                        | `fix(journey): corregir carga de encuentros`                 |
| `refactor` | El código ya funcionaba y lo reorganizaste sin cambiar lo que hace.                   | `refactor(journey): simplificar obtención del equipo actual` |
| `docs`     | Tocaste solamente documentación.                                                      | `docs: actualizar README con instrucciones de ejecución`     |
| `style`    | Solo cambiaste formato del código, sin cambiar su funcionamiento.                     | `style: aplicar Prettier al frontend`                        |
| `test`     | Agregaste o modificaste pruebas.                                                      | `test(journey): agregar tests del servicio`                  |
| `chore`    | Hiciste mantenimiento/configuración que no agrega una función al usuario.             | `chore: actualizar configuración del proyecto`               |
| `build`    | Cambiaste dependencias o configuración necesaria para construir/ejecutar el proyecto. | `build(frontend): agregar dependencia de Angular`            |
| `ci`       | Configuraste automatizaciones del repositorio.                                        | `ci: agregar workflow de GitHub Actions`                     |

---

# Buenos mensajes

Un mensaje debería ser:

- Breve.
- Específico.
- Fácil de entender.
- Relacionado con un cambio concreto.
    
Evitar:

```
cambios
```

```
cosas
```

```
arreglos
```

Preferir:

```
fix: corregir navegación a inicio
```

---

# Commits de clases

En ejercicios guiados puede utilizarse una convención propia.

Por ejemplo:

```
C05 Step1
C05 Step2
C05 Step3
C05 Step4
C05 Step5
C06 Step1
C06 Step2
```

En este contexto el objetivo es identificar exactamente el paso realizado.

No hace falta convertirlo en:

```
feat: C06 Step2
```

En proyectos reales o TPs es más útil utilizar mensajes descriptivos:

```
feat(journey): agregar endpoint de recorrido actual
```

Ver también [[Git]], [[Historial de Git]] y [[Git Rebase]].

---

