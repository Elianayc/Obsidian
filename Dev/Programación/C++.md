---
tags:
  - Programación
  - ProgramaciónI
  - ProgramaciónII
---
C++ es una evolución de C que agrega programación orientada a objetos sin perder eficiencia.  
Permite programar en varios paradigmas: procedural, orientado a objetos y genérico.

Se usa mucho en videojuegos, motores gráficos, sistemas, software de alto rendimiento y aplicaciones complejas.

### **Sintaxis básica**

##### Estructura mínima de un programa:
```cpp
#include <iostream>  
using namespace std;  
  
int main() {  
	cout << "Hola mundo";  
	return 0;  
}
```

##### Elementos clave:
- `#include` → importa librerías.
- `main()` → punto de entrada del programa.
- `printf()` → salida por pantalla.
- `return 0` → indica que el programa terminó correctamente.

##### Variables:
```cpp
int edad = 20;  
double altura = 1.70;  
string nombre = "Ana";
```

##### Leer y escribir:
```cpp
#include <iostream>  
using namespace std;  
  
int main() {  

	int a=0, b=0, r=0; //Declaraciones
	
	cin >> a; //Console in
	cin >> b;
	
	r= a+b; //Operación
	
	cout << r;  //Console out
}
```

##### If-Else:
```cpp
if(condición){ //Si...
	...
}
else if (condición){ //Sino si...
	...
}
else{ //Sino
	...
}
```

##### Switch:
```cpp
switch(var){
	case 1: { //Cada caso lleva {}, opcional pero recomendado.
	...
	break; //Casa case termina con un break sí o sí.
	}
	case 2:{
	...
	break;
	}
	default: { //El default es opcional pero recomendado.
	instrucción; //Si existe default debe tener al menos una instrucción.
	break; //Break opcional pero recomendable.
	}
}
```

##### While:
```cpp
while (condición){
	...
}
```

##### Do while:
```cpp
do{ //Hace al menos una vez.
	...
}while (condición); //Se repite mientras se cumpla la condición.
```

##### For:
```cpp
for(i=valorInicio; i<valorFin; i++){ //Inicio, fin, incremento.
	...
}
```

##### Clase básica:
```cpp
class Persona {  
	public:  
	string nombre;  
	int edad;  
  
	void saludar() {  
	cout << "Hola soy " << nombre;  
	}  
};
```

##### Salida por pantalla:
- `cout` en lugar de `printf`.
#Programación