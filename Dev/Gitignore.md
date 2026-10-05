El archivo `.gitignore` permite indicar archivos y carpetas que Git debería **ignorar**.

Esto significa que Git no debería comenzar a seguirlos automáticamente.

---

# Ejemplo

```
node_modules/
.env
*.log
*.tmp
```

---

# Carpetas

Para ignorar una carpeta:

```
node_modules/
```

---

# Archivos específicos

```
.env
```

---

# Extensiones

Para ignorar todos los archivos con determinada extensión:

```
*.log
```

Esto puede ignorar:

```
error.log
app.log
debug.log
```

---

# ¿Para qué sirve?

Puede utilizarse para evitar versionar:

- Dependencias instaladas.
- Archivos temporales.
- Logs.
   
- Configuraciones locales.
    
- Archivos generados automáticamente.
    
- Determinada información sensible.
    

---

# Importante: archivos ya tracked

`.gitignore` afecta principalmente archivos que Git todavía no está siguiendo.

Si un archivo **ya está tracked**, agregarlo a `.gitignore` no hace que Git deje automáticamente de seguirlo.

Por ejemplo:

```
archivo ya tracked
       +
lo agrego a .gitignore
       ↓
Git puede seguir rastreándolo
```

---

# Dejar de seguir sin borrar localmente

Puede utilizarse:

```
git rm --cached archivo
```

Para una carpeta:

```
git rm -r --cached carpeta
```

Esto quita el archivo del seguimiento de Git pero permite conservarlo localmente.

Después corresponde registrar ese cambio mediante un commit.

---

# Comprobar si algo está ignorado

Puede utilizarse:

```
git check-ignore -v ruta
```

Por ejemplo:

```
git check-ignore -v Dev/.obsidian/workspace.json
```

Además de indicar si está ignorado, `-v` permite ver qué regla de `.gitignore` produjo el resultado.

---

# Ejemplo conceptual

```
.gitignore
    │
    ├── node_modules/
    ├── *.log
    └── .env
          ↓
Git evita comenzar
a seguir esos archivos
```

---

# Machete

```
.gitignore
→ reglas de archivos que Git debe ignorar

carpeta/
→ ignorar carpeta

*.log
→ ignorar extensión

git rm --cached
→ dejar de seguir sin borrar localmente

git check-ignore -v
→ comprobar qué regla ignora una ruta
```

Ver también [[Git]] y [[Estados y Staging]].