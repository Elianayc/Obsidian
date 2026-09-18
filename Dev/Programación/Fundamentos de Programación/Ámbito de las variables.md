---
tags:
  - Programación
  - ProgramaciónII
---
### Ámbito de las variables
Es el espacio donde una variable "vive" y puede ser utilizada. Este espacio se divide en ámbitos y cada parte de un programa (el principal o los módulos) tiene su propio ámbito.

---

#### Ámbito Global
Las variables globales se definen fuera del main.
Son accesibles desde todo el programa, pero no se deben usar directamente desde módulos o funciones.
Si una función las necesita debe recibirla como parámero, para respetar la abstracción.

> [!example]
> 
> ```C++
> int g; //Variable global.
> 
> int main(){
> 	int a = 10, b = 20; //Variables locales.
> 	g = a + b;
> 	
> 	cout <<g; //Muestro resultado.
> 	
> 	return 0;
> }
> ```
> 

---

#### Ámbito Local
Las variables que se definen dentro de una función o bloque de código pertenecen al ámbito local en el que fueron definidas.
Solo existen mientras se ejecuta la función. Luego se eliminan de la memoria.
También son locales los parámetros de una función.

> [!example]
> 
> ```C++
> float CalcularPromedioNotas(int nota1, int nota2){ //Parámetros locales.
> 	int promedio = 0; //Variable loca.
> 	promedio = (nota1 + nota2)/2;
> 	return promedio;
> }
> ```
> 

----

#### Beneficios de respetar ámbitos
- Mejora la organización del código.
- Permite la modularización.
- Evita errores por uso indebido de variables externas.
- Hace que el código sea más legible y fácil de mantener.
#Programación