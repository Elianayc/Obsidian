La **validación de inputs** consiste en comprobar que los datos recibidos por la API sean válidos, tengan el formato esperado y se encuentren dentro de los valores permitidos.

Es una de las primeras líneas de defensa contra **datos maliciosos y ataques de inyección**.

---

## Principios fundamentales

1. **Validar todo:** nunca confiar directamente en los datos enviados por el cliente.
2. **Sanitización:** limpiar los datos antes de procesarlos cuando sea necesario.
3. **Whitelist vs Blacklist:** preferir una lista de valores permitidos en lugar de intentar enumerar todos los valores peligrosos.

---

## Validación de formato

Por ejemplo, utilizando Joi:

```js
const Joi = require('joi');

const userSchema = Joi.object({
  email: Joi.string().email().required(),
  age: Joi.number().integer().min(18).max(120),
  name: Joi.string().alphanum().min(2).max(50).required()
});

app.post('/users', (req, res) => {
  const { error, value } = userSchema.validate(req.body);

  if (error) {
    return res.status(400).json({
      error: error.details[0].message
    });
  }

  // Procesar datos validados...
});
```

---

## Validación de tipos y rangos

También es necesario comprobar que los datos sean del **tipo esperado** y estén dentro de un rango válido.

```
function validateProductPrice(price) {
  if (typeof price !== 'number' || price < 0 || price > 999999) {
    throw new Error('Precio inválido');
  }

  return true;
}
```

---

## Defensa contra ataques comunes

- **SQL Injection:** utilizar consultas parametrizadas.
- **XSS (Cross-Site Scripting):** escapar caracteres especiales.
- **NoSQL Injection:** validar estrictamente los tipos de datos.

---

