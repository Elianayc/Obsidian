---
tags:
  - Programación
  - ProgramaciónI
---
El elemento más representativo de la programación secuencial es la instrucción **goto**.

`goto` permite saltar directamente a otra parte del programa, rompiendo el flujo normal de ejecución.

**Es literalmente decirle al programa:**  
“dejá lo que estás haciendo y seguí desde aquella etiqueta”.

---

### **Sintaxis conceptual**

##### Ejemplo simple en C:
```C
#include <stdio.h>
int main() {   
	 int numero = 1;
 
 inicio:    
	 printf("%d\n", numero);    
	 numero++;    
	 
	 if (numero <= 5)        
		 goto inicio;    
	 
	 return 0;
}
```

##### Qué pasa acá:
1. Se imprime el número.
2. Se incrementa.
3. Si todavía no llegó a 5 → vuelve a la etiqueta `inicio`.

Es como un bucle… pero hecho “a mano”.

---

**Por qué dejó de usarse**
El uso excesivo de `goto` generaba programas muy difíciles de entender y mantener.  
El flujo del programa saltaba por todos lados → esto se conoce como _spaghetti code_ 

Por eso surgió la **programación estructurada**, que reemplaza los `goto` por estructuras de control, de repetición y funciones / módulos.

Hoy el `goto` casi no se usa y en muchos cursos se enseña como antecedente histórico.