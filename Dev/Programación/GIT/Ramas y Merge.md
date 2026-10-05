Una **rama** o **branch** es una línea de desarrollo independiente dentro del repositorio.

La rama principal suele llamarse:

```
main
```

---

# ¿Para qué sirven?

Permiten desarrollar funcionalidades sin trabajar directamente sobre la rama principal.

```
main
 │
 ├── commit
 │
 └──────────────┐
                          │
                    feature/r7
                          │
                          ├── commit
                         └── commit
```

Por ejemplo, podemos desarrollar una funcionalidad R7 en:

```
feature/r7
```

y mantener `main` separada hasta que corresponda integrar el trabajo.

---

# Ver ramas

```
git branch
```

Por ejemplo:

```
* main
  feature/r7
```

El `*` indica la rama actual.

---

# Crear una rama

```
git branch nombre-rama
```

Por ejemplo:

```
git branch feature/r7
```

Esto crea la rama pero no cambia hacia ella.

---

# Cambiar de rama

```
git switch feature/r7
```

---

# Crear y cambiar directamente

```
git switch -c feature/r7
```

Equivale conceptualmente a:

```
crear rama
    +
cambiar a la rama
```

---

# Merge

**Merge** permite integrar el trabajo de una rama dentro de otra.

Supongamos:

```
main
 │
 A
 │
 B
  \
   C
   D
   ↑
feature/r7
```

Si queremos integrar `feature/r7` en `main`, primero nos posicionamos en `main`:

```
git switch main
```

Después:

```
git merge feature/r7
```

La idea es:

```
feature/r7
     │
     │ merge
     ▼
    main
```

---

# Regla mental del merge

Cuando ejecutamos:

```
git merge otra-rama
```

estamos diciendo:

> Traé los cambios de `otra-rama` a la rama en la que estoy parado.

Por eso es importante saber primero cuál es nuestra rama actual:

```
git branch
```

---

# Fast-forward

Si `main` no tuvo nuevos commits desde que creamos nuestra rama, Git puede simplemente avanzar `main`.

Antes:

```
A──B main
    \
     C──D feature
```

Después:

```
A──B──C──D main
```

No necesita crear un commit de merge adicional.

---

# Merge commit

Si ambas ramas avanzaron independientemente:

```
A──B──E main
    \
     C──D feature
```

Git puede crear un commit de merge:

```
A──B──E────M
    \     /
     C──D
```

`M` representa el commit que une ambas historias.

---

# Antes de hacer merge

Conviene revisar:

```
git status
```

y confirmar en qué rama estamos:

```
git branch
```

---

# Si hay conflictos

Si Git no puede combinar automáticamente los cambios, aparece un [[Conflictos en Git|conflicto]].

Hay que resolverlo antes de terminar la integración.

---

# Machete

```
git branch
→ ver ramas

git branch nombre
→ crear rama

git switch nombre
→ cambiar de rama

git switch -c nombre
→ crear + cambiar

git merge rama
→ traer esa rama a mi rama actual
```

Ver también [[GIT]], [[Conflictos en Git]], [[Repositorios Remotos]] y [[Git Rebase]].

---
