---
tags:
  - Programación
  - ProgramaciónI
---
C es un lenguaje de programación compilado, de tipado fuerte y orientado a la programación estructurada (procedural).  
Se caracteriza por ser muy eficiente y permitir control directo de la memoria, por eso se usa mucho en sistemas operativos, drivers, firmware y software de alto rendimiento.

Es la base de muchos lenguajes modernos.

### **Sintaxis básica**

##### Estructura mínima de un programa:
```C
#include <stdio.h>
int main() {    
	printf("Hola mundo");    
	return 0;
}
```

##### Elementos clave:
- `#include` → importa librerías.
- `main()` → punto de entrada del programa.
- `printf()` → salida por pantalla.
- `return 0` → indica que el programa terminó correctamente.

##### Variables:
```C
int edad = 20;
float altura = 1.70;
char letra = 'A';
```

##### Condicional:
```C
if (edad >= 18) {    
	printf("Mayor de edad");
}
```

##### Bucle:
```C
for (int i = 0; i < 5; i++) {    
	printf("%d", i);
}
```