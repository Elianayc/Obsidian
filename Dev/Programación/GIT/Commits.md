Un **commit** representa una versión guardada del proyecto dentro del historial de Git.

Un commit contiene información como:

```
COMMIT
├── cambios
├── autor
├── fecha
├── mensaje
└── identificador
```

---

# Crear un commit

Primero los cambios deben estar en el [[Estados y Staging|Staging Area]].

Después:

```
git commit -m "mensaje"
```

Por ejemplo:

```
git commit -m "feat: agregar pantalla de login"
```

---

# Hash

Cada commit posee un identificador único llamado **hash**.

Por ejemplo:

```
66de2dc C06 Step2
323db54 C05 Step5
c6f8e2f C05 Step4
```

En:

```
66de2dc C06 Step2
```

tenemos:

```
66de2dc
→ hash abreviado

C06 Step2
→ mensaje del commit
```

Si se reescribe un commit, puede cambiar su hash.

---

# Autor

Git guarda dentro del commit el nombre y email del autor.

Consultar el nombre:

```
git config user.name
```

Consultar el email:

```
git config user.email
```

---

# Configuración global

Para configurar el nombre utilizado en los commits:

```
git config --global user.name "Eliana Yasmín Carro"
```

El email se configura mediante:

```
git config --global user.email "email"
```

La configuración `--global` se aplica normalmente a los repositorios del usuario de esa computadora.

---

# Configuración local

Un repositorio puede tener una configuración propia que sobrescriba la configuración global.

Para saber de dónde proviene un valor:

```
git config --show-origin --get user.name
```

```
git config --show-origin --get user.email
```


Ver [[Conventional Commits]]

---

