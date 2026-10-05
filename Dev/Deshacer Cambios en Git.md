Git posee diferentes herramientas para corregir o deshacer cambios.
No todas hacen lo mismo.

Antes de utilizar comandos destructivos conviene revisar:

```
git status
```

y:

```
git diff
```

---

# Descartar cambios de un archivo

Si modificamos un archivo pero todavía no hicimos commit y queremos volver a su versión anterior:

```
git restore archivo
```

Esto puede eliminar modificaciones que todavía no fueron guardadas.

---

# Sacar un archivo del staging

Si ejecutamos:

```
git add archivo
```

pero no queremos incluirlo en el próximo commit:

```
git restore --staged archivo
```

Esto **no elimina el cambio**.

Solamente lo saca del staging.

```
STAGED
   │
   │ restore --staged
   ▼
MODIFIED
```

---

# Diferencia importante

```
git restore --staged archivo
→ conservar cambio, sacar de staging

git restore archivo
→ descartar modificación del archivo
```

---

# Reset

`git reset` permite mover una rama hacia otro commit.

Dependiendo de la opción utilizada también puede afectar el staging y los archivos.

---

# reset --hard

```
git reset --hard HASH
```

Mueve la rama al commit indicado y hace coincidir los archivos con ese estado.

Ejemplo:

```
git reset --hard 66de2dc
```

Conceptualmente:

```
A──B──C──D ← main
      ↑
    reset --hard
```

puede dejar:

```
A──B──C ← main
```

Los commits posteriores dejan de formar parte de esa rama.

---

# Peligro de --hard

`--hard` también puede eliminar modificaciones no guardadas del Working Directory.

Por eso no debe ejecutarse a ciegas.

Antes:

```
git status
```

Y si estamos trabajando con historial:

```
git log --oneline --graph --decorate
```

---

# Cancelar un rebase

Si estamos dentro de un rebase y queremos volver al estado anterior:

```
git rebase --abort
```

---

# Push después de reescribir historial

Si modificamos commits que ya estaban publicados, puede ser necesario actualizar el remoto con:

```
git push --force-with-lease
```

---

# force-with-lease vs force

Existe:

```
git push --force
```

pero es más agresivo.

Es preferible:

```
git push --force-with-lease
```

porque comprueba que el remoto continúe en el estado esperado antes de sobrescribirlo.

Aun así, ambos pueden reescribir el historial remoto.

---

# En ramas compartidas

Si otras personas trabajan sobre la misma rama, reescribir commits publicados puede complicar su historial.

Por eso operaciones como:

- `rebase`
    
- `reset`
    
- `push --force-with-lease`
    

requieren más cuidado cuando el historial ya fue compartido.

---

# Machete

```
git restore archivo
→ descartar cambios del archivo

git restore --staged archivo
→ sacar del staging sin borrar cambios

git reset --hard HASH
→ mover rama y archivos a ese commit

git rebase --abort
→ cancelar rebase

git push --force-with-lease
→ actualizar remoto después de reescribir historial
```

Ver también [[Estados y Staging]], [[Rebase]] y [[Historial de Git]].

---
