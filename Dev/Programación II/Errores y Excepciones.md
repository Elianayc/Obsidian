---
tags:
  - Programación
  - ProgramaciónII
---
#### 1. Errores sintácticos y semánticos
Errores de diseño. Son fáciles de detectar por el IDE o el compilador.

#### 2. Errores de lógica
Cumplen con la sintaxis y semántica, pero el programa no funciona como se espera.  
Son errores en la ejecución (bugs).

#### 3. Eventos externos
Situaciones externas al programa que pueden afectar su ejecución (por ejemplo, pérdida de conexión, archivo inexistente, etc.).

---

## Excepción
Una excepción ocurre cuando el flujo normal del programa se interrumpe por un evento no contemplado (punto 2 o 3), lo que puede provocar la terminación del programa si no es manejada correctamente.

---

## Control de excepciones
La mayoría de los lenguajes de alto nivel implementan el bloque de control **try/catch**, cuyo objetivo es manejar situaciones excepcionales y definir un camino alternativo de ejecución.

---

## Estructura de un bloque try/catch

### Try
Encierra el código que se espera ejecutar normalmente.  
Contiene el código que podría generar un error.

### Catch
Contiene el manejo de la excepción.  
Define el camino alternativo cuando ocurre un error.

### Finally
Subbloque opcional que se ejecuta siempre, haya o no error.  
Se utiliza generalmente para tareas de limpieza o liberación de recursos.

> Si un bloque try/catch intercepta una excepción, el flujo salta inmediatamente al `catch` correspondiente y se omite el resto del `try`.


#### Orden de los catch
Siempre deben declararse primero los `catch` más específicos y al final los más genéricos.
Se ejecuta el primer `catch` que coincida con el tipo de error.

---

## Throw
`throw` se utiliza para lanzar una excepción.

**Ejemplo:**
```
throw new Error("Error de...");
```

Se utiliza dentro de un `try` o dentro de una función.


#### Propagación de excepciones
Si se lanza una excepción dentro de un bloque `try`, esta será capturada inmediatamente por el `catch` correspondiente dentro del mismo contexto o se propagará hacia arriba si no es manejada.

#### Excepciones personalizadas
Se crean extendiendo la clase `Error`.