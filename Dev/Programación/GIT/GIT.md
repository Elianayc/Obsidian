**Git** es un sistema de **control de versiones distribuido**.

Permite registrar los cambios realizados en un proyecto a lo largo del tiempo.

Con Git podemos:

- Guardar versiones de un proyecto.
- Consultar qué cambió.
- Saber quién realizó un cambio.
- Volver a versiones anteriores.
- Trabajar con [[Ramas y Merge|ramas]].
- Combinar el trabajo de distintas personas.
- Sincronizar nuestro proyecto con un repositorio remoto.
- Trabajar en equipo sin modificar todos directamente los mismos archivos al mismo tiempo.

---

# Git ≠ GitHub

**Git** es la herramienta que controla las versiones del proyecto.

**GitHub** es una plataforma que permite alojar repositorios Git en Internet y colaborar con otras personas.

```
GIT
Control de versiones
en nuestra computadora
        │
        │ push / pull
        ▼
GITHUB
Repositorio remoto
```

Se puede utilizar Git sin utilizar GitHub.

---

# Repositorio

Un **repositorio** es un proyecto cuyo historial está siendo administrado por Git.

Cuando inicializamos Git se crea internamente:

```
mi-proyecto/
├── .git/
├── src/
├── README.md
└── ...
```

La carpeta:

```
.git/
```

contiene la información que Git necesita para mantener el historial del repositorio.

No se modifica manualmente.

---

# Crear un repositorio

Para comenzar a utilizar Git en una carpeta:

```
git init
```

Esto crea el repositorio Git local.

---

# Clonar un repositorio

**Clonar** significa traer a nuestra computadora una copia de un repositorio Git existente.

```
git clone URL
```

Por ejemplo:

```
git clone https://github.com/usuario/proyecto.git
```

Conceptualmente:

```
GitHub
   │
   │ git clone
   ▼
Computadora
   │
   └── repositorio local
```

---

# Modelo mental de Git

El flujo fundamental es:

```
ARCHIVOS
Working Directory
      │
      │ git add
      ▼
STAGING AREA
      │
      │ git commit
      ▼
REPOSITORIO LOCAL
      │
      │ git push
      ▼
REPOSITORIO REMOTO
GitHub
```

Es decir:

```
Modificar
   ↓
Preparar
   ↓
Guardar versión
   ↓
Compartir
```

Los estados se explican con más detalle en [[Estados y Staging]].

---

# Flujo básico

Después de modificar el código:

### 1. Revisar el estado

```
git status
```

### 2. Revisar qué cambió

```
git diff
```

### 3. Preparar los cambios

```
git add .
```

### 4. Crear el commit

```
git commit -m "mensaje"
```

### 5. Subir los commits

```
git push
```

El flujo completo queda:

```
MODIFICO ARCHIVOS
       ↓
git status
       ↓
git diff
       ↓
git add .
       ↓
git commit
       ↓
git push
```

---

# Commit

Un [[Commits|commit]] representa una versión guardada dentro del historial.

Por ejemplo:

```
git commit -m "feat: agregar pantalla de login"
```

Cada commit contiene información como:

```
COMMIT
├── cambios
├── autor
├── fecha
├── mensaje
└── identificador
```

Cada commit posee un identificador único llamado **hash**.

Por ejemplo:

```
66de2dc C06 Step2
```

`66de2dc` es una versión abreviada del hash.

Ver [[Commits]].

---

# Ramas

Una **rama** permite desarrollar cambios en una línea independiente del proyecto.

Por ejemplo:

```
main
 │
 ├── commit
 │
 └─────────────┐
               │
          feature/r7
               │
               ├── commit
               └── commit
```

Esto permite trabajar en una funcionalidad sin desarrollar directamente sobre `main`.

Ver [[Ramas y Merge]].

---

# Repositorio local y remoto

Nuestro repositorio de la computadora es el **repositorio local**.

El repositorio alojado, por ejemplo, en GitHub es un **repositorio remoto**.

```
LOCAL
  │
  │ push
  ▼
REMOTO

LOCAL
  ▲
  │ pull
  │
REMOTO
```

El remoto principal suele llamarse:

```
origin
```

Por ejemplo:

```
main
```

es nuestra rama local.

```
origin/main
```

representa nuestra referencia del estado de `main` en el remoto.

Ver [[Repositorios Remotos]].

---

# HEAD

`HEAD` indica dónde estamos posicionados actualmente dentro del historial.

Normalmente apunta al último commit de nuestra rama actual.

```
commit A
   ↓
commit B
   ↓
commit C ← HEAD
```

También podemos referirnos a commits anteriores:

```
HEAD~1
```

significa:

```
1 commit antes de HEAD
```

Y:

```
HEAD~2
```

significa:

```
2 commits antes de HEAD
```

Ver [[Historial]].

---

# Comandos fundamentales

## Estado

```
git status
```

Permite saber qué está ocurriendo actualmente en el repositorio.

---

## Ver cambios

```
git diff
```

---

## Preparar cambios

```
git add .
```

---

## Crear un commit

```
git commit -m "mensaje"
```

---

## Ver historial

```
git log --oneline
```

---

## Ver ramas

```
git branch
```

---

## Cambiar de rama

```
git switch nombre-rama
```

---

## Crear y cambiar a una rama

```
git switch -c nombre-rama
```

---

## Integrar una rama

```
git merge nombre-rama
```

---

## Traer cambios

```
git pull
```

---

## Subir commits

```
git push
```

---

## Guardar temporalmente cambios

```
git stash
```

---

# Machete

```
git clone
→ traer un repositorio por primera vez

git status
→ ¿cómo está mi repositorio?

git diff
→ ¿qué cambié?

git add
→ preparar cambios

git commit
→ guardar una versión

git log
→ consultar el historial

git branch
→ consultar/manejar ramas

git switch
→ cambiar de rama

git merge
→ integrar ramas

git pull
→ traer e integrar cambios remotos

git push
→ subir commits

git stash
→ guardar temporalmente cambios

git restore
→ restaurar cambios

git rebase
→ reorganizar/reubicar commits

git tag
→ marcar un commit importante
```

---

# Temas relacionados

- [[Estados y Staging]]
- [[Commits]]
- [[Historial]]
- [[Ramas y Merge]]
- [[Repositorios Remotos]]
- [[Conflictos]]
- [[Stash]]
- [[Rebase]]
- [[Deshacer Cambios]]
- [[Gitignore]]
- [[Tags]]
    
---

# Idea principal

Git administra el historial de nuestro proyecto.

El flujo fundamental que hay que recordar es:

```
ARCHIVOS
   │
   │ git add
   ▼
STAGING
   │
   │ git commit
   ▼
REPOSITORIO LOCAL
   │
   │ git push
   ▼
GITHUB
```

A partir de este flujo aparecen las demás herramientas de Git para manejar ramas, trabajo en equipo, conflictos, historial y correcciones.

---
