`stash` permite guardar temporalmente cambios que todavía no queremos convertir en un commit.

Sirve cuando estamos trabajando y necesitamos temporalmente un Working Directory limpio.

```
CAMBIOS SIN COMMIT
        │
        │ git stash
        ▼
GUARDADOS TEMPORALMENTE
```

---

# Guardar cambios

```
git stash
```

Git guarda temporalmente los cambios y restaura el Working Directory.

---

# Guardar con descripción

```
git stash push -m "trabajo en progreso"
```

Esto permite reconocer fácilmente qué contiene el stash.

---

# Archivos untracked

Si también queremos incluir archivos nuevos que todavía están `untracked`:

```
git stash push -u
```

Por ejemplo:

```
git stash push -u -m "C06 Step2 en progreso"
```

`-u` incluye los archivos untracked.

---

# Ver stash guardados

```
git stash list
```

Puede mostrar:

```
stash@{0}: C06 Step2 en progreso
stash@{1}: cambios anteriores
```

---

# Recuperar cambios

```
git stash pop
```

Aplica el stash y, si todo sale correctamente, lo elimina de la lista.

---

# Aplicar sin eliminar

```
git stash apply
```

Aplica los cambios pero mantiene el stash guardado.

---

# Diferencia

```
git stash pop
→ recuperar + quitar de la lista

git stash apply
→ recuperar + conservar en la lista
```

---

# Cuándo usarlo

Por ejemplo:

```
Estoy trabajando en C06 Step2
        ↓
todavía no quiero hacer commit
        ↓
necesito cambiar de tarea/rama
        ↓
git stash
        ↓
trabajo temporalmente en otra cosa
        ↓
git stash pop
        ↓
continúo C06 Step2
```

---

# Stash no reemplaza a los commits

El stash está pensado como almacenamiento **temporal**.

Si el trabajo ya constituye una versión lógica y terminada, normalmente corresponde hacer un [[Commits|commit]].

---

# Machete

```
git stash
→ guardar temporalmente cambios

git stash push -u
→ incluir archivos nuevos

git stash list
→ ver stash

git stash pop
→ recuperar y eliminar stash

git stash apply
→ recuperar sin eliminar stash
```

Ver también [[Estados y Staging]] y [[Commits]].

---
