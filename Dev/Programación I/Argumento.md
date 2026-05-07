Los **argumentos** son los valores reales que se envían a una función cuando es llamada. Esos valores “rellenan” los parámetros definidos en la función.

En otras palabras: los parámetros son la definición, y los argumentos son lo que efectivamente se pasa en la ejecución.

**Ejemplo:**
```C++
int suma(int a, int b) {   // a y b son parámetros    
	return a + b;
}

int resultado = suma(5, 10);  // 5 y 10 son argumentos
```