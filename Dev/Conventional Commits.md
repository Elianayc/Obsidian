# Conventional Commits

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

```
feat      → nueva funcionalidad
fix       → corregir error
refactor  → reorganizar código
docs      → documentación
style     → formato
test      → tests
chore     → mantenimiento
build     → build/dependencias
ci        → integración continua
```

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

Ver también [[GIT]], [[Historial]] y [[Rebase]].
