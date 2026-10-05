
Un **tag** permite asignar un nombre a un punto específico del historial.

Se utiliza habitualmente para marcar:

- Versiones.
- Releases.
- Entregas.
- Checkpoints.
    

---

# Idea general

Tenemos:

```
commit A
   ↓
commit B
   ↓
commit C
```

Podemos marcar `commit C`:

```
commit A
   ↓
commit B
   ↓
commit C ← checkpoint-2
```

El tag permite encontrar ese punto del historial fácilmente.

---

# Crear un tag

Para crear un tag sobre el commit actual:

```
git tag checkpoint-2
```

El tag queda asociado al commit señalado actualmente por `HEAD`.

---

# Ver tags

```
git tag
```

Por ejemplo:

```
checkpoint-1
checkpoint-2
checkpoint-3
```

---

# Crear un tag sobre otro commit

También podemos indicar un hash:

```
git tag checkpoint-2 HASH
```

Por ejemplo:

```
git tag checkpoint-2 66de2dc
```

---

# Los tags no se suben necesariamente con push

Hacer:

```
git push
```

no implica necesariamente subir todos los tags locales.

Para subir uno específico:

```
git push origin checkpoint-2
```

---

# Subir todos los tags

```
git push --tags
```

---

# Ver dónde está un tag

El historial decorado puede mostrarlo:

```
git log --oneline --decorate
```

Por ejemplo:

```
abc123 (HEAD -> main, tag: checkpoint-2) entrega CP2
```

---

# Tags y ramas no son lo mismo

Una rama normalmente avanza cuando agregamos commits.

```
main
 │
 A
 │
 B
 │
 C
 │
 D ← main
```

Un tag permanece marcando el commit al que fue asignado:

```
A
│
B ← checkpoint-2
│
C
│
D ← main
```

Conceptualmente:

```
RAMA
→ línea de desarrollo que avanza

TAG
→ marca fija sobre un commit
```

---

# Machete

```
git tag
→ listar tags

git tag nombre
→ crear tag en HEAD

git tag nombre HASH
→ crear tag en otro commit

git push origin nombre
→ subir un tag

git push --tags
→ subir todos los tags
```

Ver también [[Git]], [[Historial de Git]] y [[Commits]].

---
