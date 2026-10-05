Un **repositorio remoto** es una versión del repositorio almacenada en otro lugar, por ejemplo GitHub.

```
COMPUTADORA
Repositorio local
       ↕
    Internet
       ↕
GITHUB
Repositorio remoto
```

---

# origin

El remoto principal suele recibir el nombre:

```
origin
```

`origin` no significa GitHub.

Es simplemente el nombre convencional que Git suele asignar al repositorio remoto principal.

---

# Ver remotos

```
git remote -v
```

Por ejemplo:

```
origin  https://github.com/usuario/proyecto.git
```

---

# Clonar

Para traer un repositorio por primera vez:

```
git clone URL
```

Conceptualmente:

```
GITHUB
   │
   │ git clone
   ▼
REPOSITORIO LOCAL
```

---

# main y origin/main

```
main
```

es nuestra rama local.

```
origin/main
```

es nuestra referencia local del estado conocido de `main` en el remoto.

No son exactamente la misma cosa.

---

# git fetch

```
git fetch
```

Trae información nueva del remoto pero no integra automáticamente esos cambios en nuestra rama.

```
REMOTO
   │
   │ fetch
   ▼
actualizo información
del remoto
```

---

# git pull

```
git pull
```

Trae cambios del remoto e intenta integrarlos en nuestra rama actual.

Simplificando:

```
git pull
    ↓
traer cambios
    +
integrarlos
```

---

# git push

```
git push
```

Envía nuestros commits locales al repositorio remoto.

```
LOCAL
commits nuevos
     │
     │ push
     ▼
REMOTO
```

---

# Primera subida de una rama

Cuando una rama local todavía no tiene asociada una rama remota puede utilizarse:

```
git push -u origin nombre-rama
```

Por ejemplo:

```
git push -u origin feature/r7
```

`-u` establece la relación entre la rama local y la remota.

Después normalmente alcanza con:

```
git push
```

---

# Rama actualizada

`git status` puede indicar:

```
Your branch is up to date with 'origin/main'.
```

Significa que nuestra rama local y la referencia remota correspondiente están sincronizadas.

---

# Ahead

Si tenemos commits locales todavía no subidos, Git puede indicar que estamos **ahead**.

Conceptualmente:

```
origin/main
    │
    A
    │
    B
    │
    C ← main

C todavía no está en GitHub
```

Necesitamos:

```
git push
```

---

# Behind

Si el remoto tiene commits que todavía no tenemos localmente, podemos estar **behind**.

```
main
 │
 A
 │
 B
 │
 C ← origin/main
```

Hay cambios remotos que todavía debemos traer.

---

# Push forzado

Cuando se reescribe un historial que ya estaba publicado puede ser necesario:

```
git push --force-with-lease
```

Esto reemplaza el historial remoto por el nuevo historial local, realizando una comprobación adicional antes de hacerlo.

Es preferible a:

```
git push --force
```

pero igualmente debe utilizarse con cuidado.

En ramas compartidas puede afectar el trabajo de otras personas.

---

# Machete

```
origin
→ nombre habitual del remoto principal

git clone
→ traer repositorio por primera vez

git remote -v
→ ver remotos

git fetch
→ traer información sin integrar

git pull
→ traer + integrar

git push
→ subir commits

main
→ rama local

origin/main
→ referencia del main remoto
```

Ver también [[Git]], [[Ramas y Merge]] y [[Conflictos en Git]].

---
