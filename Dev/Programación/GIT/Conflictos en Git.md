Un **conflicto** ocurre cuando Git no puede decidir automáticamente cómo combinar dos cambios.

Por ejemplo:

```
Versión A modifica línea 10

Versión B modifica también línea 10

              ↓

Git no sabe cuál conservar
```

---

# Cuándo pueden aparecer

Pueden aparecer durante operaciones como:

- `merge`
- `pull`
- `rebase`
- `stash pop`

No significa que Git esté roto.

Significa que necesita que una persona decida cómo debe quedar el archivo.

---

# Marcas de conflicto

Git puede colocar dentro del archivo marcas como:

```
<<<<<<< HEAD
contenido de nuestra versión
=======
contenido de la otra versión
>>>>>>> otra-rama
```

Tenemos tres separadores importantes:

```
<<<<<<<
inicio de una versión

=======
separación entre versiones

>>>>>>>
fin de la otra versión
```

---

# Resolver un conflicto

Hay que editar manualmente el archivo y decidir cómo debe quedar.

Podemos:

- Conservar nuestra versión.
- Conservar la otra.
- Combinar ambas.
- Escribir una nueva versión.

Después debemos eliminar las marcas:

```
<<<<<<<
=======
>>>>>>>
```

---

# Marcar como resuelto

Una vez corregido:

```
git add archivo
```

Esto le indica a Git que ese archivo ya fue resuelto.

---

# Revisar conflictos

```
git status
```

es fundamental durante un conflicto porque Git indica qué archivos necesitan atención.

---

# Conflicto en merge

Después de resolver los archivos y hacer `git add`, se completa el merge según el estado que indique Git.

---

# Conflicto en rebase

Después de resolver:

```
git add archivo
```

y luego:

```
git rebase --continue
```

Si queremos cancelar el rebase:

```
git rebase --abort
```

---

# No hacer

No borrar archivos o ejecutar comandos destructivos solamente para hacer desaparecer el mensaje de conflicto.

Primero:

```
git status
```

Después entender qué operación está activa.

---

# Machete

```
conflicto
→ Git no puede decidir cómo combinar cambios

git status
→ ver qué archivos tienen conflicto

editar archivo
→ decidir resultado final

git add archivo
→ marcar conflicto como resuelto

git rebase --continue
→ continuar un rebase

git rebase --abort
→ cancelar el rebase
```

Ver también [[Ramas y Merge]], [[Git Rebase]] y [[Repositorios Remotos]].

---
