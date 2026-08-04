---
tags:
  - Programación
  - ProgramaciónI
  - ProgramaciónII
---
C# es un lenguaje moderno, compilado y orientado a objetos creado por Microsoft.  
Se ejecuta sobre la plataforma .NET y se usa para aplicaciones de escritorio, web, móviles, videojuegos (Unity) y servicios.

Es más seguro y automatiza la gestión de memoria (garbage collector).

### **Sintaxis básica**

##### Estructura mínima de un programa:
```C#
using System;  
  
class Program {  
	static void Main() {  
		Console.WriteLine("Hola mundo");  
	}  
}
```

##### Elementos clave:
- `#include` → importa librerías.
- `main()` → punto de entrada del programa.
- `printf()` → salida por pantalla.
- `return 0` → indica que el programa terminó correctamente.

##### Variables:
```C#
int edad = 20;  
double altura = 1.70;  
string nombre = "Ana";
```

##### Condicional:
```C#
if (edad >= 18) {    
	Console.WriteLine("Mayor de edad");
}
```

##### Clase básica:
```C#
class Persona {  
	public string Nombre;  
	public int Edad;  
	  
	public void Saludar() {  
		Console.WriteLine("Hola soy " + Nombre);  
	}  
}
```

#Programación