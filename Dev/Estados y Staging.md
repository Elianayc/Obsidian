Git distingue diferentes estados para los archivos de un proyecto.

El flujo principal es:

```
WORKING DIRECTORY
archivo modificado
       │
       │ git add
       ▼
STAGING AREA
cambio preparado
       │
       │ git commit
       ▼
REPOSITORIO LOCAL
cambio guardado
```

---

# Working Directory

El **Working Directory** es el estado actual de los archivos con los que estamos trabajando.

Cuando modificamos un archivo, el cambio aparece primero acá.

Por ejemplo:

```
app.component.ts
```

fue modificado, pero todavía no ejecutamos `git add`.

---

# Staging Area

El **Staging Area** es una zona intermedia donde seleccionamos qué cambios queremos incluir en el próximo commit.

```
MODIFICADO
    │
    │ git add
    ▼
STAGING
    │
    │ git commit
    ▼
COMMIT
```

Esto permite tener varios archivos modificados pero elegir cuáles formarán parte del siguiente commit.

---

# git status

```
git status
```

Permite consultar el estado actual del repositorio.

Puede mostrar:

- Archivos modificados.
    
- Archivos preparados.
    
- Archivos nuevos.
    
- Archivos eliminados.
    
- Rama actual.
    
- Estado respecto del remoto.
    

Por ejemplo:

```
Changes not staged for commit:
    modified: app.component.ts
```

Significa:

```
archivo modificado
        ↓
todavía NO está en staging
```

---

# Archivos tracked

Un archivo **tracked** es un archivo que Git ya está siguiendo.

Git conoce su existencia y puede detectar sus modificaciones.

```
archivo tracked
      ↓
lo modifico
      ↓
Git detecta el cambio
```

---

# Archivos untracked

Un archivo **untracked** es un archivo nuevo que Git todavía no está siguiendo.

Por ejemplo:

```
Untracked files:
    src/app/app.routes.ts
```

Significa que `app.routes.ts` existe en nuestra computadora pero todavía no fue agregado al seguimiento.

---

# git add

Para preparar un archivo:

```
git add archivo
```

Por ejemplo:

```
git add src/app/app.routes.ts
```

Para preparar todos los cambios:

```
git add .
```

Después de `git add`, los cambios quedan preparados para el próximo commit.

---

# Sacar un archivo del staging

Si agregamos un archivo pero todavía no queremos incluirlo en el commit:

```
git restore --staged archivo
```

El cambio **no desaparece**.

Simplemente vuelve de:

```
STAGING
   ↓
WORKING DIRECTORY
```

---

# git diff

Permite ver las diferencias entre nuestros archivos y la última versión registrada.

```
git diff
```

Muestra principalmente cambios que todavía **no están en staging**.

---

# Cambios que ya están en staging

Para revisar lo que vamos a incluir en el próximo commit:

```
git diff --staged
```

Esto permite revisar antes de ejecutar:

```
git commit
```

---

# Flujo recomendado

```
git status
git diff
git add .
git diff --staged
git status
git commit -m "mensaje"
```

Conceptualmente:

```
¿Qué tengo?
→ git status

¿Qué cambié?
→ git diff

¿Qué quiero guardar?
→ git add

¿Qué preparé?
→ git diff --staged

Guardar versión
→ git commit
```

---

# Machete

```
tracked
→ Git ya conoce el archivo

untracked
→ archivo nuevo que Git todavía no sigue

modified
→ archivo conocido que fue modificado

staged
→ cambio preparado para el próximo commit

git add
→ llevar cambios al staging

git restore --staged
→ sacar cambios del staging sin borrarlos

git diff
→ ver cambios sin preparar

git diff --staged
→ ver cambios preparados
```

Ver también [[Git]], [[Commits]] y [[Deshacer Cambios]].