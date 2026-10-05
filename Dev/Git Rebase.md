**Rebase** permite cambiar la base de una serie de commits.

También puede utilizarse para reorganizar o modificar commits existentes.

Es una operación que puede **reescribir el historial**.

---

# Idea general

Supongamos:

```
A──B──C
    \
     D──E
```

Un rebase puede volver a aplicar determinados commits sobre otra base.

El resultado puede quedar:

```
A──B──C──D'──E'
```

`D'` y `E'` representan commits nuevos equivalentes a los anteriores.

Como fueron recreados, sus hashes cambian.

---

# Rebase interactivo

```
git rebase -i HEAD~3
```

Significa:

> Quiero trabajar interactivamente con los últimos tres commits.

Puede abrir:

```
pick abc123 primer commit
pick def456 segundo commit
pick ghi789 tercer commit
```

---

# Comandos principales

## `pick`

```
pick
```

Conserva el commit.

---

## `reword`

```
reword
```

Conserva el contenido del commit pero permite modificar su mensaje.

Por ejemplo:

```
reword abc123 C06 Step4
```

Git después permite cambiar el mensaje.

---

## `edit`

```
edit
```

Detiene el rebase en ese commit para permitir modificarlo.

---

## `squash`

```
squash
```

Combina el commit con el anterior.

Por ejemplo:

```
pick abc123 primer cambio
squash def456 corrección del primer cambio
```

puede convertirse en un único commit.

---

## `drop`

```
drop
```

Elimina el commit del nuevo historial.

Debe utilizarse con mucho cuidado.

---

# Reword de un commit

Ejemplo:

Tenemos:

```
C06 Step4
```

pero debería ser:

```
C05 Step4
```

Podemos utilizar:

```
git rebase -i HEAD~N
```

y cambiar:

```
pick HASH C06 Step4
```

por:

```
reword HASH C06 Step4
```

Después Git solicita el nuevo mensaje.

---

# Continuar un rebase

Si Git se detiene:

```
git rebase --continue
```

---

# Cancelar un rebase

Si queremos volver al estado anterior al comienzo del rebase:

```
git rebase --abort
```

Esto es especialmente útil si nos confundimos durante el proceso.

---

# Conflictos

Un rebase puede generar [[Conflictos|conflictos]].

Después de resolverlos:

```
git add archivo
```

y:

```
git rebase --continue
```

---

# Rebase cambia hashes

Cuando Git vuelve a crear un commit, obtiene un hash nuevo.

Antes:

```
7ba42cd C06 Step4
```

Después:

```
c6f8e2f C05 Step4
```

Aunque los archivos puedan contener los mismos cambios, técnicamente son commits distintos.

---

# Rebase y GitHub

Si los commits reescritos ya fueron subidos a GitHub, el historial remoto contiene los hashes anteriores.

Por eso un push normal puede ser rechazado.

En determinados casos puede ser necesario:

```
git push --force-with-lease
```

Esto debe utilizarse con especial cuidado en ramas compartidas.

---

# Merge vs Rebase

```
MERGE
→ une historias

REBASE
→ vuelve a aplicar commits sobre otra base
```

Merge suele conservar explícitamente la bifurcación.

Rebase puede generar un historial más lineal, pero reescribe commits.

---

# Machete

```
git rebase -i HEAD~3
→ editar últimos 3 commits

pick
→ conservar

reword
→ cambiar mensaje

edit
→ modificar commit

squash
→ combinar con anterior

drop
→ eliminar

git rebase --continue
→ continuar

git rebase --abort
→ cancelar
```

Ver también [[Historial]], [[Conflictos]] y [[Deshacer Cambios]].

---
