La **validación de inputs** consiste en comprobar que los datos recibidos por una API sean válidos, tengan el formato esperado y se encuentren dentro de los valores permitidos.

Es una de las primeras líneas de defensa del backend contra **datos maliciosos y ataques de inyección**.

> **Importante:** aunque el frontend también puede validar datos para mejorar la experiencia del usuario, el **backend siempre debe volver a validarlos**, porque no puede confiar en los datos enviados por el cliente.

---

## Principios fundamentales

### 1. Validar todo

Nunca se debe confiar directamente en los datos enviados por el cliente.

Por ejemplo, si una API espera:

```json
{
  "name": "Eliana",
  "age": 38
}
```

el servidor debería comprobar que:

- `name` sea un texto;
    
- `age` sea un número;
    
- `age` esté dentro de un rango válido;
    
- los datos tengan la estructura esperada.
    

---

### 2. Sanitización

La **sanitización** consiste en limpiar o transformar los datos recibidos antes de utilizarlos, cuando sea necesario.

Por ejemplo, eliminar o transformar determinados caracteres o espacios innecesarios.

La diferencia es:

- **Validación:** comprobar si el dato cumple las reglas.
    
- **Sanitización:** limpiar o transformar el dato antes de utilizarlo.
    

---

### 3. Whitelist vs. Blacklist

Una **whitelist** (lista blanca) define explícitamente qué valores están permitidos.

Por ejemplo:

```text
roles permitidos:
- admin
- user
- editor
```

Una **blacklist** (lista negra) intenta definir qué valores o patrones están prohibidos.

En seguridad suele ser preferible utilizar **whitelists**, porque es más seguro definir explícitamente qué está permitido que intentar anticipar todas las formas posibles de datos peligrosos.

---

## Validación de formato

Una API puede recibir datos con diferentes reglas de formato.

Por ejemplo:

- `email` debe tener un formato de correo válido.
    
- `age` debe ser un número entero.
    
- `name` debe ser un texto con determinada longitud.
    

Para facilitar estas validaciones existen librerías como **Joi**.

### ¿Qué es Joi?

**Joi es una librería de JavaScript que permite definir reglas de validación mediante esquemas.**

Por ejemplo:

```js
const Joi = require('joi');

const userSchema = Joi.object({
  email: Joi.string().email().required(),
  age: Joi.number().integer().min(18).max(120),
  name: Joi.string().alphanum().min(2).max(50).required()
});
```

Este esquema establece las reglas que debe cumplir un usuario.

Por ejemplo:

- `email` → debe ser un texto con formato de email y es obligatorio.
    
- `age` → debe ser un número entero entre 18 y 120.
    
- `name` → debe ser un texto de entre 2 y 50 caracteres y es obligatorio.
    

### ¿Y qué es Express?

**Express es un framework de Node.js que facilita la creación de servidores y APIs.**

Permite, entre otras cosas, definir las rutas que recibe la API:

```js
app.post('/users', (req, res) => {
  // Procesar el request
});
```

En este ejemplo:

- **Express** se encarga de recibir el `POST /users`.
    
- **Joi** puede encargarse de comprobar que los datos recibidos sean válidos.
    

Conceptualmente:

```text
Cliente
   ↓
POST /users + datos
   ↓
Express recibe el request
   ↓
Joi valida los datos
   ↓
¿Son válidos?
   ├── No → Error 400
   └── Sí → Continúa el procesamiento
```

---

## Validación de tipos y rangos

No solo hay que comprobar el formato. También hay que verificar que los datos sean del **tipo esperado** y estén dentro de los **rangos permitidos**.

Por ejemplo, si una API recibe el precio de un producto:

```js
function validateProductPrice(price) {
  if (typeof price !== 'number' || price < 0 || price > 999999) {
    throw new Error('Precio inválido');
  }

  return true;
}
```

En este caso se comprueba que:

- `price` sea un número;
    
- no sea negativo;
    
- no supere `999999`.
    

---

## Defensa contra ataques comunes

La validación de inputs también ayuda a reducir determinados ataques:

### SQL Injection

Ocurre cuando datos enviados por el usuario pueden alterar una consulta SQL.

Una medida de protección es utilizar **consultas parametrizadas**, evitando construir consultas SQL concatenando directamente datos del usuario.

### XSS — Cross-Site Scripting

Consiste en conseguir que contenido proporcionado por un usuario sea interpretado como código HTML o JavaScript.

Una medida de protección es **escapar o codificar correctamente los caracteres especiales** antes de mostrar contenido que proviene de usuarios.

### NoSQL Injection

Es una inyección dirigida a bases de datos NoSQL.

Una medida de protección es realizar una **validación estricta de los tipos y estructuras de los datos recibidos**, además de utilizar consultas seguras.

---
