Un **commit** representa una versión guardada del proyecto dentro del historial de Git.

Un commit contiene información como:

```
COMMIT
├── cambios
├── autor
├── fecha
├── mensaje
└── identificador
```

---

# Crear un commit

Primero los cambios deben estar en el [[Estados y Staging|Staging Area]].

Después:

```
git commit -m "mensaje"
```

Por ejemplo:

```
git commit -m "feat: agregar pantalla de login"
```

---

# Hash

Cada commit posee un identificador único llamado **hash**.

Por ejemplo:

```
66de2dc C06 Step2
323db54 C05 Step5
c6f8e2f C05 Step4
```

En:

```
66de2dc C06 Step2
```

tenemos:

```
66de2dc
→ hash abreviado

C06 Step2
→ mensaje del commit
```

Si se reescribe un commit, puede cambiar su hash.

---

# Autor

Git guarda dentro del commit el nombre y email del autor.

Consultar el nombre:

```
git config user.name
```

Consultar el email:

```
git config user.email
```

---

# Configuración global

Para configurar el nombre utilizado en los commits:

```
git config --global user.name "Eliana Yasmín Carro"
```

El email se configura mediante:

```
git config --global user.email "email"
```

La configuración `--global` se aplica normalmente a los repositorios del usuario de esa computadora.

---

# Configuración local

Un repositorio puede tener una configuración propia que sobrescriba la configuración global.

Para saber de dónde proviene un valor:

```
git config --show-origin --get user.name
```

```
git config --show-origin --get user.email
```

---

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

Ver también [[Git]], [[Historial]] y [[Rebase]].