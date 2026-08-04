Son formas de **identificar recursos** dentro de una red.

---

## URI (Uniform Resource Identifier)

Una **URI** es una cadena de caracteres que permite **identificar un recurso de forma única**.

Dentro de las URI existen dos tipos principales:
- **[[URL]] (Uniform Resource Locator)**
- **[[URN]] (Uniform Resource Name)**

---

## Componentes de una URI
Una URI puede estar formada por:

- **Esquema:** indica cómo interpretar el identificador o el protocolo utilizado.
  - Ejemplos: `http`, `https`, `mailto`, `ftp`, `urn`.

- **Autoridad:** identifica quién controla o dónde se encuentra el recurso.
  - Ejemplo: `//www.example.com`

- **Ruta:** indica la ubicación del recurso dentro del servidor.
  - Ejemplo: `/productos/index.html`

- **Consulta:** información adicional enviada al recurso, generalmente en formato clave=valor.
  - Comienza con `?`
  - Ejemplo: `?usuario=juan`

- **Fragmento:** identifica una parte específica dentro del recurso.
  - Comienza con `#`
  - Ejemplo: `#contacto`

---
#Redes #ProgramaciónIII