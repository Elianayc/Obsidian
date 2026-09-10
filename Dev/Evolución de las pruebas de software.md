
### Depuración y control de calidad

Inicialmente, la **depuración ([[Debugging]])** era el principal método para encontrar y corregir errores.

Durante la década de 1980, las pruebas comenzaron a adoptar una visión más amplia, incorporando el **control y la garantía de calidad** como parte fundamental del desarrollo.

Las pruebas pasaron a integrarse al **[Ciclo de Vida del Desarrollo de Software (SDLC)](Ciclo%20de%20Vida%20del%20Desarrollo%20de%20Software)**.

---

### Caja negra y caja blanca

Durante los años 70 se sistematizaron dos enfoques:

- **Caja negra:** se prueba el sistema desde afuera, sin conocer su código interno. Se analizan principalmente entradas y salidas.
- **Caja blanca:** se prueba teniendo en cuenta la estructura interna, lógica, ramas y caminos del código.

Glenford Myers también planteó que el programador no debería ser necesariamente quien pruebe su propio código, debido al posible sesgo al buscar errores en algo que él mismo desarrolló.

---

### Automatización

Durante los años 80 y 90 aparecieron herramientas de automatización para poder ejecutar pruebas repetitivas a mayor escala.

---

### Agile y TDD

Con el **Manifiesto Ágil de 2001**, desarrollo y testing dejaron de verse como etapas completamente separadas.

Kent Beck formalizó el **Test-Driven Development (TDD)**, donde se escribe primero la prueba y luego el código necesario para hacerla pasar.

---

### DevOps y testing continuo

Con **CI/CD (Integración Continua y Entrega o Despliegue Continuo)**, las pruebas pasaron a formar parte de un flujo permanente.

Actualmente las pruebas pueden ser:

- Continuas.
- Automatizadas.
- Integradas durante todo el desarrollo.
- Ejecutadas en diferentes entornos.

---
