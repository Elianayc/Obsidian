---
tags:
  - Programación
  - ProgramaciónII
---

- ### Responsabilidad única
	Cada clase debe tener **una única responsabilidad**, es decir, una sola razón para cambiar.

- ### Abierto/cerrado
	Las clases, módulos o funciones deben estar **abiertos a la extensión pero cerrados a la modificación**.

- ### Sustitución de Liskov
	Si una clase A es subtipo de una clase B, los objetos de A deben poder **reemplazar a los de B sin alterar el correcto funcionamiento del programa**.

- ### Segregación de interfaces
	Ningún cliente debe verse obligado a depender de métodos que **no utiliza**. Es mejor tener varias interfaces específicas que una general muy grande.

- ### Inversión de dependencias
	Los módulos de alto nivel **no deben depender de los de bajo nivel**.  
	Ambos deben depender de **abstracciones** (interfaces o clases abstractas).  
	Las abstracciones no deben depender de los detalles; los detalles deben depender de las abstracciones.