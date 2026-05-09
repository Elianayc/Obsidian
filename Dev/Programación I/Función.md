---
tags:
  - Programación
  - ProgramaciónI
---
Una **función** es un módulo de un programa que recibe datos de entrada (parámetros), realiza un procesamiento y devuelve **un único valor de salida**.
Contiene un grupo de instrucciones. Permite encapsular comportamiento. 


### Estructura en C++
```cpp
tipo_de_retorno nombre_funcion(lista_parametros) {
    cuerpo_de_la_funcion
}
```

#### Partes de una función

- **tipo_de_retorno**: tipo de dato que devuelve la función (int, float, char, etc.).
- **nombre_funcion**: identificador de la función.
- **lista_parametros**: conjunto de variables que recibe la función como entrada.
- **cuerpo_de_la_funcion**: bloque de instrucciones que define lo que hace la función.


---

### Parámetros vs argumentos

- **Parámetros**: variables declaradas en la función (en su definición).
- **Argumentos**: valores reales que se envían al llamar la función.

---

### Firma de una función
La **firma de una función** es la parte que identifica de manera única a una función dentro de un programa.

Está compuesta por:
- el **nombre de la función**
- el **tipo, cantidad y orden de los parámetros**

`nombre_funcion(lista_parametros)`

No incluye el tipo de retorno en muchos lenguajes como C++ (esto depende del lenguaje).

---
### Ejemplo

Función que retorna el máximo entre dos valores:
```cpp
int maximo(int a, int b) {
	int resultado; //Declaración de variable local: solo puede ser accedida desde el módulo dónde se declaran.
	
    if (a > b) {
        result = a;
    } else {
        result = b;
    }
    
    return result; //También podemos devolver directamente a o b, según corresponda.
}
```

La función se declara antes del `main`, normalmente solo con su firma, y luego se define su implementación después. Esto permite que el compilador la reconozca desde el inicio y facilita separar el código en archivos `.h` (declaraciones) y `.cpp` (implementación), mejorando la organización y modularidad del programa.

Uso:
```cpp
int resultado = maximo(5, 10);
```

