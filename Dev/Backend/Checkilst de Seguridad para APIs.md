
## Configuración básica

- [ ] HTTPS habilitado con certificado válido.
- [ ] Rate limiting implementado.
- [ ] Validación de inputs en todos los endpoints.
- [ ] Autenticación robusta.
- [ ] JWT correctamente implementado cuando corresponda.
- [ ] Secretos fuertes y protegidos.
- [ ] Autorización granular mediante RBAC.

---

## Mejores prácticas

- [ ] Headers de seguridad configurados.
- [ ] CORS correctamente configurado.
- [ ] Logs de seguridad implementados.
- [ ] Monitoreo activo.
- [ ] Las respuestas de error no exponen información sensible.
- [ ] Los secretos no están almacenados directamente en el código.

---

## Datos sensibles

- [ ] Nunca registrar credenciales en los logs.
- [ ] Nunca registrar tokens en los logs.
- [ ] Enmascarar información personal sensible en los logs.
- [ ] Cifrar datos sensibles almacenados en la base de datos.
- [ ] Utilizar variables de entorno para almacenar secretos.

---

## Seguridad como proceso continuo

La seguridad de una API REST requiere un **enfoque multicapa** que combine diferentes mecanismos de protección.

Ninguna medida por sí sola garantiza la seguridad de una API.

La seguridad no es un estado final, sino un **proceso continuo** que requiere actualizaciones regulares, monitoreo constante y adaptación frente a nuevas amenazas.

---