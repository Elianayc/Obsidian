Dividen el problema en subproblemas para simplificar el desarrollo de un programa.

---

### Desarrollo Top Down
Metodología de división por módulos.
Realizaremos un algoritmo principal y varios subalgoritmos para ir resolviendo cada uno de los subproblemas.

- Subproblemas
- Módulos
- Subprogramas
- Rutinas
- Subrutinas

---

### Razones para modularizar

- Simplifica el programa.
- Permite la reutilización de código: se pueden reutilizar módulos, lo que evita "reinventar la rueda".
- Algoritmo más simple y más claro: el algoritmo principal será una pequeña lista de módulos. Se entiende la idea de lo que realiza sin la necesidad de acceder a los detalles de cómo resuelve cada cosa.
- El programa es más simple de verificar: las pruebas pueden ejecutarse en cada módulo de forma independiente.
- Reduce tiempos de mantenimiento.

---

### Abstracción
Cada módulo es independiente de los demás módulos y lo ideal es que realice una sola tarea.
La abstracción es el aislamiento de un elemento de su contexto o el resto de los elementos que lo acompañan.

---
### Ocultamiento de la información
La información de un módulo no es de interés para el resto, por lo que queda oculta en él.

---

[[Comunicación entre módulos]]

[[Tipos de módulos]]


---

### Ámbito de las variables
Es el espacio donde una variable "vive" y puede ser utilizada. Este espacio se divide en ámbitos y cada parte de un programa (el principal o los módulos) tiene su propio ámbito.

#### Ámbito Global
Las variables globales se definen fuera del main.
Son accesibles desde todo el programa, pero no se deben usar directamente desde módulos o funciones.
Si una función las necesita debe recibirla como parámero, para respetar la abstracción.

#### Ejemplo
```C++
int g; //Variable global.

int main(){
	int a = 10, b = 20; //Variables locales.
	g = a + b;
	
	cout <<g; //Muestro resultado.
	
	return 0;
}
```

#### Ámbito Local
Las variables que se definen dentro de una funci´pon o bloque de código pertenecen al ámbito local en el que fueron definidas.
Solo existen mientras se ejecuta la función. Luego se eliminan de la memoria.
También son locales los parámetros de una función.

#### Ejemplo
```C++
float CalcularPromedioNotas(int nota1, int nota2){ //Parámetros locales.
	int promedio = 0; //Variable loca.
	promedio = (nota1 + nota2)/2;
	return promedio;
}
```

#### Beneficios de respetar ámbitos
- Mejora la organización del código.
- Permite la modularización.
- Evita errores por uso indebido de variables externas.
- Hace que el código sea más legible y fácil de mantener.