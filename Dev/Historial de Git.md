Git mantiene un historial de los commits realizados en el repositorio.

---

# git log

Para consultar el historial:

```
git log
```

Muestra información detallada de los commits.

---

# Historial resumido

```
git log --oneline
```

Por ejemplo:

```
66de2dc C06 Step2
323db54 C05 Step5
c6f8e2f C05 Step4
293d547 C05 Step3
```

Cada línea representa un commit.

---

# Historial como gráfico

Para visualizar ramas y merges:

```
git log --oneline --graph --decorate
```

Ejemplo:

```
*   abc123 Merge branch 'feature'
|\
| * def456 feat: agregar pantalla
* | ghi789 fix: corregir login
|/
* jkl012 commit anterior
```

Es especialmente útil para detectar bifurcaciones del historial.

---

# HEAD

`HEAD` representa nuestra posición actual dentro del historial.

Normalmente apunta al último commit de la rama actual.

```
commit A
   ↓
commit B
   ↓
commit C ← HEAD
```

---

# Referencias relativas

Podemos referirnos a commits anteriores respecto de `HEAD`.

```
HEAD~1
```

significa:

```
1 commit antes de HEAD
```

```
HEAD~2
```

significa:

```
2 commits antes de HEAD
```

Por ejemplo:

```
git rebase -i HEAD~3
```

trabaja con los últimos tres commits.

---

# Hash

También podemos identificar directamente un commit mediante su hash.

Por ejemplo:

```
66de2dc
```

Git puede utilizar ese identificador en diferentes comandos.

Por ejemplo:

```
git reset --hard 66de2dc
```

---

# Decoraciones

Con:

```
git log --oneline --graph --decorate
```

pueden aparecer referencias como:

```
(HEAD -> main, origin/main)
```

Esto significa:

```
HEAD
→ posición actual

main
→ rama local

origin/main
→ referencia del estado de main en el remoto
```

---

# Machete

```
git log
→ historial detallado

git log --oneline
→ historial resumido

git log --oneline --graph --decorate
→ historial + ramas + referencias

HEAD
→ posición actual

HEAD~1
→ un commit anterior

HEAD~2
→ dos commits anteriores

hash
→ identificador de un commit
```

Ver también [[Commits]], [[Ramas y Merge]], [[Rebase]] y [[Deshacer Cambios]].

---
